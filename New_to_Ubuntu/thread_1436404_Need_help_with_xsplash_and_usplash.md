---
title: "Need help with xsplash and usplash"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by the_jermz on 2010-03-22
Hello all!  I started using Karmic (first time in a Linux distro) about 3 months ago, and have been able to solve most of my problems through this forum.  But, this one has me stumped...  When I go into XSplash to change my splash screen, I first get an error: Unable to create a backup registry, edit at your OWN RISK!  Then when I try to change the fun brown screen to anything else, in reverts right back to the brown.  2nd, I have been trying to get the USplash Fingerprint theme loaded, but to no avail ([http://gnome-look.org/content/show.php/USplash+Theme+Fingerprint?content=93826](http://gnome-look.org/content/show.php/USplash+Theme+Fingerprint?content=93826)).  I installed the Start-Up Manager, as directed on another post in here, and installed the theme... but all I get is a random color box/screen setting thing when it boots up and shuts down.  Maybe I am missing something very basic here, but I have been searching around for a couple hours and can't figure it out.  

Side note:  If it wasn't for this site, I probably would have gone back to Windows, Thank you for all the info and "hand-holding" guides.  It sucks being a noob, but you guys made it a heck of a lot easier! :D

---

### Post by patchwork on 2010-03-22
I've been changing my xsplash without incident by backing-up the current image 
```
 sudo cp /usr/share/images/xsplash/bg_2560x1600.jpg /usr/share/images/bg_2560x1600.jpg.backup
```(Notice the backup is to the parent directory, not the xsplash directory), and then replacing it with an image of my choice using the same filename```
sudo cp /my/image /usr/share/images/xsplash/bg_2560x1600.jpg
```

I don't believe this method will work on 10.04 (using the Plymouth boot screen), but works well with 9.10

---

### Post by ajgreeny on 2010-03-22
> **patchwork said:**
> I've been changing my xsplash without incident by backing-up the current image 
```
 sudo cp /usr/share/images/xsplash/bg_2560x1600.jpg /usr/share/images/bg_2560x1600.jpg.backup
```(Notice the backup is to the parent directory, not the xsplash directory), and then replacing it with an image of my choice using the same filename```
sudo cp /my/image /usr/share/images/xsplash/bg_2560x1600.jpg
```I don't believe this method will work on 10.04 (using the Plymouth boot screen), but works well with 9.10
I agree this is the way to do it with karmic.  It's exactly what I did to get my own deaktop background as the login screen background, so now I go from the white ubuntu logo to my desktop background without the grey/brown screen interrupting the progression, though with a couple of momentary screen blackouts as the login box appears admittedly.

---

### Post by the_jermz on 2010-03-22
Here's what I get:  cp: cannot stat `/home/thejermz/pictures/linux.jpg': No such file or directory  
I feel like a complete idiot, what the heck am I doing wrong?

---

### Post by patchwork on 2010-03-22
Case-sensitive

You probably mean ~/Pictures/linux.jpg?

---

### Post by the_jermz on 2010-03-22
Works like a charm, thanks for taking the time to help a noob.  Since I had such a hard time with this, think I'll hold off on USplash...  Heading back to the dummy lessons now.:oops:

---

### Post by the_jermz on 2010-03-23
Okay, has anyone had any luck trying to configure usplash via Startup Manager?  I'm trying to set up the fingerprint theme.  Read the how to's, changed screen resolution, and every other "troubleshooting" post out there.  I've been on this for a solid five hours now.

---

### Post by ajgreeny on 2010-03-24
> **the_jermz said:**
> Okay, has anyone had any luck trying to configure usplash via Startup Manager?  I'm trying to set up the fingerprint theme.  Read the how to's, changed screen resolution, and every other "troubleshooting" post out there.  I've been on this for a solid five hours now.
No.  I'm afraid you can give up now as startup-manager is only useful for changing the simple things like the time delay or default OS to boot.  All the other things such as theming that it would do in legacy grub are not working on grub2.

---

### Post by towheedm on 2010-04-29
Really interested in customizing Grub, Usplash, Xsplash and GDM?  Then check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)
If you need help, post a reply there.

---

