---
title: "Ubuntu Moblin Remix: How-to install the Broadcom wireless driver"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by mantisdolphin on 2009-10-21
I've looked around on Ubuntu Forums, but can't find precise help on this.

How do I install the Broadcom wireless driver on a Dell Mini 9 under Ubuntu Moblin Remix? 

I downloaded the Broadcom driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  

I extracted it to a USB memory stick.

Karmic Moblin Remix .img is on the same thumbdrive.  

It boots fine, just no wireless.  

Crunchbang (Ubuntu) is on one partition of the netbook SSD with the Broadcom BCM4312 wireless driver compiled and working.

Okay, so when I install to the netbook, how do I compile the Broadcom driver into Ubuntu Moblin Remix?   

Thanks!

---

### Post by pgar23 on 2009-10-21
I have an idea of what you could do...
Why not try plugging your netbook into your router, install the driver via a wired connection. Get everything up and running and then try your wireless.

Hope that helps man.

---

### Post by pgar23 on 2009-10-21
Copied from another thread:


Re: Can't install Broadcom STA Wireless Driver 
$sudo apt-get install bcmwl-kernel-source
will install the broadcom STA driver, maybe someone else knows whether it needs and post-install setup

[EDIT] just to add, i'm assuming your device is covered by the versions below

These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware.

Located [HEREEEEEEEEEEEEE]("http://ubuntuforums.org/showthread.php?t=1280375")

---

### Post by xoftware on 2009-11-11
I also have dell mini 9 which refuses to install the sta driver. I tried the command line and it didn't work either. I've been really disappointed with all the bugs in 9.10. Hope someone figures out the wireless issues.

---

### Post by dai_bach on 2009-11-19
I got my wireless driver working using the drivers from the Broadcom website, but they seem not to be automatically recognised at each startup.  I will write a script that is executed at startup but it seems like a lot of hassle for something to fix a feature that should work from "out of the box".  A small, but nevertheless very annoying, glitch in what is otherwise a very smart OS.

---

### Post by dai_bach on 2009-11-19
I've just used the following commands:
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```

and restarted.  I have WiFi connectivity without having to fiddle anything.  Found the commands on the following website:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by shuvro58 on 2009-12-30
thanks for the post[IMG]http://ubuntuforums.org/[IMG]http://my-used-stuff.com/smiley.gif[/IMG][/IMG]

---

### Post by shuvro58 on 2009-12-30
[IMG]http://ubuntuforums.org/[IMG]http://my-used-stuff.com/smiley.gif[/IMG][/IMG]

---

