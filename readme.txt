=== Plugin Name ===
Contributors: jcow
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=jacobsnyder%40gmail%2ecom&lc=US&item_name=Jacob%20Snyder&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_SM%2egif%3aNonHosted
Tags: gravity forms, update posts, frontend, front end
Requires at least: 3.6.1
Tested up to: 3.9.1
Stable tag: 1.2.4
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Allows you to use Gravity Forms to update any post on the front end.

== Description ==

Allows you to use Gravity Forms to update any post on the front end. If you use the "Gravity Forms + Custom Post Types", you can even update custom post types and use custom taxonomies.

Also hosted on bitbucket: https://bitbucket.org/jupitercow/gravity-forms-update-post

If you have a bug or feature request, submit it there: https://bitbucket.org/jupitercow/gravity-forms-update-post/issues?status=new&status=open

This started as an update to the Gravity Forms Update Post plugin developed by p51labs here.
It has evolved into a completely rewritten plugin that streamlines the system, adds some new support for more fields, and adds more interfaces and filters.

= Compatibility =

Here is how it does NOT really support the original version:

*   All of the delete functionality has been removed. It didn't have anything to do with Gravity Forms, so I thought it should be in a separate plugin or users can manually add it. It seemed like it complicated things in a way that distracted from the main function of the plugin. And I wasn't getting a lot of feedback that users were using it.
*   You can NOT just send a URL get variable and have a form populate with existing content and be editable. I wanted another layer to that. So you have to include a nonce as well, however, there is a built in function for creating edit links to make up for that.

So it isn't very compatible. Plain and simple, you will have to change something to start using this plugin if you were using the original, but I don't think it will be very hard and I did keep the original query variable that was used before.

= New Features =

*   Supports custom field file uploading and deletion with thumbnails or mime type icons for existing items.
*   Fixed a bugs on multi selects and checkboxes.
*   Fixed bug on Categories.
*   Completely removed the ability to delete posts.
*   There are some filters to customize things now.
*   Adds non-query-var template method to setup a form.
*   Adds a really basic shortcode to setup a form (UPDATE: This is still supported, but it is better to use the addition, below, to the gravityform shortcode).
*   Adds an additional attribute to the gravityform shortcode: "update"

= SHORTCODE =

`[gravityforms id="1" update] // Loads current post for editing`

`[gravityforms id="1" update="34"] // Loads post where ID=34 for editing`

We worked with Rocketgenius, makers of Gravity Forms, to get a small upgrade added that allows us to extend their shortcode, so now you can simply add the "update" attribute to the normal "gravityform" shortcode. If you only add "update", it will load the current post in to update. If you add an integer to the update attribute, it will use that to load a post by its ID.

== Installation ==

This add-on can be treated as both a WP plugin and a theme include.

= Install as Plugin =

*   Copy the folder into your plugins folder
*   Activate the plugin via the Plugins admin page

= Include within theme =

*   Copy the folder into your theme folder (can use sub folders). You can place the folder anywhere inside the 'wp-content' directory
*   Edit your functions.php file and add the code below (Make sure the path is correct to include the gravityforms-update-post.php file)
*   `include_once('gravityforms-update-post/gravityforms-update-post.php');`

== Frequently Asked Questions ==

= Tags aren't working in a _____. =

Tags really only work with a single line text field, checkbox and multiselect currently won't show the selected items when loaded for editing, but they will select the items. This might get changed in the future, but isn't pressing. Categories support those other methods, and the text field seems more appropriate, over all, for the tags.

= Why can't I add a post image that is not "featured"? =

Image fields are only supported if they are the "Featured Image". Otherwise you have to use a Custom Field and choose "File Upload" under File Type. If it is not one of these two types, we can't track it for updating.

== Screenshots ==

1. A form on the front end. This just demonstrates the image/file capabilities.

== Changelog ==

= 1.2.4 - 2014-06-04

* Update to allow adding classes to the edit button.

= 1.2.3 - 2014-05-17 =

* Updated taxonomies to allow for more than one custom taxonomy to have value retrieved when updating.

= 1.2.2 - 2014-05-17 =

* Fixed prefix property to contant slip.

= 1.2.1 - 2014-05-17

* Added a filter to allow multifield values to be adjusted.

= 1.2 - 2014-05-13 =

* Added the shortcode support to Gravity Forms main shortcode.

= 1.0.0 - 2014-02-13 =

*	Acknowledging that this plugin doesn't really work with the original anymore, I distiguishing it by marking a new version: 1.0 from 0.x.
*	This should fix the strange output when users directories aren't writable. There is a test to make sure the directory is writable before sending the image to Wordpress core to crop.

= 0.6.4 - 2014-02-13 =

*	Images/Files can now be required on update.

= 0.6.3.3 - 2014-02-04 =

*	Fixed bug in anonymous function replacement. There is still an anonymous function left... Not sure if I can get rid of it. Going to stop trying.
*	Added support for multiple capabilities.
*	Added ability to turn off image resizing for now to better support users with the crazy output from GD.

= 0.6.3.2 - 2014-02-04 =

*	Now supports the list field, at least with the default text field(s).

= 0.6.3.1 - 2014-02-04 =

*	Removed two anonymous functions in an effort to support php 5.2 users.

= 0.6.3.0 - 2013-10-21 =

*	Small bug change when adding a conditional to the form for the first time.

= 0.6.2.9 - 2013-10-15 =

*	process_request was moved to the 'wp' action to make sure the taxonomies were loaded for post set up. This cause problems with the actual form processing because the form wasn't getting the post_id soon enough and started creating new posts. It was tricky to put back and still get all of the taxonomy support, but this seems to fix it.

= 0.6.2.8 - 2013-10-15 =

*	Added an empty test for fieldType and type on image field type tests in "gform_field_content" filter.

= 0.6.2.7 - 2013-10-15 =

*	Fix for categories, tags, and taxonomies when editing on a separate page.

= 0.6.2.6 - 2013-10-15 =

*	Updated categories, tags, and added initial support for custom taxonomies through the gf custom post type plugin.

= 0.6.2.5 - 2013-10-15 =

*	Fixed getting post thumbnail for current page/post instead of post that is currently being edited.

= 0.6.2.4 - 2013-10-15 =

*	Fileuploads were always getting duplicated in database, becuase the method used was a carrie over from a fix for the old update posts plugin. This simplified it and makes sure fileuploads are never duplicated in database now.

= 0.6.2.3 - 2013-10-03 =

*	Fixed an issue from last update where nonce was required for $_POST. This broke actual form posting. I reverted that aspect.

= 0.6.2.2 - 2013-09-27 =

*	Updated the query variable form setup to always require a nonce and to better support posting the post_id to set up a form. Though it is highly unrecommended and doesn't really seem to work.

= 0.6.2.1 - 2013-09-20 =

*	Added error checking for thumbnail save. If it doesn't work, we just move on and use the full sized image. Need to figure out what is causing save problem.

= 0.6.2 - 2013-09-19 =

*	Overhauled the image thumbnail generation to start using the newer WP_Image_Editor instead of image_make_intermediate_size.

= 0.6.1 - 2013-09-19 =

*	Removed error output from unlink when a file doesn't exist. Stopped the default thumbnail on post images, so post image thumbs only show up when there is an actual image.

== Upgrade Notice ==

= 1.0 =
This is the first version in the Wordpress repository.
