# Magento 2 Bongloy Integration

[![Build Status](https://travis-ci.org/pmclain/module-stripe.svg?branch=master)](https://travis-ci.org/pmclain/module-stripe)
[![Coverage Status](https://coveralls.io/repos/github/pmclain/module-stripe/badge.svg?branch=master)](https://coveralls.io/github/pmclain/module-stripe?branch=master)
[![Total Downloads](https://poser.pugx.org/pmclain/module-stripe/downloads)](https://packagist.org/packages/pmclain/module-stripe)
[![License](https://poser.pugx.org/pmclain/module-stripe/license)](https://packagist.org/packages/pmclain/module-stripe)

Accept credit card payments through the Bongloy payment gateway.

* Supports Magento Instant Purchase for One Click Checkout
* Securely accept customer payments using the bongloy.js tokenization when
collecting all payments.
* Provide customers option of storing payment information for future
transactions.
* Stored customer card information can be used for orders created in the
frontend or backend.
* Stored cards deleted by customer in Magento are also removed from the
corresponding Bongloy customer profile.
* New payments can be authorize or authorize and capture.
* Authorized payments can be captured online during invoice creation.
* Full and partial refund support when creating credit memos.
* 3D Secure support for one-time and vault payments

## Installation
#### Composer

In your Magento 2 root directory run  
`composer require phannaly/bongloy-magento-payment`

`bin/magento setup:upgrade`  

## Magento Version Requirements
| Release | Magento Version |
| ------- | --------------- |
| 2.1.x   | >=2.2.5         |
| 2.0.x   | 2.2.0-2.2.4     |
| 1.x.x   | 2.1.x           |
| None    | 2.0.x           |

## Configuration
The configuration can be found in the Magento 2 admin panel under  
Store->Configuration->Sales->Payment Methods->Bongloy

Enter your Bongloy account credentials (*secret key and publishable key*), select **Accepted Currency**
and then enter **Title** (*Bongloy Credit Card*) so user will see and can select it as payment option in checkout page.


## Testing and Local Development
**WARNING**
The docker setup included is intended for local development only.

### Local Development
`cd ./dev`  
`docker-compose up -d`
`docker-compose exec app module-installer`  
`docker-compose exec app magento-installer`

Create the host entry `127.0.0.1 bongloy.docker`

### Execute Tests
 * Setup  
    `docker-compose -f dev/docker-compose.yml up -d`  
    `docker-compose -f dev/docker-compose.yml exec app module-installer`  
 * Unit - `docker-compose -f dev/docker-compose.yml exec app test-unit`
 * Integration - `docker-compose -f dev/docker-compose.yml exec app test-integration`
 * Acceptance - `docker-compose -f dev/docker-compose.yml exec app test-acceptance`

## License
Open Software License v3.0
