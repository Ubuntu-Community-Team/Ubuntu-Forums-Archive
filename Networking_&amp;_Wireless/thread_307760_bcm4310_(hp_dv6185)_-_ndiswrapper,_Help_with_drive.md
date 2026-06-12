---
title: "bcm4310 (hp dv6185) - ndiswrapper, Help with driver installation"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by fisherking on 2006-11-27
Hi all, 
I have recently bought myself a HP dv6185 laptop with an integrated bcm4310 wireless NIC, but I have some serious issues getting it working!

I tried out the fwcutter stuff at first and I got the card working, but it was really, really slow! I couldn't get that fixed so I decided to try ndiswrapper instead. 

I found an installation guide at sourceforge ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)). I double checked what kind of Wireless card I had... Downloaded the driver from HP (which I also use on my Windows installation on the same computer). The ndiswrapper version I use is 1.29 (installed by: make, make install as superuser).
I extract my driver with cabextract and installed it with:

```

ndiswrapper  -i bcmwl5.inf

```

and the message I got was:

```

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

```

Now the installer guide suggest that you type in ndiswapper -l to confirm that everything is ok! 
But in my case it's not!

```

 sudo ndiswrapper -l
installed drivers:
bcmwl5  invalid driver!

```

I think this is strange since the card is supported by this driver (the installer guide says so anyway). 
Here is the output from lspci -vvv:

```

03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1361
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at c0400000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```


Please help me with this!

---

### Post by fisherking on 2006-11-28
Ok... I fixed it! 

I installed the latest ndiswrapper (1.30) and it works perfectly! Couldn't be happier

---

### Post by octane_olga on 2006-12-04
I'm on an HP Pavillion dv9074ea (dv9000) and have a bcm4310 wireless card. I've struggeled for days on end with this, and now it's working beutifully thanks to this post. Thank you very much! (almost given up on ubuntu ;) )

To others struggeling: VERY IMPORTANT: the latest version of ndiswrapper is essential to get this working!!

BUT IT WORKS! Oh, happy day...

---

### Post by fisherking on 2006-12-05
Nice :D

---

### Post by elizleisndahizle on 2007-03-23
:guitar: rockin' I have been about to throw my dv9000z out my window.  Plus my battery doesn't charge past 51% now.  But this rocks thanks.

---

### Post by FNGtyler on 2007-03-23
im getting the same problem i will try newer version of ndiswrapper

---

### Post by CraniumDesigns on 2007-03-23
anyone know of this will work on a bm4303? i have an hp pav zd7000.

---

### Post by SurferGTO on 2008-03-03
i cant get it to work at all. ndiswrapper -l shows that the drive is installed and the device is present. however an iwconfig command shows that i still have no connections. wtf am i doing wrong??

---

### Post by Limbic on 2008-03-03
I had a freaking nightmare problem with the wireless for my DV2715nr, but I finally got it fixed.  The problem, I think, is that there appear to be several different BCM4310 (rev 1) cards that all require different drivers.  Some drivers will install but won't detect the hardware, others won't detect anything at all.  Just a huge pain.

It originally looked like the problem was NDISWrapper but  that wasn't it.  I tried all the different ways of installing it, but now that I have the right driver it works immediately with the NDISWrapper version from the Repositories.

Here's what made it work for me, but bear in mind I'm very much a Linux noob.  Here's [the guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and [the driver]("http://ubuntuforums.org/showthread.php?p=4379996") I used to get mine working.

The most important part for me was getting the right driver, as I said, so here's the step from the above guide that made all the difference:

> 3.2.1. PCI Wireless Adapter

   1.  Open a Terminal (Applications | Accessories | Terminal), type ```
lspci
``` and press the return/enter key.
   2.  Look through the output of the lspci command for an entry for your wireless card.
   3.  Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0.
   4.  Now, type ```
lspci -n
``` into the Terminal and press return.
   5.  Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400.

The PCI ID that came up for my dv2715 was 14e4:4315 which keys to the driver I linked above.  If you search around on the web, you'll find some of the same wireless card that use 14e4:4312 as a PCI ID, but the drivers aren't the same.  That four digit code behind the colon is the important bit; the "lspci" command tells you the card is a Broadcom BCM4310 (rev 1) the driver and NDISWrapper instead see it as a Broadcom 4315.  Likewise with the BCM4310 (rev 1) that the drivers and NDISWrapper see as a Broadcom 4312.

Once I had the correct driver I was able to install it with the GUI from the System -> Administrative ->"Windows Wireless Drivers" and can have it up and running a few minutes after an OS install.

---

