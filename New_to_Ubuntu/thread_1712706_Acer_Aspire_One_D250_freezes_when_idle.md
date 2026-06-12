---
title: "Acer Aspire One D250 freezes when idle"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by MIKRO402 on 2011-03-23
Hi all ai am a newbie to Ubutu
. I have a problem with this machine freezing up if left idle for a while. When it happens I have to power off and restart.. This happens both on battery and ac.

Thank you

---

### Post by jtarin on 2011-03-23
How big is you swapspace and what is the total size of ram you have?

---

### Post by jtarin on 2011-03-23
How big is your swapspace and what is the total size of ram you have?

---

### Post by MIKRO402 on 2011-03-23
> **jtarin said:**
> How big is your swapspace and what is the total size of ram you have?

The swap is 3.1 G and  RAM is 992.1

---

### Post by 5149.5 on 2011-03-23
My D255 doesn't have that issue. I only have 1G of ram w/5G of swap space.

---

### Post by jtarin on 2011-03-23
I'm going to point you to some [Ubuntu documentation on the Aspire]("https://help.ubuntu.com/community/AspireOne"). Keep in mind it is slightly dated, but perhaps something will strike a chord.

---

### Post by DogMatix on 2011-03-23
Hi

I am a Acer One ZG8 owner. With Ubuntu 9.01 and 10.10 I had similar issues. Usually it happened during battery operation. However, having read the Aspire documentation at the link posted by jtarin I suspect it could be something to do with an SD card I permanently had in the SD expansion slot.

Unfortunately, I have recently updated that netbook to 11.04 and I haven't had the issue 'yet'. But I have removed the SD card anyway and will see if the problem persists. If it doesn't I will replace the SD card and see if I can replicate the problem. I will post anything of interest here.

I must admit though its a bloomin' annoying problem when you leave your computer for 15 mins then return to it and find it won't wake and a hard restart is required.

---

### Post by MIKRO402 on 2011-03-24
> **jtarin said:**
> I'm going to point you to some [Ubuntu documentation on the Aspire]("https://help.ubuntu.com/community/AspireOne"). Keep in mind it is slightly dated, but perhaps something will strike a chord.

Thank you for the link. I changed  the==>System=Preferences= Appearance -Visual Affects to None.
I had read somewhere to disable affects.

---

### Post by Dutch70 on 2011-03-24
What graphics card do you have? 

or post the output of...
```
lspci
```

---

### Post by MIKRO402 on 2011-03-24
> **jtarin said:**
> I'm going to point you to some [Ubuntu documentation on the Aspire]("https://help.ubuntu.com/community/AspireOne"). Keep in mind it is slightly dated, but perhaps something will strike a chord.

> **Dutch70 said:**
> What graphics card do you have? 

or post the output of...
```
lspci
```

Aspire-one:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132

---

### Post by jtarin on 2011-03-24
> **MIKRO402 said:**
> Thank you for the link. I changed  the==>System=Preferences= Appearance -Visual Affects to None.
I had read somewhere to disable affects.Did this help?

---

### Post by Dutch70 on 2011-03-24
I know that card is kind of buggy, I don't know what the fix is for it.

To help narrow the problem down though. 
1. Have you ever tried going to desktop effects & selecting "none" to see if it still freezes when left idle?
2. Does it ever freeze when it's not idle?

Edit: disregard the 1st question, I had forgotten that you did. So, as jtarin said...Did it help?

---

### Post by RubenAlonzo on 2011-03-24
Is it getting too hot? 

I have an eMachines em250, essentially the very same computer except yours says Acer on it. I have 2 gigs ram and a 250 gig hdd. I have noticed these little netbooks get quit warm if not in a well ventilated environment.

One more thing, did you ever have a problem with Windows (if you ever had Windows on it) lock up on you?

My 10.10 Netbook Remix never did lock up on me, even with the SD Card always in the slot.

---

### Post by MIKRO402 on 2011-03-24
> **jtarin said:**
> Did this help?

No, it's still freezing.

---

### Post by MIKRO402 on 2011-03-24
> **Dutch70 said:**
> I know that card is kind of buggy, I don't know what the fix is for it.

To help narrow the problem down though. 
1. Have you ever tried going to desktop effects & selecting "none" to see if it still freezes when left idle?
2. Does it ever freeze when it's not idle?

Edit: disregard the 1st question, I had forgotten that you did. So, as jtarin said...Did it help?

No freezing while in use.

---

### Post by MIKRO402 on 2011-03-24
it does seem to happen only when on ac

---

### Post by MIKRO402 on 2011-03-24
> **RubenAlonzo said:**
> Is it getting too hot? 

I have an eMachines em250, essentially the very same computer except yours says Acer on it. I have 2 gigs ram and a 250 gig hdd. I have noticed these little netbooks get quit warm if not in a well ventilated environment.

One more thing, did you ever have a problem with Windows (if you ever had Windows on it) lock up on you?

My 10.10 Netbook Remix never did lock up on me, even with the SD Card always in the slot.

I had Win 7 on it (which I removed). It never locked up on Win 7...

---

### Post by DogMatix on 2011-03-27
Since removing the SD card from the 'expansion' slot Suspend and Hibernate have been working fine for me.

Also I used to have Win XP on the netbook and the SD card didn't cause problems waking the computer when booted into that.

---

### Post by MIKRO402 on 2011-03-31
Well I have discovered that as long as I have the pc open it doesn't freeze up. If I close the screen it freezes.:confused:

---

### Post by jtarin on 2011-03-31
> **MIKRO402 said:**
> Well I have discovered that as long as I have the pc open it doesn't freeze up. If I close the screen it freezes.:confused:
Try logging off (not shutdown, not restart)before closing.
[Another link with some things to consider.]("http://ubuntuforums.org/archive/index.php/t-1341435.html")

---

### Post by MIKRO402 on 2011-03-31
> **jtarin said:**
> Try logging off (not shutdown, not restart)before closing.
[Another link with some things to consider.]("http://ubuntuforums.org/archive/index.php/t-1341435.html")

Ok I'm trying that now.
Do you think it could be heat related? I noticed when the lid is closed it gets quite warm...

---

### Post by jtarin on 2011-03-31
In my searching for an answer to your problem it appears to me that this particular model has been problematic regardless of what Operating System is on it.So your looking for a best case scenario.....more than likely less than perfect.

---

### Post by LargePiece on 2011-05-03
10.04 was totally solid on my aspireone 522 netbook. No lockups or crashes. Since installing 11.04 it locks up regularly and not just when idle either, sometimes it'll lock when I'm doing stuff. 

I've tried installing Kubuntu 11.04 from a flashdrive but that locks up during the install and in different places each time too. I've seen a bug report for a similar problem here:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2880382.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2880382.html)

This post here has some helpful stuff too, I'm about to try booting into windoze then back to kubuntu install to see if it stops the lockup:

[http://ubuntuforums.org/showthread.php?t=1702462&page=2](http://ubuntuforums.org/showthread.php?t=1702462&page=2)

---

