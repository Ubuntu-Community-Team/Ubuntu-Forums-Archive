---
title: "[SOLVED] More Flash Woes"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by The ragman on 2008-12-17
I successfully installed Kubuntu, onto an older IBM T21, and got firefox. . 

I searched many threads for info on Flash installation, did a lot of the suggested solutions, like ```
locate libflashplayer.so
```, found it, removed it by synaptic package manager, did the ```
sudo apt-get clean
``` and the ```
sudo apt-get autoremove
``` that managed to remove way more than I intended:lolflag:, and then downloaded the deb installer for flash 10. something. I did all of this eagerly, clicked on all suggested, was told Flash was installed, opened up the browser, pointed it at a flash dependent site and was informed> You need Flash Player and the bar at the top suggest I > install plugins Clicked on that, and after much chuntering, the box tells me that I could install nothing, click next. Clicked next, and was taken to the Adobe site, where  I had just downloaded the package from earlier. Clicked on the package again, and reinstalled it. same results occurred. 

So, anyone got any ideas what I am not doing right? 

I repeat, this computer is running Kubuntu 8.04. 
I had similar problems with my other laptop, running Ubuntu 8.04, but the above resolved the issue.

---

### Post by taurus on 2008-12-17
How did you install flash on your machine?  Did you install the flashplugin-nonfree from the repos?

Installing kubuntu-restricted-extras should install flash, java, and other things to your machine too.

---

### Post by evilkastel on 2008-12-17
ak, have you tried the standard procedure? sudo apt-get install flash-plugin-nonfree?
remember, flash plyer is for swf but shockwave sites are not supported (that i know)

---

### Post by The ragman on 2008-12-17
I had tried that way earlier, and got nothing, but there were a few messed up packages at that time. I will try it again, and let you know.

---

### Post by The ragman on 2008-12-17
Just repeated the ```
apt-get install flashplugin-nonfree
```bit, and got this. > apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 214 not upgraded.
Need to get 18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 1s (10.4kB/s)
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 105804 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--16:17:42--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.66.70
Connecting to fpdownload.macromedia.com|72.247.66.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:17:43 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


What went wrong? :confused:

---

### Post by taurus on 2008-12-17
Looks like it's a dead link.  Try downloading it directly from Adobe's site.

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

Once saved to your Desktop, open a terminal and run

```
cd ~/Desktop
tar xvzf install_flash_player_10_linux.tar.gz
cd install_flash_player_10_linux
sudo ./flashplayer-installer
```

---

### Post by The ragman on 2008-12-17
Thank you, that worked. It also explains why the other attempts failed. 

The expected folder for Firefox is ~/mozilla apparently - on this computer the installer put firefox into ~/firefox.3.0.4 Now, however it works, thank you very much - I now know what to do with a .tar.gz file. :lolflag::guitar::guitar:

---

