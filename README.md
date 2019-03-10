# Drupal 8 template

## Custom modules, themes or profiles

To maintain correct dependency managment you should always define each local
module, theme or profile as a true composer object.

### Custom composer.json

To add a custom module, theme or library you should put a composer.json file
within the root of the module, theme or profile folder with contents as you find
in the example below.

```json
{
  "name": "custom/myproject_core",
  "type": "drupal-custom-module",
  "require": {
    "drupal/views_bulk_operations": "^2.5"
  }
}

```

Best is to reserve the `custom` vendor namespace followed by the name of the
module, theme or profile. As type you can choose the accompanying composer
installers type: `drupal-custom-module`, `drupal-custom-theme`or
`drupal-custom-profile`
([Composer installer reference](https://github.com/composer/installers/blob/master/src/Composer/Installers/DrupalInstaller.php#L13-L15))

If you have other dependencies which should also be defined in your module info
file, you need to add these to the require section of your composer.json file.

### Project composer.json

To use the local custom module in your projects composer.json file you need to
define the local path in the repositories section of the composer.json file. The
path should point to the root folder of the module, theme or profile.
([Composer repository path reference](https://getcomposer.org/doc/05-repositories.md#path))

```json
{
    "name": "ec-europa/custom-project",
    "description": "Project template for Drupal 8 projects with composer",
    "type": "project",
    "require": {
        "custom/myproject_core": "dev-master",
        "drupal/core": "^8.6.0"
    },
    "repositories": [
        {
            "type": "composer",
            "url": "https://packages.drupal.org/8"
        },
        {
            "type": "path",
            "url": "lib/modules/custom/myproject_core"
        }
    ]
}

```
