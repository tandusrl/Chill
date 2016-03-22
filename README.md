Chill - PHP Library for CouchDb
===============================

This is a fork
---------------

This is just an internal fork in order to have better error handling and have more flexibility


Chill is a simple and efficient CouchDb client library for PHP. Released under the BSD 2 Clause Licence and made available via [Composer/Packagist](https://packagist.org/packages/chill/chill).

**Current Build Status:**

[![Build Status](http://phpci.block8.net/build-status/image/4?branch=master)](http://phpci.block8.net/build-status/view/4?branch=master)

Example usage
-------------

**Retrieve a single document by ID:**

```php
$chill = new Chill\Client('localhost', 'my_database');
$doc = $chill->get('8128173972d50affdb6724ecbd00d9fc');
print $doc['_id'];
```

**Retrieve the results of a view as Chill Document objects:**

```php
$chill = new Chill\Client('localhost', 'my_database');
$docs = $chill->asDocuments()->getView('mydesign', 'myview', array('key1', 'key2'));

foreach ($docs as $doc) {
    print $doc->_id . PHP_EOL;
}
```

**Retrieve and update a document**

```php
$chill = new Chill\Client('localhost', 'my_database');
$doc = $chill->get('8128173972d50affdb6724ecbd00d9fc');
$doc->title = 'Changing my doc.';
$doc->save();
```

New stuff in the fork
----------------------


**Connect with username and password**

```php
// yes, now you can remove admin party
$chill = new Chill\Client('localhost', 'my_database', 'username', 'password');
```

**Get raw form of a document (eg. get a design document)**
```php
$doc = $chill->getRawDocument('_design/yolo');
```

**Create a new database**
```php
// connect with the new database name not already created
$chill = new Chill\Client('localhost', 'my_database');
$chill->createDatabase('my_database');
// enjoy query in your new databases
```

**HTTP status in most error reporting**


With thanks to
--------------
* [Sylvain Filteau](https://github.com/sylvainfilteau) for contributing various bug fixes.
* [Luke Plaster](https://github.com/notatestuser) for contributing support for arrays as view parameters.
* [Ryan Hughes](https://github.com/ryanhughes) for fixing a bug related to PUT requests.
