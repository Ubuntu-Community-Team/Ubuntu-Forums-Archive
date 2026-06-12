---
title: "How do I install this plugin?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by furoido on 2010-10-25
Hi!
Just downloaded the Fx Foundry plug-in for GIMP (gimpfx-foundry-2.6-1.tar.gz) onto my desktop as a zip file, but not sure how/where to install it! Can anybody give me PRECISE instructions on how to do so?!
Thanks!

---

### Post by ajgreeny on 2010-10-25
I have no idea about that plugin, but some others, eg pandora to make panoramas from two or more photos, are accessed from the menus of gimp, and are not specifically installed into gimp after installing on the system.

Have a good look into all the gimp menus and see if you can find anything that looks hopeful.

---

### Post by ronnielsen1 on 2010-10-25
> Install GIMP brushes in Linux

Go to your Home folder. You have to make hidden files/folders visible, so hit Ctrl+H. Go to the directory named .gimp-2.x (where 2.x is version number of GIMP you are using). Within that folder, there are subfolders, one of which is brushes. Drop your brushes to that folder.
We're talking gimp 2.6 but it should still apply. You should have hidden folders for .scripts .plugins etc

[http://www.techzilo.com/how-to-install-gimp-plugins-scripts-brushes-and-gradients/](http://www.techzilo.com/how-to-install-gimp-plugins-scripts-brushes-and-gradients/)

Here's a link to an Ubuntu forum that tells you to change the root portion of gimp which surprises me since it seems it would be better in your personal home folder

> sudo cp whatever_script_is /usr/share/gimp/2.0/scripts
Or, if you're more comfortable using nautilus,
Alt + F2
Code:
gksu nautilus
and just drag and drop it where it belongs.

[http://ubuntuforums.org/showthread.php?t=282032](http://ubuntuforums.org/showthread.php?t=282032)

Here's a link to a good site about gimp plugins that fault the developer for not including a read me file
> For more complex plugins, organized as a directory with multiple files, there ought to be a file inside called either INSTALL or README, with instructions. If not, the best advice is to toss the plugin in the trash and spend your time on something else: any code written with so little concern for the user is likely to be frustrating in myriad ways.
[http://docs.gimp.org/en/gimp-scripting.html#gimp-plugins-install](http://docs.gimp.org/en/gimp-scripting.html#gimp-plugins-install)

---

