---
title: "TTY1 Ubuntu Boot"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Townley89 on 2011-03-07
Hey all,

I booted to a live USB of Ubuntu 10.10 on my Dell Vostro V130 (which came with Ubuntu, but I tried out Mint for a while, so deleted it) 

Anyway, the USB loaded just fine, but when I try to boot after install, it starts loading a series of numbers that fly by too quickly to read. It stops somewhere around 19.02___ something about Bluetooth and then brings me to a screen that says Ubuntu 10.10 (my comp's name) tty1 and asks me to log in.

Once I do, it brings me to a screen from which I can run commands. As per what mint taught me, I try "live" to no avail. StartX seems to run for a minute and then the screen goes blank for hours and I have to do a hard reboot. Any suggestions for how to fix this?

(btw it also happens with Ubuntu 10.10 netbook remix)

Thanks for the assistance!
-Rob

---

### Post by Townley89 on 2011-03-09
Got it!

So the problem was that during install, I guess I screwed up Grub (not sure how that works, but apparently that's the case)

I entered the Grub menu by holding down Shift during boot. When the option came up, I chose to reinstall dpkg and do all of the other updates there (just for good measure.) It took 20 mins of downloading before it asked "cannot locate menu.lst would you like Grub to reform it? y/n" pick yes and watch grub put itself back together! 

So yeah, if anyone has a problem where it loads numbers that look like 
> 
1.111414 blah blah
1.122422 blah blah
2.1531626 blah blah
.
..
...
19.23662 reconnect=0 dpkg failed, bluetooth error

login: 
password:


then just enter into the Grub menu and presto! problems solved!

---

