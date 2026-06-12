---
title: "Move data and programs"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Chipshot on 2010-05-17
Hello, My Jaunty 9.04 is a dual boot. Gparted was used to copy the Windows partition to a new drive then Karmic 9.10 was installed with a swap, Linux and Home partition. 
If the Home partition on 9.04 is copied over the Home on 9.10 will my programs and setting come over and work?
If yes, how is that done?
The 9.04 drive has been mirrored (by Clonezilla) on yet another drive so we can be fearless.
Thank you in advance.

---

### Post by ubunterooster on 2010-05-17
You would certainly want to update first thing; I would assume you would have some problems though. But if you want to, try

---

### Post by jbrown96 on 2010-05-17
Just your settings and data. Programs are stored in /bin and /usr/bin, but if you wanted to copy those, then you would need /lib as well. Most server-type programs like an ssh server and nfs server are stored in /etc, but you should copy those files individually and only the ones you know that you need. 

/home will definitely hold all the settings for your normal applications.

---

### Post by Chipshot on 2010-05-17
> **jbrown96 said:**
> Just your settings and data. Programs are stored in /bin and /usr/bin, but if you wanted to copy those, then you would need /lib as well. Most server-type programs like an ssh server and nfs server are stored in /etc, but you should copy those files individually and only the ones you know that you need. 

/home will definitely hold all the settings for your normal applications.
Thanks, I'll give it a try tomorrow and let you know the results.

---

### Post by Chipshot on 2010-05-19
> **jbrown96 said:**
> Just your settings and data. Programs are stored in /bin and /usr/bin, but if you wanted to copy those, then you would need /lib as well. Most server-type programs like an ssh server and nfs server are stored in /etc, but you should copy those files individually and only the ones you know that you need. 

/home will definitely hold all the settings for your normal applications.
Well, it started giving me error and permission messages so I just did a fresh load on a new drive  and brought all the data over and reinstalled the few extra programs that I have. Maybe I should have tried it from the command line. What would have been the best thing to do-copy /bin and /usr/bin and /lib to and external drive,load Karmic and then overwrite the new installation with /bin et al?

Anyway it up and running well. I like it! Thanks for your imput.

---

### Post by jbrown96 on 2010-05-19
Copying from the command line is the way to go. ```
sudo cp -R /bin /media/EXTERNAL
``` and so on

---

### Post by Chipshot on 2010-05-19
> **jbrown96 said:**
> Copying from the command line is the way to go. ```
sudo cp -R /bin /media/EXTERNAL
``` and so on
Exactly what I was looking for.  I'll try it on another drive soon.  Thanks

---

### Post by Chipshot on 2010-05-19
> **jbrown96 said:**
> Copying from the command line is the way to go. ```
sudo cp -R /bin /media/EXTERNAL
``` and so onOne more question, please. I'm clear on the bin and lib copy but when I copy the /usr/bin should just copy the bin part of that or copy the whole usr folder with the bin that's in that folder? Thanks.

---

### Post by oldfred on 2010-05-19
Are you sure you want to copy /bin.  You may want to copy some system wide settings from /etc if you did anything.

You can copy all the programs you have installed with this and then your will have the updated versions of everything you had, not old stuff that may not work with the new version.

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

old install
dpkg --get-selections | grep -v deinstall > ubuntu-files

New system:
  432  sudo dpkg --set-selections < ubuntu-files
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgrade

---

### Post by Chipshot on 2010-05-20
> **oldfred said:**
> Are you sure you want to copy /bin.  You may want to copy some system wide settings from /etc if you did anything.

You can copy all the programs you have installed with this and then your will have the updated versions of everything you had, not old stuff that may not work with the new version.

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

old install
dpkg --get-selections | grep -v deinstall > ubuntu-files

New system:
  432  sudo dpkg --set-selections < ubuntu-files
  434  sudo apt-get -y update
  435  sudo apt-get update
  436  sudo apt-get dselect-upgradeWell, testing this on another drive,  after loading 9.10, copying usr, et cetera produced error and access messages.  When it was finally accomplished Ubuntu never booted to the desktop. It seems to me the the easiest and most reliable  way to backup and/or restore a system is to the mirror a drive with Clonezilla, make occasional copies of the Documents folder (where almost all my data is) and TAR Evolution. This is what was done when moving to Karmic from Juanty and it's running great. However, that tip about the "Programs List" ([http://ubuntuforums.org/showpost.php...75&postcount=5]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")) worked perfectly. Thanks. Can you tell me how to get to a ntfs USB flash drive named "Flash" and access the folders and files through Terminal instead of having to use Nautilus?

---

### Post by oldfred on 2010-05-21
tilde ~ is short cut to home
.. is up one directory
/  is root

from your home $
type cd / and you will be at root
type ls and you will see all the directories under root including media
cd media and type ls and you should see your flash
Capitals and small letters are important when typing, I often have to use ls to see that I mistyped something.
Tab can help is you get the first letter or two correct and the rest are unique as it will complete the line for you.

Directly should be:
cd /media/flash
unless it is Flash:)

---

### Post by -kg- on 2010-05-21
> from your home $
type cd / and you will be at root

Incorrect... typing cd\ (that's a backslash - no space between) will take you to root, just like DOS. I was uncertain, so I just tried it (in Karmic). ;)

---

### Post by Chipshot on 2010-05-21
> **oldfred said:**
> tilde ~ is short cut to home
.. is up one directory
/  is root

from your home $
type cd / and you will be at root
type ls and you will see all the directories under root including media
cd media and type ls and you should see your flash
Capitals and small letters are important when typing, I often have to use ls to see that I mistyped something.
Tab can help is you get the first letter or two correct and the rest are unique as it will complete the line for you.

Directly should be:
cd /media/flash
unless it is Flash:) Thanks, that did it.  cd\ only produced > which didn't respond well (just messages) to ls or dir.  Thanks again guys, this will get closed soon but ..."I'll be back."

---

