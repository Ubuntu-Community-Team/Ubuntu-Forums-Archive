---
title: "WLAN not working on new Apple iMac (Edgy Eft)"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by kirby-k on 2006-12-10
Hi there,

I'm currently trying to install Ubuntu 6.10 (Edgy Eft) on a new Apple iMac (17", 2,0GHz Intel Core 2 Duo). WLAN does not work -- most probably due to the new Broadcom 4328 Chip, which is obviously not supported.

I already tried to install the bcm43xx Driver and it's firmware packages, according to 
[http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)
and
[http://wiki.ubuntuusers.de/WLAN/Broadcom_bcm43xx](http://wiki.ubuntuusers.de/WLAN/Broadcom_bcm43xx)

However, iwconfig does not list any devices with wireless extensions.
I used firmware from bcmwl5.sys, version 3.120.27.0, since bcm43xx-fwcutter was unable to cut the firmware from Apples AirPort2-driver that came with Mac OS X.

Unfortunately, WLAN is the only way for me to get internet access, so I really need WLAN working. Any ideas?

---

### Post by kirby-k on 2006-12-15
Hi there,

in the meantime I tried to use ndiwswrapper to solve the problem; however it seems to be diffcult obtaining the required windows driver. Drivers for other devices using Broadcom's 4328 chipset are quite easy to obtain; however, they fail to work, even if I rename and edit configurations files in /etc/ndiswrapper to match Apple's vendor/product id.

BootCamp provides the required driver inside an 128MB .exe file which I can't extract and which also fails to execute on an old Windows 2000 Computer that I dragged out in vain from under my bed.

So again: has anybody out there a clue how to make Broadcom's new pre-802.11n chipset (14e4:4328) which is built into new Apple iMac (Intel Core 2 Duo) work with Linux?

Kirby.

---

### Post by automat on 2006-12-21
Do you have windows installed and configured with the boot camp drivers cd?  If so, I can help.  If not, you'll have to figure out how to extract the drivers from the .exe, and I don't know where to start with that.

---

### Post by kirby-k on 2006-12-28
Hi there,

I finally made it work. There is unfortunately no linux driver for Broadcom's 4328 WLAN chip, so I had to use ndiswrapper. 
This means you need to get a working windows driver first -- as I found out, only Apple's own windows driver will work. You can grab it from the windows driver CD, which Apples Boot Camp Software generates for you.
Unfortunately, once you have already installed linux, Apple's Boot Camp Software won't start. By right-clicking the  Application, you can open its contents, finding an .exe file which will install the drivers required to run windows on your apple computer. 
Unfortunately this file is not a self-extracting exe, so I needed to get an old computer running W2k from under my bed. It would execute the driver install program, but only to say that this program only works with windows xp. However it had already unpacked its contents, so the trick is to leave the program open, and go to your Application Data Folder, finding a newly generated folder with some rather accidental name, containing the desired "Macintosh Drivers for Windows XP.msi" file. 
Adding to my frustration, it was rather difficult extracting this packed archive, as it is impossible with windows' own means. Finally having retrieved bcmwl5.inf/bcmwl5.sys setting up WLAN using ndiswrapper was a breeze.

If anyone needs help setting up Ubuntu 6.10 on an Apple iMac (intel Core2 Duo processor), feel free to contact me.

I also put together some information on installing Edgy Eft on Core 2 Duo iMacs here: [http://forum.ubuntuusers.de/topic/57318/#494548](http://forum.ubuntuusers.de/topic/57318/#494548)
This page is in german, if you have any questions or suggestions, contact me.

---

### Post by ashokcm on 2007-01-18
Did you manage to get sound working? If so please can you explain how.

---

### Post by kirby-k on 2007-01-18
> **ashokcm said:**
> Did you manage to get sound working? If so please can you explain how.

That was quite easy. Sound works out-of-the-box; the only problem was making the internal speakers work.
You simply start a mixer (alsamixer should be fine) and select "Line in as Output" (unmute it), then choose your desired volume using the "side" speakers. That's it!

Kirby.

---

### Post by pandu on 2007-02-11
hi Kirby,

i'm newbie for use linux, now i try using ubuntu edgy....
i already install ubuntu edy on imac intel 2.0 core 2 duo...
but my sound and wlan still not work...
can you help me explain how to make it that works??

thanks
pandu

---

### Post by kirby-k on 2007-02-12
Hello Pnadu, 

welcome to ubuntu.

> **pandu said:**
> 
i'm newbie for use linux, now i try using ubuntu edgy....
i already install ubuntu edy on imac intel 2.0 core 2 duo...
but my sound and wlan still not work...

My previous post explains how to get sound working (more precisely: how to get the internal speakers set to a volume that you can hear, since sound itself works out-of-the-box).

WLAN ist a bit more difficult, a first start could be the ndiswrapper howto of ubuntu.org's wiki
([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))
Simply, ndiswrapper lets you use a windows network card driver with linux.
The only problem with setting up ndiswrapper in edgy was obtaining the windows driver for this particular network card -- see my previous post for details.

If you have any more specific questions, simply keep asking as I will help you in any way and as much as I can. 
However, I will not provide a step-by-step solve-the-problem-without-knowing-what-I'm-doing solution.
So if you have questions about more general aspects of linux system administration, you should consider reading some introductions first.

Kirby.

---

### Post by ashokcm on 2007-04-25
I tried what you suggested for sound. But still no sound from the speakers :confused:

---

### Post by kirby-k on 2007-04-26
> **ashokcm said:**
> I tried what you suggested for sound. But still no sound from the speakers :confused:

Maybe you should post the output of 

~$ /usr/bin/amixer

This should help to identify the problem. See that all relevant volumes are set to sane values (especially the 'PCM' and 'Side' volume).

Kirby.

---

### Post by ashokcm on 2007-07-31
After trying out a lot of troubleshooting, I finally gave up. Just then the other day I was tinkering around with alsa and decided to change everything to OSS. Once I did this, sound magically works for xmms. But it does not work for any other application. None of the application throws any errors. Its just that they are all mute! Anyways I am happy to have atleast xmms working. Seems there is some problem with alsa and imac 17".

Now I have an iMac 17" with everything (well almost) working perfectly. :)

---

### Post by ashokcm on 2007-07-31
BTW. In the meantime I upgraded to Fiesty, so cant say if it started working because of this.

---

