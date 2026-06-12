---
title: "flash player plug-in crash"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by ericstrom on 2010-09-05
When I run Google Chrome and open Yahoo mail, I get the following message:

The following plug-in has crashed /usr/lib/adobe-flashplugin/libflashplayer.so

Can someone tell me why this is happening and more importantly, how do I fix it ?

Running Ubuntu Lucid Lynx 10.04

---

### Post by sandyd on 2010-09-05
> **ericstrom said:**
> When I run Google Chrome and open Yahoo mail, I get the following message:

The following plug-in has crashed /usr/lib/adobe-flashplugin/libflashplayer.so

Can someone tell me why this is happening and more importantly, how do I fix it ?

Running Ubuntu Lucid Lynx 10.04
Ask adobe. Adobe provides the flash plugins for us to use, but since Flash is a prpreity format, we cannot "fix" flash.

If your using 64 bit, you may have more issues with flash, because Adobe discontinued its x64 version of flash for Linux. The version you would be using (if your using 64-bit ubuntu) is the Nswrapper (wrapped) flash plugin (which creates more issues, again, not changable by us, really)

---

### Post by ericstrom on 2010-09-05
Using 32 bit; not 64

How would I remove it and reinstall it ? Maybe it got corrupted ?

---

### Post by pqwoerituytrueiwoq on 2010-09-05
get the deb file from adobe and install it

---

### Post by sandyd on 2010-09-05
> **ericstrom said:**
> Using 32 bit; not 64

How would I remove it and reinstall it ? Maybe it got corrupted ?
```

wget -c http://adobe-flash-tools.googlecode.com/svn/branches/unstable/scripts/adobe_flash_x86-ubuntu.sh
chmod 667 adobe_flash_x86-ubuntu.sh
/bin/bash ./adobe_flash-x86-ubuntu.sh
```

---

### Post by PRC09 on 2010-09-05
I have been experiencing the flash plugin crash error for a couple of weeks now but it seems to be happening across all the browsers including IE 8 in Windows.The windows crash just takes about 3 times as long to crash and lock-up as Firefox.In the Firefox crash if you go to system > admin > system monitor and check under Processes you will see that the process Plugin-Container is running at usually 80% or more and is locked up.If you end the process and refresh your browser it goes back to normal until it climbs up again.This doesnt happen on all Flash sites but only a few that I have tried but it does happen on the same sites with Firefox in Ubuntu and Windows.There was an ongoing discussion regarding the plugin container and a work-around on the following site.....

[http://support.mozilla.com/en-US/questions/713600#answer-8632](http://support.mozilla.com/en-US/questions/713600#answer-8632) 

Edit: when you disable the pluggin container as suggested then Firefox itself locks up and not just Flash.....

---

### Post by 7bn on 2010-09-05
I can't find the exact article but I used a method similar to this URL. [http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2](http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2)

---

### Post by gandaran on 2010-09-06
> **ericstrom said:**
> When I run Google Chrome and open Yahoo mail, I get the following message:

The following plug-in has crashed /usr/lib/adobe-flashplugin/libflashplayer.so

Can someone tell me why this is happening and more importantly, how do I fix it ?

Running Ubuntu Lucid Lynx 10.04
if you are on Ubuntu 32-bits update chrome, chrome version 6 32-bits has built in flash, no longer users the system installed flash.

---

### Post by ericstrom on 2010-09-07
I upgraded to Chrome version 6. That solved the previous problem but now I get a new crash of flash player. I am getting a message that libgcflashplayer.so is now crashing.

Suggestions ???

---

### Post by gandaran on 2010-09-08
> **ericstrom said:**
> I upgraded to Chrome version 6. That solved the previous problem but now I get a new crash of flash player. I am getting a message that libgcflashplayer.so is now crashing.

Suggestions ???
libgcflashplayer.so is chrome's built in flashplugin, maybe your computer cannot run flash properly! what video card and driver installed do you have?

---

### Post by Gonzalo_VC on 2011-03-09
This post is from last year, don't get mad at me... but it happens that FlashPlayer CRASHES every semester! :mad: 
Ubuntu changes (improves), the new version of this plugin is installed, and the new generations collide, **again**...  ](*,)  You can't see a video in the web or do other stuff that needs this plugin!!?? 

PLEASE, somebody develop a really good open source plugin to compete with this proprietary stuff!!!

Thank you very much!

---

