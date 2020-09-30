# OpenAuth.dev Provider for Laravel Socialite

<div align=center>

![openauth-icon](https://user-images.githubusercontent.com/81188/87538212-25d2ef00-c69c-11ea-87a7-b967826cb669.png)


### OpenAuth.dev Provider for Laravel Socialite


![GitHub Workflow Status](https://img.shields.io/github/workflow/status/openauth-dev/SocialiteOpenAuthProvider/Build) ![Packagist Version](https://img.shields.io/packagist/v/openauthdev/socialiteopenauthprovider) ![Packagist Downloads](https://img.shields.io/packagist/dt/openauthdev/socialiteopenauthprovider) 
[![GitHub license](https://img.shields.io/github/license/openauth-dev/SocialiteOpenAuthProvider)](https://github.com/openauth-dev/SocialiteOpenAuthProvider/blob/main/LICENSE)

</div>

---

### Table of contents

* [About the project](#about-the-project)
* [Getting Started](#getting-started)
* [Configuration](#configuration)
* [Usage](#usage)
* [Contributing](#contributing)
* [Versioning](#versioning)
* [Built With](#built-with)
* [Authors](#authors)
* [License](#license)

## About the project

TBA

## Getting started

Require the project:
```BASH
composer require openauthdev/socialiteopenauthprovider
```

Ready! Now you can start with your project.

## Configuration

First of all replace the service provider `Laravel\Socialite\SocialiteServiceProvider` in the `config\app.php` in `providers[]` with `\SocialiteProviders\Manager\ServiceProvider::class`.

Then we add the required event listener. Go to `app/Providers/EventServiceProvider` and add the following lines to the `listen[]` array.
```PHP
\SocialiteProviders\Manager\SocialiteWasCalled::class => [
    'SocialiteProviders\\OpenAuth\\OpenAuthExtendSocialite@handle',
]
```

Finally, we just need to add the configuration instructions. To do this, add the following to the `config/services.php' file.
```PHP
'openauth' => [
    'client_id' => env('OPENAUTH_CLIENT_ID'),
    'client_secret' => env('OPENAUTH_CLIENT_SECRET'),
    'redirect' => env('OPENAUTH_REDIRECT_URI')
]
```

The configuration is now complete.

## Usage

Now you can use the OAuthProvider as usual with Sociallite.
```PHP
return Socialite::driver('openauth')->redirect();
```

## Contributing
There are many ways to help this open source project. Write tutorials, improve documentation, share bugs with others, make feature requests, or just write code. We look forward to every contribution.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For available versions, see the [tags on this repository](https://github.com/openauth-dev/SocialiteOpenAuthProvider/tags).

## Built with

* [Socialite Providers Manager](https://github.com/SocialiteProviders/Manager) - Easily add new or override built-in Laravel Socialite providers

## Authors

* **Titus Kirch** - *Main development* - [TitusKirch](https://github.com/TitusKirch)

See also the list of [contributors](https://github.com/openauth-dev/SocialiteOpenAuthProvider/graphs/contributors) who participated in this project.

## License

This project is licensed under the LGPL-2.1 License - see the [LICENSE](LICENSE) file for details.
