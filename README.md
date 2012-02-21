ExpDOM extension for PHP DOM
============================

*ExpDOM* try to ease the use of DOM to manipulate XML documents.

Requirements
------------
* PHP 5.3+
* PHPUnit 5.6+


Installation
------------

The library follow the PSR-0 naming convention. To load the library,
use any compliant class loader or simply require the `src/autoload.php` file.

``` php
require __DIR__ . '/path/to/expdom/src/autoload.php';
```


Usage
-----

Load an XML document:

``` php
<?php

use Welldom\Document;

$doc = new Document('UTF-8');

if (false === $doc->load('data.xml')) {
    $errors = $doc->getLastErrors();
    throw new Exception("XML Loading error\n" . implode("\n", $errors));
}

// ... enjoy your DOM document
```

Find a node values using XPath:

``` php
$values = array(
    'title' => $doc->getNodeValue('//book/title'),
    'lang' => $doc->getNodeValue('//book/title/@lang', 'en'),
);
```

Execute action on each node matching a given Xpath:

``` php
$doc->query('//foo/bar[@lang=de]')
    ->remove();

$doc->query('//foo/bar[@lang=english]/@lang')
    ->setValue('en');
```


Run tests
---------

Run PHPUnit test suite:
```
phpunit
```

Quality metrics:
```
ant phpmd
ant phpcs
ant phpcpd
ant phploc
```
