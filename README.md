[![Latest Stable Version](https://poser.pugx.org/pouler/apple-music-api/v/stable)](https://packagist.org/packages/pouler/apple-music-api)
[![Latest Unstable Version](https://poser.pugx.org/pouler/apple-music-api/v/unstable)](https://packagist.org/packages/pouler/apple-music-api)
[![Build Status](https://travis-ci.org/PouleR/apple-music-api.svg?branch=master)](https://travis-ci.org/PouleR/apple-music-api)



# Apple Music API PHP

This is a PHP wrapper for the [Apple Music API](https://developer.apple.com/documentation/applemusicapi).

## Requirements
* PHP 7.1 or later.
* HTTP Client

### HTTP Clients
This wrapper relies on HTTPlug, which defines how HTTP message should be sent and received. You can use any library to send HTTP messages
that implements [php-http/client-implementation](https://packagist.org/providers/php-http/client-implementation).

Here is a list of all officially supported clients and adapters by HTTPlug: http://docs.php-http.org/en/latest/clients.html

Read more about HTTPlug in [their docs](http://docs.php-http.org/en/latest/httplug/users.html).

## Installation
Install it using [Composer](https://getcomposer.org/):

```sh
composer require pouler/apple-music-api
```

To install with Guzzle 6 you may run the following command: 

```
$ composer require pouler/apple-music-api php-http/guzzle6-adapter php-http/message
```

## Usage
Before using the Apple Music API, you need to sign up for the Apple Developer Program. Read more about this [here](https://developer.apple.com/documentation/applemusicapi/getting_keys_and_creating_tokens).

```php
<?php

require 'vendor/autoload.php';

$tokenGenerator = new PouleR\AppleMusicAPI\AppleMusicAPITokenGenerator();
$jwtToken = $tokenGenerator->generateDeveloperToken(
    'team.id',
    'key.id',
    '/path/to/authkey.p8'
);

$client = new PouleR\AppleMusicAPI\APIClient();
$client->setDeveloperToken($jwtToken);

$api = new PouleR\AppleMusicAPI\AppleMusicAPI($client);

$result = $api->getCatalogPlaylist('nl', 'pl.a56541661a7a4cca95ddeca24e5e5316');

print_r($result);
```
