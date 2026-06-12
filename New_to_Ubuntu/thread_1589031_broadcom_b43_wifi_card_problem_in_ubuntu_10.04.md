---
title: "broadcom b43 wifi card problem in ubuntu 10.04"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by stoopidhed720p on 2010-10-05
i have a broadcom b43 wifi card in my dell latitude c840 laptop and i'm having a problem with it, when i login it says it's connected but then a minute later it disconnects and starts reconnecting and whenever it does this it disables my rooter and kicks everybody else off of the network until it's connected and it takes anywhere from just a minute to over 2 minutes for it to finish connecting and during that time it it prompts me for my network password sometimes only once but other times it prompts me for the password multiple times, my brother is having the exact same problem with his broadcom wifi card in his dell inspiron 1545 laptop with windows vista home basic, so is this just a problem with broadcom wifi cards or is there a fix for it?

---

### Post by lkraemer on 2010-10-06
Are you using the B43 Driver with Ubuntu 10.04 or STA, or ndiswrapper and
the Windows Driver (32 bit XP Driver for 32 Bit Ubuntu & 64 Bit XP Driver
for 64 Bit Ubuntu)?

B43 seems to work well for me, and I only had to install the Firmware files.

REF:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

Open a Terminal Console and do:
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
Post the output.

lk

---

### Post by lkraemer on 2010-10-06
Duplicate Post??? For some strange reason!

---

### Post by coffeecat on 2010-10-06
> **stoopidhed720p said:**
>  so is this just a problem with broadcom wifi cards or is there a fix for it?

Yes and yes. There are licensing issues with Broadcom such that the firmware cannot be included in a default install and has to be installed separately. I'm surprised you're getting any connection at all.

See here for community documentation on getting Broadcom cards working.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by anewguy on 2010-10-06
As has already been mentioned, Ubuntu does not come with a driver already installed for your wireless adapter due to the driver not being open source.  If no driver was ever loaded on the Windows PC as well, this could be the problem there also.

For Ubuntu, you have a few options for getting this running.  This partial list starts with the easiest and most recommended and works it way down from there:

[LIST]
[*]Install the restricted driver.  Look in System/Administration/Hardware Drivers and see if there is a driver already listed for your wireless adapter.  If so, enable it.  If not, do the following:
[list]
[*]temporarily hardwire your PC to the router
[*]in a terminal window (Applications/Accessories/Terminal), type:
[*]sudo apt-get update <press enter>  Just enter your normal password (it won't show as it is entered)
[*]- check in System/Administration/Hardware Drivers and see if a driver is now listed - if so, enable it.  It may download something during this procedure.
[*]physically disconnect the hard-wired cable from your PC to the router.
[*][/list]
[*]right-click on the network manager icon.  The "Enable Wireless" button should show - be sure it is checked to be enabled.
[*]left-click on the network manager icon.  Is your network listed?  Try to connect, remembering you'll need your encryption type and password/passphrase if you use encryption.  If you use MAC filtering, be sure your PC is in the MAC list in the router.
[/list]

[list]If you are unable to do the above, you could try the firmware cutter method.  I am not familiar with it in that I haven't used it, but I know lkraemer can help you there.  The firmware cutter is on the installation CD, so no network connection should be needed.[/list]

[list]3rd on the list would be ndiswrapper.  This utility lets you use your Windows XP (32 or 64 bit - matching your Ubuntu type) wireless drivers in Ubuntu.  The files for ndiswrapper are all on the installation CD as well, so you do not need a network connection to use this method either.  All you need is the .inf and .sys files from Windows XP for your wireless driver.  If you would prefer to try this method, just post back and I can give you some very simple instructions for doing this.  It is easy, and it usually works quite well.[/list]

There are probably other ways as well, but these would be the 3 easiest.

Let us know what you would like to try next, after posting back the output requested in lkramer's previous post, and we can go from there.

Dave ;)

---

### Post by stoopidhed720p on 2010-10-18
@ikraemer i'm using the restricted driver in the hardware drivers utility

---

### Post by stoopidhed720p on 2010-10-18
by the way, i didn't mean to put this in the beginner talk section, i am not a beginner i have had 2 years of experience with ubuntu, xubuntu, and linux mint

---

### Post by migs73 on 2010-10-18
> **stoopidhed720p said:**
>  my brother is having the exact same problem with his broadcom wifi card in his dell inspiron 1545 laptop with windows vista home basic
??? On the same router as yourself???
I am by no means an expert but I would try a different router.
2 different computers running two different OS's with different drivers for, albeit, similar cards, are able to crash the same router?

---

### Post by stoopidhed720p on 2010-10-18
yes on the same rooter

---

### Post by migs73 on 2010-10-18
> **stoopidhed720p said:**
> yes on the same rooter

Like I said, try a different router. Don't buy one just use one. Go to a free wifi hotspot and see if you can stay connected there, or a friends house.

---

### Post by stoopidhed720p on 2010-10-18
i failed to mention my brother left for college two months ago, so my laptop, the PS3,and my mom's blackberry are the only devices on the wifi now, my dad's computer, my desktop computer, and 2nd oldest brother's computer use the wired Ethernet connection. as far as trying a different rooter goes i cannot try another rooter because i don't have another one, i'm can't afford one right now, and there are no hotspots in this tiny little historical town i live in

---

### Post by carnytom on 2010-11-26
I have a dell c840, 10.10 & 10.04 live cd and full installs both see all available wifi's but will not connect to any. If i run the live cd for 9.10 the wifi detects and connects just fine.... any suggestions for 10.10 would be awesome...

---

### Post by fslezak on 2010-11-26
The simplest way is the NDISWrapper method. I found a very good walkthrough, which is here:

[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

---

### Post by mustangeek on 2010-11-26
Does any of the other devices have connection issues? What kinda of router is this you have and sometimes go to there site and check if there is a update for the router.

---

### Post by stoopidhed720p on 2010-11-26
!UPDATE! i no longer have this laptop, the hard drive failed, the cpu fans failed, and the dc power board blew up whenever i plugged my laptop in to charge, so i got REALLY fed up with all the constant, non-stop severe problems i've been having with it ever since i got it, so i smashed it to a million pieces all over the concrete floor

---

