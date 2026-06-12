---
title: "I have a few low difficulty questions"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by king james on 2009-02-06
I would really appreciate some help with just some quirks I have, nothing major.

1) When I get to the login menu I here a static sound. This is, I assume, a vestige of the intro and login sounds played by Ubuntu upon startup. I setup my sound with a creative linux driver and OSS, it works fine but not really with this intro sound. I have disabled the login jingle via the system menu, but the sound persists.

2) I have several hard drives that do not auto mount upon boot up. They are listed in "places" but I have to select them there and THEN they become available on the desktop. Not a big deal but a bit annoying.

3) Next, I am used to windows and we have a registry cleanup program and the add/remove programs option. Is there anything like this for linux? Some stuff I have installed not with synaptic or through packages and I have no clue where some if it installed to be honest. How can I clean this junk out?

Thanks for any help.

---

### Post by nlz on 2009-02-06
1.
System > Preferences > Sound 
Then untick 'Play system sounds'


2.
Add the harddrives to /etc/fstab
Please open a terminal (Application > Accessories > Terminal) and type ```
cat /etc/fstab
``` and paste the outcome here.

3.
You install stuff through synaptic, apt, aptitude and you can find this though the package manager. If you install standalone applications like Urban Terror or Songbird, you can find them mostly in your home directory or in /opt.

Feel free to ask if you don't understand.

---

### Post by Temposs on 2009-02-06
I can take #3

There is, at least in 8.10, a package called system-cleaner-gtk. This will try to look for extra programs installed that you might want to uninstall, as in your case. It's new in 8.10 and doesn't exist in 8.04. If you want this kind of functionality, you'll need to upgrade to Ubuntu 8.10. I used it after I did the upgrade from 8.04 to 8.10 and it worked well.

---

### Post by king james on 2009-02-07
Thanks for the help. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ec97d6e-47cc-43b2-b98a-05d8fa811bba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1499da32-dba9-4781-837e-1324636b5841 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Doesn't seem like my 2 other drives are listed...hm.

---

