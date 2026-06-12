---
title: "ASUS WL-107G: Making it work"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by kameneye on 2007-03-06
After struggling with my Linksys WPC54G for weeks on end, I decided to buy an ASUS WL-107G wireless card because of it's cheap price, the fact that it says "Linux Support!" on the box, and many (ubuntu, SuSE, take your pick) users that claim that it works "out of the box".  Mine doesn't.  Well, "Linux Support" couldn't be all that bad right? Wrong.  Instead of instructions in the manual, (oh hell no, that's valuable space for Windoze users) it tells me to look on the CD for many different README files that instruct me to compile and download (with no instruction as to where to start) and a plethora of other things that makes this Linux n00b angry and PRIFO. I even tried downgrading, (from Edgy to Dapper, because thats one of the solutions I've read) but no.  Still no wireless.

Can someone who knows what they're doing help me here?
How do I compile the driver, or am I doing it wrong?

Thanks for any and all help.

---

### Post by magicfab on 2007-03-06
What Ubuntu version(s) did you try ? Did you try Feisty Herd 5 ?

---

### Post by tjod on 2007-03-08
> **magicfab said:**
> What Ubuntu version(s) did you try ? Did you try Feisty Herd 5 ?

I'll join in the "me too" queue here. In similar position for similar reasons. "Works out of the box" is a bit of an exaggeration. 8-) I'm using Ubuntu 6.10 on an Acer TM 2480. 

I'm a n00b as well, and looking forward to any assistance that might be available.:) 

Thanks!

Tim O

---

### Post by AklBlue on 2007-03-30
> **magicfab said:**
> What Ubuntu version(s) did you try ? Did you try Feisty Herd 5 ?

I'm currently trying Herd 5, the card appears to work, and using Network manager can detect wireless networks, but it will never actually connect.

Further, it will not connect to an unsecured WLAN, or one using WEP.  WEP is the only opion, there is no WPA.  I have also tried creating a static connection, but still no luck.

Any help would be appreciated.

---

### Post by ravemjr on 2007-04-06
My card aparantly works with Edgy, but since the only network I need it for is WPA enabled, I never got around to test it...but as soon as I connect it, the network manager finds it...

---

### Post by rhombus on 2007-05-09
Here's a "me-too" post.

I'm using Ubuntu Feisty 7.04 and I have a WPA protected network. The card works fine in WinXP. Ubuntu actually detects the card and my network but when I try to connect, it never actually goes through. It does pop up with a dialog asking for a 128-bit wireless WEP key but says nothing about WPA (and entering my passphrase into that dialog does nothing).

I've even tried connecting to an unsecured network in my neighborhood as a test and that did a fat lot of nothing.

I'm sort of new to linux but I can use the command line as long as there are clear directions on how and why I would configure something. I'd rather use the GUI if possible but hey...

Any help would be appreciated.

Thanks.

---

### Post by rhombus on 2007-05-22
So...Anyone got any ideas? Fabian?

This card connects to neither a WPA protected network nor a completely unprotected network. I need it do do both to keep using Feisty on this laptop. Everything else on this box works fine. I actually switched from a broadcom chipped card to this Asus card because it seemed to have linux drivers available but it sure isn't working so...I'm using Win XP for wireless right now and I don't particularly want to do that.

Any help would be greatly appreciated.

-e

---

### Post by jaunbanaun on 2007-07-25
I'd just like to say that I'm experiencing the same problem after setting up WPA2 with hostapd on my FreeBSD server. Ubuntu 7 with my Asus WL-107G looks only compatible with WEP.

Is there a solution for this out there? :confused:

---

### Post by kevdog on 2007-07-25
Im not sure the problems you had with your linksys card since Ive just taken two users through an installation process via ndiswrapper with success, but onto the asus card.  The first step to the solution is to find the chipset of the card you are working with.

If this is PCI based card please type and cut and paste output of:
lspci -nn

If USB
lsusb

For both, please post
lshw -C network

Thanks, Im sure there is a solution (although it might take some steps!).  I laugh everytime I hear "works out of the box" -- if it works half the time, you're lucky!

---

### Post by jaunbanaun on 2007-07-25
> **kevdog said:**
> Im not sure the problems you had with your linksys card since Ive just taken two users through an installation process via ndiswrapper with success, but onto the asus card.  The first step to the solution is to find the chipset of the card you are working with.

If this is PCI based card please type and cut and paste output of:
lspci -nn

If USB
lsusb

For both, please post
lshw -C network

Thanks, Im sure there is a solution (although it might take some steps!).  I laugh everytime I hear "works out of the box" -- if it works half the time, you're lucky!

It's a PC Card on a Compaq Evo n410c. It works if using a open wifi.
```
ak@ak-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
02:02.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:02.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:02.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)
02:03.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:04.0 Ethernet controller [0200]: Intel Corporation 82557/8/9 [Ethernet Pro 100] [8086:1229] (rev 09)
02:04.1 Serial controller [0700]: Agere Systems LT WinModem [11c1:045c]
03:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
```

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth0
       version: 09
       serial: 00:d0:59:94:84:48
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.0.253 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:40200000-40200fff ioport:2000-203f iomemory:40000000-4001ffff irq:5
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 3
       bus info: pci@03:00.0
       logical name: ra0
       version: 01
       serial: 00:17:31:37:61:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:38000000-38001fff irq:11

```

---

### Post by kevdog on 2007-07-25
Ok you are using a ra based card.  Did you install drivers or compile the serial monkey drivers??

---

### Post by jaunbanaun on 2007-07-25
> **kevdog said:**
> Ok you are using a ra based card.  Did you install drivers or compile the serial monkey drivers??
Heh, I just read the other posts about the problem. I haven't done anything. Have been working fine until today when WPA was enabled. I guess I could try some of the solutions I've read about.

---

### Post by kevdog on 2007-07-25
I think ra based cards work best in Feisty if you compile and install the serial monkey drivers.  This wasnt a problem in Edgy or earlier distros.  Supposedly some of the problems people are having with their ra cards in Feisty are to be fixed with Gusty.  ra drivers dont use wpa supplicant -- so many of the configurations statements need to be done manually in the /etc/network/interfaces file using the iwpriv statements.

---

### Post by brecke on 2007-09-03
err... so what exactly is the answer here? is there a solution or are left hoping gusty fixes it? would it help to compile the serial monkey drivers? would WPA work afterwards?

thanks in advance.

---

### Post by rhombus on 2007-12-17
> **brecke said:**
> err... so what exactly is the answer here? is there a solution or are left hoping gusty fixes it? would it help to compile the serial monkey drivers? would WPA work afterwards?

thanks in advance.

Seems to work fine in Gutsy (I also had problems in Feisty). I haven't tried connecting to a WPA network yet, but it does recognise WPA networks as being WPA (and not as WEP 128 bit as it used to for some reason) so I'm fairly confident it will work.

---

