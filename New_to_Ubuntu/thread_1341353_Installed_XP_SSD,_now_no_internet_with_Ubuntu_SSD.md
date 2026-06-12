---
title: "Installed XP SSD, now no internet with Ubuntu SSD"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by sunwatt on 2009-11-29
My Dell Mini 9 came with a 8GB SSD with XP on it. 

As soon as I got it, I removed the 8GB SSD with XP and put in a 32GB SSD with Mint 7 on it.

All is well.

Today, I plugged in my 8GB SSD with XP on it, and played with that about 20 minutes, for the 1st time.

God I hate Windows!

Installed the 32gb ssd with Mint 7 on it and now I cant connect !!

The XP did something thats blocking Mint from working.

I use an ethernet cable, no wireless here.

Right now I'm on my boatanchor laptop thats got Mint 7 on it, and its working fine.

I put the XP SSD back in the Mini 9 and it goes online!!!!

Obviously Windows is playing dirty!!!

Hellllp!

Jim

---

### Post by u.b.u.n.t.u on 2009-11-29
It appears that XP may have customised your net connection and that Mint 7 is unable to read such.

Therefore I would check the net settings for a possible solution.

Check your modem/router settings.

---

### Post by teward on 2009-11-29
The hardware shouldn't be the problem, unless Windows updated your hardware's internal software.

My recommendations: (1) stop swapping drives unless you have no choice, and (2) **cold restart** your computer (that is to say, hit "SHUT DOWN", then wait for about 20 minutes, then reboot with your Linux drive in).  This *might* work.  (3) if it still refuses to work, then I blame Windows as a culprit, and believe that you need to take your computer to a certified tech to take a look (they SHOULD be able to work with linux, if they're official techs).

***EDIT (because I'm an evil person):

Windows *_**never**_* affects the modem/router's internal hardware.  It wouldn't be able to access its software unless the user let it.  However, if the router is the problem, its possible it's not recognizing Linux as compatible, but that's not related to Windows.

END EDIT ***

---

### Post by sunwatt on 2009-11-29
No router, and the modem is very basic. On/off button.

Ive attached screenshots of my Mini 9.

I've never had any problem swapping SSD's with Linux OS's on them.

Remove battery, and swap SSD, new OS. Never a problem.

I have 9.10 on a 16gb ssd and my regular Mint 7 on the 32gb ssd.

Putting in the XP SSD that came with my Mini 9 did something, and I've got a bad feeling.

Why does the XP 8GB SSD connect and my Linux SSD's will not?

After a 20 minute testing?

As long as the battery is removed 1st, whats the harm in swapping SSD's?

I cant see how the xp ssd could do this.

But obviously, something is very wrong.

Thanks for the help.

Jim

---

### Post by teward on 2009-11-29
Okay, as I said, swapping out drives (solid-state drives or other types of drives) continuously **unless you absolutely 100% have to** is never a good idea.  However, also as I said, Windows shouldn't, but might have, taken over your wired devices.  Do me a favor though.

(1) Just humor me and cold restart your computer by shutting it down and leaving it there with the battery removed for about 5 minutes (I said 20 minutes earlier because that's usually how long I wait if I'm doing cold restart as a diagnostic tool, but 5 minutes would probably be fine enough).  Then...

(2) Boot into your linux drive.  Can you show me the output from the terminal command
```
lspci
```so I can see if Linux is even detecting your network card?


***EDIT

A thought is that the hardware itself was screwed up by Windows.  Now I only have 1 hard drive, dual booting with Linux and Win XP, and its not Solid State.  And with SSDs, your not really supposed to swap them out much.

END EDIT***

---

### Post by u.b.u.n.t.u on 2009-11-29
sunwatt, if you have a live CD, then perhaps consider noting the network settings and then apply such.

I wouldn't dismiss the modem settings until you have examined such under XP and Mint 7. Yes modem settings typically need to be applied, but it can't hurt to just check this. At least it will definitely narrow the focus of the error(s).

I do think this can easily be fixed. Finding the cause is the challenge.

---

### Post by sunwatt on 2009-11-29
OK, I took out the btry and let it sit afew hours, my wife came home.

Here's the output from the terminal. I had the ethernet cable plugged in. 

jim@jim-mini9 ~ $ lspci
-00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


Thanks!!!

I'll be away all day tomorrow, but take my Mini 9 along on the chance the wifi will kick in.

Jim

---

### Post by sunwatt on 2009-11-30
im in town, wifi works. this happened once before. ethernet failed at home, i think my dell mini 10v came with xp, and i installed ubuntu 9.04 on it.

no ethernet connection!!

took it to town, wifi worked, just like today.

soooo maybe when i go home my ethernet cable will work.

i gave my daugthter my 10v and she loves ubuntu!

im on my mini 9 mint 7 right now.

jim

---

### Post by u.b.u.n.t.u on 2009-11-30
All the best!

---

### Post by teward on 2009-11-30
A thought is that Windows updated the firmware of your ethernet card, and Ubuntu is not compatible with it.  If that's the case, then its a hardware issue we might not be able to help you with.  At the least, we can determine from the output of lspci on your system that your Linux drive is indeed detecting your network card, so that is not the problem.

I think it might be a drivers issue.  Have you seeked updated Linux drivers (if any) for your network card?

FYI: Your network card is:
```
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

**EDIT: I know that the drivers for similar networking cards are hard to find for Windows, as Realtek doesn't like giving out drivers (usually because they use custom hardware codes and stuff). **

---

### Post by u.b.u.n.t.u on 2009-11-30
If drivers were automatically installed then there should hopefully be an option to download and manually install a previous version. Such may be worth exploring to see if it is relevant.

---

### Post by teward on 2009-11-30
I agree.  You might search for a slightly-older driver version.

**EDIT: Afterthought:  I checked with my other tech friends, and they don't believe Windows caused anything, nor do they believe it was a hardware problem. **

---

### Post by sunwatt on 2009-11-30
Thanks everyone.

When I connected at a hot spot in town on wifi, it was ruff going, but after afew tries it went online.

Just got home, and all is "self repaired"!

I'm online right now via ethernet cable. 

On my Dell Mini 10V that came with XP, (4 months ago) I installed 9.04 right away, and it refused to connect to my ethernet cable. I was frustrated, brand new laptop and cant get Ubuntu to go online!

So I went to town and it connected at a hot spot - just like today, I came home and it connected .

No drivers were downloaded in either case.

I'm a tadpole, Windows since 1992, and only afew months on Linux - but it seems M$ takes over the computer, on the board where the ethernet plugs in. Like I said, I dont know much. But twice this has happened, and finding a hot spot repaired the problem.

Sidebar: At Thanksgiving dinner at my daughters house, there was a "dead" locked up virus infected  desktop (800mhz) decent little PC. I brought along a Mint 7 DVD, got the PC to boot up live and I installed Linux Mint 7 on there and brought that dead PC back to life.

Thats my 1st. wooooo hooooooooooooooo

Then I showed off my Dell Mini 9, and right away I found a neighbour calling themselves "Gnome"! The Mini 9 connected at 60%, and all afternoon folks were checking it out, watching youtube videos, and impressing everyone.

T Day I gave my Dell 10V to my daughter (Ubuntu 9.04) and she loves it. "Easy to use, and FAST", she said.

So, Sunday I messed up my Mini 9, and I almost wished I had my 10V back!  

But now my daughters a Linux user, and today this Mini 9 repaired itself.

AMAZING.

Thanks again to everyone!!

Jim

---

