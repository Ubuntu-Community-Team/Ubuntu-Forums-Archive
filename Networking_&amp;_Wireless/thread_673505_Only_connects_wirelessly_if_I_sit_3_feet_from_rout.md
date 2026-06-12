---
title: "Only connects wirelessly if I sit 3 feet from router"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by portach king on 2008-01-20
Hi,
I've been using 32-bit Gutsy Gibbon ever since it's launch and been quite happy. On my first installation I had a problem with the Restricted Drivers that came with it, so I tried using ndiswrapper and, eureka, wireless, no problems.
Last week I decided to do a fresh install of Ubuntu, thinking I could resolve the issue the same way again, Boy, was I wrong.

I've spent that last week scouring the net for a solution, and have tried every method of getting the wireless working that I could find, and now I am posting here simply as I cannot find any answers to my problem.

The problem is that while the wireless card works, it's working very badly. It wont connect unless I'm sitting very close to the router itself and then disconnects if I move away at all. This is a nightmare as I use my laptop for college a lot and I have no idea where there routers are. 

I hope somebody can help, I've reinstalled Ubuntu twice now in the last week with the same result both times. If needs be I'll reinstall it again, but hopefully somebody can help me.
It's a (dreaded I know) Broadcom Corporation BCM4318 [AirForce One 54g].

If there's any more info I can give I'd be glad to provide it.
Thanks in advance to all that reply.

---

### Post by kevdog on 2008-01-20
If you are using the bcm43 or b43 drivers for your card, then that's what you get.  Go for ndiswrapper.

---

### Post by portach king on 2008-01-20
Hey Kevdog,
I am using ndiswrapper.
The card worked fine until I reinstalled gutsy and the router is not the problm as other devices are having no trouble with the wireless.

---

### Post by kevdog on 2008-01-20
Did you go from 32 to 64 bit or any other changes with Gutsy?  Did you upgrade or clean install?  Can you find any other source for the winxp drivers?

---

### Post by steveneddy on 2008-01-20
> **portach king said:**
> Hey Kevdog,
I am using ndiswrapper.
The card worked fine until I reinstalled gutsy and the router is not the problm as other devices are having no trouble with the wireless.

I suppose that you were using ndiswrapper before the reinstall.

Did you reinstall ndiswrapper after the reinstall?

I know this sounds stupid, but we have to ask.

---

### Post by portach king on 2008-01-20
I used to have 32bit Gutsy, but  decided to do a clean install of 64-bit seeing as it is a AMD64 machine. I guess you could say that's when my trouble started. It's back to a 32-bit system at the moment. (Good ol' reliable, or so I hoped)

A clean install. Formatted the entire drive.

I've tried looking around the hp site, but without an luck with the drivers. I found a sp30038.exe file...
(I have a HP Pavilion zv6179EA btw. specs: [http://www.ciao.co.uk/HP_Pavilion_Zv6179EA__6268709](http://www.ciao.co.uk/HP_Pavilion_Zv6179EA__6268709))

Lol, yes I have installed ndiswrapper. I undstand why you have to ask though

---

### Post by kevdog on 2008-01-20
So I believe if you are going to use 64 bit -- you need a 64 bit windows xp driver.  I think this is the case.

---

### Post by portach king on 2008-01-20
> **kevdog said:**
> So I believe if you are going to use 64 bit -- you need a 64 bit windows xp driver.  I think this is the case.

I don't believe this was an issue last time, but regardless I am using a 32-bit version of Ubuntu.

---

### Post by kevdog on 2008-01-20
Ok great -- are you getting more than 3 feet wireless range with the 32-bit setup?

---

### Post by portach king on 2008-01-20
> **kevdog said:**
> Ok great -- are you getting more than 3 feet wireless range with the 32-bit setup?

No, I'm afraid not.

I think I may have confused things for you accidentally. I'll summarize my trouble again.

I have an AMD64 laptop

I used to run 32bit Gutsy with ndiswrapper and it worked fine.

I did a fresh install of 64 bit ubuntu last week. Could not get wireless to work.

Did another fresh install of 32bit Ubuntu after that, and have been having trouble since.

As a point of information, previously (ie. before last week) I wa able to see a list of the netwprks (neighbours etc) in a list when I clicked on the Network Manager applet. Now I only see my own.
I have tried Wicd and Wi-fi radar as well now.

---

### Post by kevdog on 2008-01-20
Can you provide the following:

lshw -C network
iwlist scan

---

### Post by portach king on 2008-01-20
Here it is

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:19:4a:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.51+Broadcom,03/23/2006, 4.40.1 ip=192.168.1.1 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:76:7d:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

```


iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CC:9A:43:44
                    ESSID:"eircom4644 6210"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0 
```

---

### Post by rosegarden78 on 2008-01-21
Just a theory but try setting your router frequency from 2.362 GHz to 2.464Ghz.  You'll need to access config probably by typing 192.168.2.1.  You know how higher frequencies seem to penetrate farther than lower frequencies when dealing with sound waves?  Good luck!

---

### Post by portach king on 2008-01-22
Hey rosegarden78,
As I said the problem isn't with the router as several other devices (including housemates laptops, a wii and  ds) are having no problems with the wifi at all. The problem began when I decided to do a clean install.
Thanks for your suggestion though.
Any help I can get is soothing the amount of frustration that this ongoing situation is causing.

---

### Post by kevdog on 2008-01-22
This is a hard one -- you have ipv6 disabled?

---

### Post by portach king on 2008-01-23
Yup, ipv6 is off.  I tried that too. It didn't make any difference.

OK, I just did a clean install of Feisty to see the problem manifests itself tere too, and it indeed does, which is odd as it worked perfectly under Feisty before...
Reinstalling Gutsy again now.

---

### Post by mozetti on 2008-01-23
Something I noticed in your output, but I'm not sure if this important or not since I have issues with the Broadcom 4318 WiFi card in my HP laptop, too, but what the heck.

Your output shows:```
product: BCM4318
```

and

```
configuration: broadcast=yes driver=ndiswrapper+bcmwl5
```


Is it possible you're using the wrong driver for the card?

---

### Post by portach king on 2008-01-23
Well if I am it's bizzare because that driver worked before. Perhaps someone here more knowledgable on drivers could let us know whether I'm using the correct one or not.
Out of curiousity Mozetti, what troubles are you having? Are the similar to mine, and what driver did you use?

---

### Post by portach king on 2008-01-24
I hate doing this but
.....
Bump

If anybody has any suggestions, I'd hugely appreciate it. :D

---

