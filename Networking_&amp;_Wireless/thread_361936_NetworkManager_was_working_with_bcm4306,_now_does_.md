---
title: "NetworkManager was working with bcm4306, now does not scan wireless."
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by fatespeaks on 2007-02-15
A few weeks ago, I upgraded to Feisty and my wireless setup started working very well.  NetworkManager displayed available networks and prompted for WPA keyphrase.  This was a lot nicer than the manual wpa_supplicant setup I had running (It would loose connection regularly.)

About 2 days ago, my blissful wireless experience ended.  I am not sure if something in the myriad Feisty updates regressed, or if I caused the damage by trying to use my Prism54 card (The bcm4306 is borrowed).

I noticed that the Network Settings app from Control Center now sees "wmaster0" and "wlan0" instead of "eth1".  I read that Debian and Ubuntu modify NetworkManager to not manager interfaces listed in /etc/network/interfaces so I removed wlan0 from that file.  NetworkManager looked like it was scanning the network, but it did not discover my AP.

I have also tried to reinstall NetworkManager, bcm43xx_fwcutter, and wpa_supplicant via synaptic.

Anyone else experience something similar?
Any ideas on how I can fix this?

Cheers,
Aaron Ahlemeyer

---

### Post by bnuytten on 2007-02-15
First, make sure the interfaces is up. It does not necessarely have to have an IP address etc. But if it is down you cannot scan. I.e. you have to connect the cable, or in this case the "air".
```
#ifdown wlan0
# iwlist wlan0 scanning
wlan0     Interface doesn't support scanning : Resource temporarily unavailable
#ifup wlan0
#iwlist wlan0 scanning
wlan0     Scan completed :
<snip>

```

---

### Post by fatespeaks on 2007-02-15
Thanks for the reply.

I have discovered more info about the problem, and I think I am closer to resolving it.

I decided to check the syslog.  (Probably should have checked that a few days ago, but I am a Windows convert.)  Anyway, it says that my firmware is old and versions before 4.x are not supported.  I tried a few .o's and .sys's with the fwcutter-005 from Universe.  None of my driver files  produced a 4.x or later firmware.

Next, I downloaded and compiled fwcutter-006 from [http://developer.berlios.de/projects/bcm43xx/](http://developer.berlios.de/projects/bcm43xx/) then I downloaded broadcom-wl-4.80.53.0.tar.bz2 from somewhere and extracted the wl_apsta.o file.  I cut the driver with a command like this: ./bcm43xx-fwcutter -w /lib/firmware wl_apsta.o

Now scanning works!  I see my AP and others.  KeyManager prompts for my password then several seconds later my computer completely locks up.  I have repeated this last routine a couple of times.  Only a hard reboot brings the system back.  I'll look for more firmware sources tomorrow.

Cheers,
Aaron

---

### Post by fatespeaks on 2007-02-16
I was unable to locate another source for 4.x firmware.  However, rebooting with kernel 2.6.20-6 ( instead of 2.6.20-8 ) and loading the firmware from Motorola resolved the issue.  I am untethered again, woo-hoo!

Cheers,
Aaron

---

### Post by grantbuntu on 2007-02-17
You're not imagining it!  I finally got my WPA wireless connection working in Feisty Herd 3 (using my Broadcom card) but I am not having any success with Herd 4 so far.  To begin with, all I see is the options for WEP.  

If I recall correctly, with both Herd 3 and 4 I installed bcm43xx-fwcutter_005-2_i386.deb, put wl_apsta.o on my desktop, and then ran 

sudo bcm43xx-fwcutter  -w /lib/firmware ~/Desktop/wl_apsta.o

Then rebooted and tried to modify some network settings.  But no WPA options this time with Herd 4.  And it worked so easily in Herd 3! :confused:

---

### Post by lamalex on 2007-02-17
> **grantbuntu said:**
> You're not imagining it!  I finally got my WPA wireless connection working in Feisty Herd 3 (using my Broadcom card) but I am not having any success with Herd 4 so far.  To begin with, all I see is the options for WEP.  

If I recall correctly, with both Herd 3 and 4 I installed bcm43xx-fwcutter_005-2_i386.deb, put wl_apsta.o on my desktop, and then ran 

sudo bcm43xx-fwcutter  -w /lib/firmware ~/Desktop/wl_apsta.o

Then rebooted and tried to modify some network settings.  But no WPA options this time with Herd 4.  And it worked so easily in Herd 3! :confused:

were you able to connect to a WEP? I can't get anything after the kernel update in herd 3, im about to try herd 4

---

### Post by fatespeaks on 2007-02-18
FYI, there is a bug posted in Launchpad against the 2.6.20 kernel.
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85404](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85404)

---

### Post by grantbuntu on 2007-02-19
I have added my own details to the bug report using:

uname -a

dmesg < dmesg.log

and

lspci -vvnn > lspci-vvnn.log

The more who could do the same the better.  It would make my life a lot better if this bug could be fixed.  Without a wireless connection I cannot access the internet repositories etc etc etc.

---

### Post by grantbuntu on 2007-02-20
The bug was reported by Michael Buesch so a big thanks there first.  I'm seriously grateful that the bug is not my imagination, or my fault, and that someone knows how to fix it.

Anyway, here is the most recent post to the bug from Michael Buesch  at 2007-02-20 20:12:36 UTC:

> You do _NOT_ need to answer to this bug entry. We know exactly what's broken and how to fix it.
It was a mismerge. There is absolutely no further testing or bugreporting needed.

The whole purpose for which I opened this bug, is to make the ubuntu
developers aware of the breakage, as I constantly (still) receive tons
of bugreports for the bcm43xx driver, caused by this. So please don't
spam my mailbox even more.  :) 

Thanks.

Of course, it might help if the status changed from "Unconfirmed" and its importance from "Undecided" :p

---

### Post by grantbuntu on 2007-02-22
It looks like things are going to be fixed - this from Matthew Garrett at 2007-02-21 21:36:53 UTC

> Please stop replying to this bug. It's being dealt with.

PLUS the status is now "In Progress" - here's hoping for success with Herd 5![-o<

---

### Post by wtruong on 2007-02-23
I have this problem too! It just stopped working one day.....

---

