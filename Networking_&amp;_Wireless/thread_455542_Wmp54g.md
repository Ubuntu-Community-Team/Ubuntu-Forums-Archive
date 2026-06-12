---
title: "Wmp54g"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by doctorzizmore on 2007-05-26
Hi I'm pretty new to Linux and i'm trying to get my wireless card to work (WMP54G from Linksys).  I just installed Feisty Fawn.  It seems to recognize that i have a card and it sees the networks in the area.  I think it is accepting the password and it says that the connection strength is 84%.  However when I open up firefox it can't connect to the internet. 

I've been looking through the forum and I've found some information but I'm very confused.  I know this model card has a couple differnt chipsets that all require different drivers.  Can someone please walk me though troubleshooting this?  Please assume I know nothing about linux.

---

### Post by newhope16 on 2007-05-26
same thing has happened to me. two hours and no reply...

---

### Post by dmizer on 2007-05-26
you are correct, it will help to know the chipset of your card.  you can find this by looking at the output of:
```
lspci
```
it should look something like this:
```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 USB Controller: NEC Corporation USB (rev 43)
00:0a.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
00:0c.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
00:0e.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: Texas Instruments [COLOR="Red"]ACX 111[/COLOR] 54Mbps Wireless Interface
```
where "ACX 111" is the chipset for my wireless card (emphasis mine).

---

### Post by doctorzizmore on 2007-05-28
it says:

00:08.0 Network Controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by MeeMaw on 2007-05-29
Have you tried this post?

[http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61)

I have a Linksys WMP54g (rt61 chipset) and it's the one I used.....
:)

---

