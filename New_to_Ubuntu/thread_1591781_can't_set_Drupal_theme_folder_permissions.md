---
title: "can't set Drupal theme folder permissions"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by ubscott on 2010-10-09
hi,
 
in a Drupal 5 installation on Ubuntu i'm trying to set the permissions on the folder of a particular theme. i'm trying to do this because the live site that i copied down to my local LAMP can't read files in the theme.
 
if i try to read an image from this folder i get a 404 error; e.g., in a browser i attempt this:
[http://localhost/Drupal/Particular_Drupal_Instance/themes/mytheme/images/logo.jpg](http://localhost/Drupal/Particular_Drupal_Instance/themes/mytheme/images/logo.jpg)
 
meanwhile, i have verified that the logo image is in an images folder beneath the mytheme folder. i've seen the logo in the Ubuntu file explorer.  I am sure i don't have a case sensitivity issue; i've checked for that.
 
i've set file and folder permissions before. i'm familiar with this:
[http://ubuntuforums.org/showthread.php?t=184088](http://ubuntuforums.org/showthread.php?t=184088)
 
here are the steps i'm taking. in a terminal i navigate to:
/var/www/Drupal/Particular_Drupal_Instance$
 
this command shows me the permissions of every theme underneath the themes folder:
ls -l themes
 
for the theme i'm trying to enable, the permissions are:
drwxr-xr-x
 
so, i figure i'll set the permission of the theme's folder so i can read the stuff within it. I try this:
sudo chmod o+r mytheme
 
i enter the admin's password. The terminal takes me back to the command line. when i look again at the theme's folder, the permission was not set; i.e.,
ls -l mytheme
produces: drwxr-xr-x
 
I'm baffled, and a little bit frustrated. how come i can't set a 'read' permission on the folder of a Drupal theme that i want to use?
 
thanks,

---

### Post by ubscott on 2010-10-10
hi, can anyone offer some insight?  thanks.

---

### Post by crazy dave on 2011-11-19
Have you set the ownership of the folders correctly?  such as:

```
chown -R username:www-data /drupalfolders
```  because the folders need to have the correct user and group in order to give the server access.  The ```
chown -R
``` allocates ownership and permissions recursively i.e. to the parent folder and all files and folders within it(careful when using this).  I'd recommend setting permissions on a folder by folder basis, step by step.

With respect to the individual file and folder permissions, there is a good guide here [[COLOR="RoyalBlue"]Change Drupal folder and file permissions[/COLOR]]("http://knooq.com/blog/drupal-linux-permissions") which wil help you to check your setup.  This blog post explains the numerical representation of permissions such as ```
chmod 644 settings.php
``` which I think is easier to understand and remember.

Regards.

---

