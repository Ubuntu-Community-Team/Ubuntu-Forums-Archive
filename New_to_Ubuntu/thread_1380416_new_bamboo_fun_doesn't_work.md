---
title: "new bamboo fun doesn't work"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by cameronedwards on 2010-01-13
OK I have a Bamboo Fun for Christmas this year and I've been googling like crazy trying to get it to work since. Lots of people's tablets aparently work like a mouse/touchpad as soon as it is plugged in. But mine is completely non-responsive. If it wasn't for the white light at the top of the device that glows brightly when pressure is on the pad section of the device plus the red light that replaces the white light when the pen is placed over the pad section, I would think that the device was broken.

Can anyone help me? it's a Bamboo Fun Model "CTH-461" my computer is running Ubuntu 9.10 32x I have a Hp Pavilion dv6700  

Really looking forward to using this, thinking of creating wallpapers etc...

---

### Post by cameronedwards on 2010-01-13
aperantly i have to bump this...

---

### Post by Methuselah on 2010-01-13
I have a wacom bamboo but it 'just works' with recent operating systems so I am of no specific help with troubleshooting.
I remember for hardy heron, I had to configure it by editing xorg.conf.
You can try this guide in which a person configured his own:

[http://www.rawdev.net/2008/10/09/wacom-bamboo-fun-on-linux/](http://www.rawdev.net/2008/10/09/wacom-bamboo-fun-on-linux/)

If you type lsusb in a terminal and the tablet is there there is a change you can get it to work.

---

### Post by Favux on 2010-01-13
Hi cameronedwards,

The Bamboo Fun Model "CTH-461" is so new that it isn't supported yet by linuxwacom (0.8.4-1 is the default version in Karmic).  Ayuthia, ob1kenobi, and company have developed some experimental patches to apply to linuxwacom to get it to work.  They are being submitted to linuxwacom and hopefully will be included in the next version.  So right now you want to go to [this thread]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") where we're applying them currently to linuxwacom 0.8.5-9.  That will get almost everything working.

For some more information and the new-generic rc2 .fdi you'll need see:  [http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)

Have fun and good luck!

---

