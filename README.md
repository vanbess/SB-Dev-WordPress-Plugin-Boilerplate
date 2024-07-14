Silverback Dev WordPress Plugin Template
=========================

A robust and GPL-licensed code template for creating a standards-compliant WordPress plugin.

## How do I use it?

Simply click on the **'Use this template'** button at the top of this page to either create your own new repo based on this template, or to open this template in a codespace.



## Registering a new post type

Using the [post type API](https://github.com/hlashbrooke/WordPress-Plugin-Template/blob/master/includes/lib/class-wordpress-plugin-template-post-type.php) and the wrapper function from the main plugin class you can easily register new post types with one line of code. For example if you wanted to register a `listing` post type then you could do it like this:

`WordPress_Plugin_Template()->register_post_type( 'listing', __( 'Listings', 'wordpress-plugin-template' ), __( 'Listing', 'wordpress-plugin-template' ) );`

*Note that the `WordPress_Plugin_Template()` function name and the `wordpress-plugin-template` text domain will each be unique to your plugin after you have used the cloning script.*

This will register a new post type with all the standard settings. If you would like to modify the post type settings you can use the `{$post_type}_register_args` filter. See [the WordPress codex page](http://codex.wordpress.org/Function_Reference/register_post_type) for all available arguments.

## Registering a new taxonomy

Using the [taxonomy API](https://github.com/hlashbrooke/WordPress-Plugin-Template/blob/master/includes/lib/class-wordpress-plugin-template-taxonomy.php) and the wrapper function from the main plugin class you can easily register new taxonomies with one line of code. For example if you wanted to register a `location` taxonomy that applies to the `listing` post type then you could do it like this:

`WordPress_Plugin_Template()->register_taxonomy( 'location', __( 'Locations', 'wordpress-plugin-template' ), __( 'Location', 'wordpress-plugin-template' ), 'listing' );`

*Note that the `WordPress_Plugin_Template()` function name and the `wordpress-plugin-template` text domain will each be unique to your plugin after you have used the cloning script.*

This will register a new taxonomy with all the standard settings. If you would like to modify the taxonomy settings you can use the `{$taxonomy}_register_args` filter. See [the WordPress codex page](http://codex.wordpress.org/Function_Reference/register_taxonomy) for all available arguments.




## Defining your Settings Page Location

Using the filter {base}menu_settings you can define the placement of your settings page. Set the `location` key to `options`, `menu` or `submenu`. When using `submenu` also set the `parent_slug` key to your preferred parent menu, e.g `themes.php`. For example use the following code to let your options page display under the Appearance parent menu.

```php
$settings['location'] = 'submenu';
$settings['parent_slug'] = 'themes.php';
```

See respective codex pages for `location` option defined below:
https://codex.wordpress.org/Function_Reference/add_options_page
https://developer.wordpress.org/reference/functions/add_menu_page/
https://developer.wordpress.org/reference/functions/add_submenu_page/



## Calling your Options

Using the [Settings API](https://github.com/hlashbrooke/WordPress-Plugin-Template/blob/master/includes/class-wordpress-plugin-template-settings.php) and the wrapper function from the main plugin class you can easily store options from the WP admin like text boxes, radio options, dropdown, etc. You can call the values by using `id` that you have set under the `settings_fields` function. For example you have the `id` - `text_field`, you can call its value by using `get_option('wpt_text_field')`. Take note that by default, this plugin is using a prefix of `wpt_` before the id that you will be calling, you can override that value by changing it under the `__construct` function `$this->base` variable;



## What does this template give me?

This template includes the following features:

+ Plugin headers as required by WordPress & WordPress.org
+ Readme.txt file as required by WordPress.org
+ Main plugin class
+ Full & minified Javascript files
+ Grunt.js support
+ Standard enqueue functions for the dashboard and the frontend
+ A library for easily registering a new post type
+ A library for easily registering a new taxonomy
+ A library for handling common admin functions (including adding meta boxes to any post type, displaying settings fields and display custom fields for posts)
+ A complete and versatile settings class like you see [here](http://www.hughlashbrooke.com/complete-versatile-options-page-class-wordpress-plugin/)
+ A .pot file to make localisation easier
+ Full text of the GPLv2 license