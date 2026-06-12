---
title: "ath9k with AR9280 on 8.04 LTS"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by the_citrus on 2008-10-18
Hello,
I just purchased a laptop, it is a Compaq Presario CQ-70-120us. I believe it has an Atheros AR9280 chipset, but I am not 100% sure. I installed Ubuntu 8.04.1 LTS, and I'm trying to get the wireless card working correctly.

I installed a .deb package of the ath9k drivers, version 20080806, and right now, I can connect to a network, but it does not quite work the way I had hoped. The problems I am having are:
- I have to try connecting many times before receiving an IP;
- when I finally get an IP, the connection is painfully slow; and
- eventually the connection gets dropped completely.

When I'm connected, ping returns high packet loss rates (~50-60%). iwconfig reports the signal strength as 51/100, and the bit rate as 1M; when I try to change the bit rate to 54M, the iwconfig output does not change, and there is no performance increase.

I've read a few threads here about ath9k and its issues. I'm pretty sure that my wireless card is not supported by madwifi. Is there another, later, version of ath9k or another workaround that I can try to get my wireless up to speed? Perhaps a kernel upgrade (I'm on 2.6.24-19-generic). I do have one very annoying problem though - I do not have a wired connection to the internet at all, so in order to do anything, I have to download files elsewhere and thumb-drive them over to my new laptop (I'm currently using an older Vista laptop whose screen is dying fast). Furthermore, the router is not mine, and I don't have the password to it, so I don't think I can change any of the configuration in there.

Any help would be much appreciated!
-Alex

---

### Post by az on 2008-10-18
> **the_citrus said:**
> Hello,
I just purchased a laptop, it is a Compaq Presario CQ-70-120us. I believe it has an Atheros AR9280 chipset, but I am not 100% sure. I installed Ubuntu 8.04.1 LTS, and I'm trying to get the wireless card working correctly.

I installed a .deb package of the ath9k drivers, version 20080806, and right now, I can connect to a network, but it does not quite work the way I had hoped. The problems I am having are:
- I have to try connecting many times before receiving an IP;
- when I finally get an IP, the connection is painfully slow; and
- eventually the connection gets dropped completely.

When I'm connected, ping returns high packet loss rates (~50-60%). iwconfig reports the signal strength as 51/100, and the bit rate as 1M; when I try to change the bit rate to 54M, the iwconfig output does not change, and there is no performance increase.

I've read a few threads here about ath9k and its issues. I'm pretty sure that my wireless card is not supported by madwifi. Is there another, later, version of ath9k or another workaround that I can try to get my wireless up to speed? Perhaps a kernel upgrade (I'm on 2.6.24-19-generic). I do have one very annoying problem though - I do not have a wired connection to the internet at all, so in order to do anything, I have to download files elsewhere and thumb-drive them over to my new laptop (I'm currently using an older Vista laptop whose screen is dying fast). Furthermore, the router is not mine, and I don't have the password to it, so I don't think I can change any of the configuration in there.

Any help would be much appreciated!
-Alex

Hardy-Updates, which is enabled by default, provides the 2.6.24-21 kernel, which provides better ath9k support.  Are you able to connect to a wired net and update?

---

### Post by the_citrus on 2008-10-18
Ah, so a kernel upgrade is in order. Unfortunately, I don't have a wired connection that I can use. Is there any way I can download an update onto a windows machine, copy it over, and install the update?

uname -a:
Linux citrus-3 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

-Alex

---

### Post by the_citrus on 2008-10-18
Looks like I got the wireless working.
I upgraded the kernel to 2.6.24-21-generic by downloading .deb packages from the Web.
Then I ran the shell script given at [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097), using the 20080907 version. A couple restarts later, and it seems to work fine.

---

### Post by the_citrus on 2008-10-19
Or maybe not. It was working for a few hours, got kicked off, and I can't get back on. It keeps on asking me for the WEP key. Maybe I'll try kernel 2.6.27.

---

### Post by the_citrus on 2008-10-19
Yes, it looks like I just got lucky that one time....I haven't been able to get an IP from the router since then, not with kernels 2.6.24-21-generic on 8.04, and not with the 8.10 Beta, which supposedly includes the drivers in the 2.6.27 kernel.

If anyone has any suggestions, I'd be glad to hear them, but I think I'm going to give up and reinstall windows tomorrow :-\

---

### Post by az on 2008-10-19
> **the_citrus said:**
> Yes, it looks like I just got lucky that one time....I haven't been able to get an IP from the router since then, not with kernels 2.6.24-21-generic on 8.04, and not with the 8.10 Beta, which supposedly includes the drivers in the 2.6.27 kernel.

If anyone has any suggestions, I'd be glad to hear them, but I think I'm going to give up and reinstall windows tomorrow :-\

The wireless light does not work when using the Linux driver for me.  That means that if I press the wireless button, I don't know if it's on or off.  Is this the case for you?  If so, perhaps you turned off wireless and don't even know it?

It took me the better part of a day to figure that out...

---

### Post by the_citrus on 2008-10-19
The wireless light was working for me. I'm going to try again in a month or so - maybe the driver compatibility kinks will be worked out by then.

---

