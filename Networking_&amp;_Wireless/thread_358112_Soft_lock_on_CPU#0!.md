---
title: "Soft lock on CPU#0!"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by bunnny on 2007-02-10
Hi
I have been strugling with this problem for two days.
I have a fully working ubuntu 6.06 running, but I decided to try something "new",
so installed xubuntu 6.10 (AMD-64) command-line system.

The problem:
I can't get my level one wnc-0301 v.3 (ralink rt2561 chip) wireless network card to work.
I been using this howto (wich worked like a charm on my ubuntu 6.06 (i386) system)
[http://www.ubuntuforums.org/showthread.php?t=296822&highlight=ralink](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=ralink)

but when I try to use the card (i.e. "dhclient ra0") I get this "soft lockup on CPU#0!" error followed by a system crash.

I have tied both ralink's drivers and those from serial monkey.

I have searched this forum without succes

What to do???
Please help

---

### Post by warri0r on 2007-02-11
oops me too having this problem for the past 2 days but discovered the solution some 2 mins ago :P

u can temporarily solve this problem by turning of your pc and restart the router and then the system.

voila your system ll boot up clearly

but this ll happen frequently ,cud any1 provide us a reliable solution 

myself using a ralink chip (linksys wmp54g wireless card)

help us plz :(

---

### Post by bunnny on 2007-02-12
Hehe strange problem

My card seems to work as it should except this bug.

"iwlist scan" finds my router, but after the output I get this luckup bug.

---

### Post by Orion2000za on 2007-02-12
Got a similar problem with a built-in wireless on a laptop. What I have discovered is that the wireless must be activated when I switch on, if I used my "hot-key" to switch it off and then reboots I get the soft bug no fail. If I leave it on and then boot then no problem. 
Sometime I have to boot in "recovery mode" so I can hit "hot-key" and activate the card.

so I guess your router has to be on so the PC can detect it or you get kernel lockup somehow.

Sinclair

---

### Post by bunnny on 2007-02-13
Well mine isn't an built in card, so there is no "button".

But should it be possible to turn wlan "on" on bootup?

I do not get this error if I unplugg the router, but then I cant get any network (of course)

Please help

---

### Post by bunnny on 2007-02-18
I still have this problem, and I am confident in that this is solveable

Please help

---

### Post by Amt0571 on 2007-02-18
Having the same problem too with a PCI rt61 card... this has completely screwed my system since this it can't be connected wired. I had to remove the PCI card in order to boot the system.

It's seems the solution is nowhere near and I'm starting to think about switching distro...

---

### Post by bunnny on 2007-02-23
Shouldnt this problem been solved by now, it seems like Im not alone with this bug, so why have none find an solution? not to be a bitch or anything :)

---

### Post by GordSellar on 2007-03-13
What's weird is that I get the same problem when I insert a 2-gig card into my dv2000's built-in card reader slot (which works fine in Windows, and IIRC worked okay with a 1-gig card too).

---

### Post by bunnny on 2007-03-25
I have been strugling with tihs problem for some time now. It shuldn't be huge problem to solve (it works in dapper so why not). I have tried to configure the kernel, but I don't know where to look.

Please help... is it the kernel, if so wich work?

---

### Post by zakhooi on 2007-05-26
I'm having exactly the same problem with my Sitecin WL-122 V2 on Ubuntu 7.04

I tried RT61_Linux_STA_Drv1.0.4.0 and RT61_Linux_STA_Drv1.1.0.0 but they both have this problem.

A few notes:

The "Soft lock detected on CPU#0!" error does not appear immediately after inserting the PCMCIA card or when loading the driver.
It happens as soon as the interface (in my case ra0) is brought up, then after a few seconds my lappy hangs completely and the error appears in the console.

/etc/network/interfaces:
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid "<MYESSID>j"
pre-up iwpriv ra0 set WPAPSK="<MYNETWORKKEY>"

/etc/modprobe.d/aliases:
alias ra0 rt61

/etc/modprobe.d/blacklist:
blacklist rt61pci

Has anyone solved this issue? If please share the solution.
I'm struggling with this now since the launch of feisty fawn and it's frustrating.

Thanks in advance

---

### Post by illiadum on 2007-05-31
This is driving me crazy too.  I've installed Feisty on my girlfriend's machine (AMD64), it has an RT61 chipset in the wireless card.  Everything boots up great.  I'm not even connected to any router yet as mine and everything around is encrypted.  But...about 2 to 10 minutes after booting up, whether in Recovery or normal mode, I get the "Soft Lock Detected" error.  Everything freezes, and I'm pissed, since this of course makes the entire OS completely useless.

I had the exact same chipset wireless card in another machine (Also AMD64) with the RT61 drivers installed on Gentoo.  The gentoo install was beatifully stable, but didn't recognize the wireless until RT61 was installed.  Once installed, Gentoo also gave me the big freeze at random several minutes after bootup.  So...I'm thinking this is a bug with the 64-bit version of the RT61 drivers.  If anyone can get this resolved...oh man would I be one happy camper.

BTW, on the Gentoo box, I got so frustrated dealing with lock-ups (after all this isn't windows), that I actually purchased a new Wireless card with the Atheros chipset.  Madwifi drivers work like a charm (No Lock Ups).  I really don't want to buy yet another wireless card.  :)

---

### Post by Bealer on 2008-04-26
I now get this problem. Argggghh. 

Feisty works fine on my laptop, I can run the LIve CD and have it installed no problem. 

I just downloaded Hardy (both live and alternate versions). I get to the boot menu, select to install Ubuntu etc... Then it just freezes. 

Must be an issue with the kernel. It's frustrating when a bug gets introduced into a newer version.

---

### Post by illiadum on 2008-04-26
Hi Bealer,
I'm not sure the issue you're having is the same.  As far as I know the lockup caused by RT61 drivers has been fixed in the newer versions.  Unless you're sure you've got a wireless card that is using these drivers, I would suggest probably starting up a new thread or checking for an existing thread with lockups at boot time.

I would also post what hardware you're running and as much information as you can.  (ie, IDE drive/SATA drive, what error messages are you getting, have you tried booting in text mode, etc).

---

