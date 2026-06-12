---
title: "Flash 64 bit"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by phatcartoon on 2010-05-02
Ok, I'm doing this for the newbies out there and any one else who had a problem getting this to work right.  

First off, trying to use 32bit flash didn't work out for me in Lucid (10.4).  Some YouTube videos would work; others not so good.  I could watch them, but could not use the controls.  I tried some links people shared, but they all linked me to another 32bit version.  I tried the adobe site and every time I clicked on on the 64bit apt link I would get some kind of error.  (adobe-flashplugin is virtual)  So, after some searching I found this and entered it into the Terminal.

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

Now all videos play correctly and I can control all the player controls.


Apologize if I posted this in the wrong area.  I might not be new to Ubuntu, but to the forums I am.

---

### Post by ddecator on 2010-05-03
[https://bugs.launchpad.net/debian/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/debian/+source/flashplugin-nonfree/+bug/410407)

The third workaround fixes the control issue with Flash from the repos on 64-bit systems. It's a bug in Flash, so all we can do right now is provide the workaround.

---

### Post by bandersen on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591) REALLY helped me.. :P

---

### Post by nhasian on 2010-05-03
thats odd to have a ppa for adobe software... i just recommend grabbing the latest 64bit adobe flash from:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by roddersg on 2010-05-03
Thanks all.
What I did:
   checked to see that Flash not installed
   used GrabFlash64-bit (did not work)
   downloaded Flash 64-bit from adobe site
   did a find . | grep libflashplayer.so and found the locations
   manually copied the libflashplayer.so from adobe into the locations from find
   works!

thanks

---

