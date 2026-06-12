---
title: "How to configure wireless..."
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by Euphoric Invasion on 2006-12-21
Hey,

I am not sure if this needs to be in the begginer's section, so parden me if this sounds a bit.... dumb.

I recently got a generic wireless card (the kind that sits on the motherboard, not a USB dongle)  and I don't even know if it recognized it.  I got it to work with win98se, so I know the card is good.  How do I get Edgy to work with it?  I did all I know (which is not alot) with the network thing on the system menu, but it doesn't give me much options.  Can anyone help me?  I HAVE to have internet on this computer and it HAS to work with this card (its not my computer, I am just fixing it and I figured, since they don't care, Ubuntu would be better than win any day), but if I can't get it to work, I'm gonna have to go to windows :-?    I REALLY don't want to if I don't have to :'(  So I need help to get it working.  I got everything else working, except the wireless :( ](*,) 

Thank you in advance (for all those who help and all those who try)

EI

---

### Post by bernied on 2006-12-21
In a terminal, type
```
lspci
```and look for a line that might describe your wireless card (that's a PCI card, by the way)
Post the line here - copy/paste

then try googling what looks like the model number, with the words ubuntu and howto, so for me:
```
bernie@kubulaptop:~$ lspci
...snip...
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```I would google 'ubuntu wireless intel 2200BG howto'

But, be careful how you apply the results. Because I just found this:
[http://ubuntuforums.org/archive/index.php/t-13576.html](http://ubuntuforums.org/archive/index.php/t-13576.html)

And, if you didn't read that carefully you might just launch into the instructions, which in this case are totally unnecessary because that howto is for a very old version of ubuntu (warty warthog). But that howto could at least tell me which driver I needed - in my case its ipw2200.

So then, I'd google 'ubuntu ipw2200 howto'

But mine is not a good example, because this driver was included in ubuntu so worked out of the box.

So, find out which driver you need, and see what you can do

---

### Post by Euphoric Invasion on 2006-12-22
Thanks, unfortunatly I have to do this at two different places.  The computer I'm working on is at my place, and I cant get the internet working there... so I have to alternate between 2 places.  I'll get you the information as fast as I can.

Thanks again.

---

### Post by Euphoric Invasion on 2006-12-23
Hey,
I did the *lspci* and this is what I remembered:
It is Texas Instruments. (OEM)
it is an IEEE card
Ubuntu does recognize it. so thats good.
I had to do static IP b/c when I did *ifconfig* it did not show me an IP address on the wireless. When I did static IP it showed the IP, but still no Internet.
I'll get the exact information from it once I go back to my place and copy the information (by hand )

Thank you very much for your help.

-EI

---

### Post by Euphoric Invasion on 2006-12-24
Ok, I saved it on a diskette, and here it is....

$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
00:0d.0 Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem
00:0d.1 Computer telephony device: Broadcom Corporation BCM4212 v.90 56k modem
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

Thank youfor helping.

-EI

---

