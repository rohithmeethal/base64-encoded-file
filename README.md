base64-encoded-file
===================

Provides handling for base64 encoded files

[![Build Status](https://travis-ci.org/bagrinsergiu/base64-encoded-file.svg?branch=master)](https://travis-ci.org/bagrinsergiu/base64-encoded-file)

## Installation

1. Add in `composer.json`

    ```json
    {
        "repositories": [
            {
                "type": "vcs",
                "url": "https://github.com/bagrinsergiu/base64-encoded-file.git"
            }
        ]
    }
    ```

2. Install

    ```bash
    $ composer require bagrinsergiu/base64-encoded-file
    ```

## Usage

```php
<?php

use Hshn\Base64EncodedFile\HttpFoundation\File\Base64EncodedFile;

$file = new Base64EncodedFile(base64_encode($data));

$file->getPathname(); // "/path/to/file"
$file instanceof Symfony\Component\HttpFoundation\File\File; // true
```


### Integration for symfony/form

```php
<?php

use Hshn\Base64EncodedFile\Form\Type\Base64EncodedFileType;

$form = $formBuilder
    // symfony 2.7
    ->add('file', new Base64EncodedFileType())
    // symfony 2.8~
    ->add('file', Base64EncodedFileType::class)
    ->getForm();
```

### Integration in a Symfony project (manual install)

Use this bundle in a Symfony project requires the following libraries:

* symfony/dependency-injection
* symfony/http-kernel
* symfony/config

Then, you can load the bundle through the following configuration:

```php
<?php

// bundles.php

Hshn\Base64EncodedFile\Bridge\Symfony\Bundle\Base64EncodedFileBundle::class => ['all' => true],
```
