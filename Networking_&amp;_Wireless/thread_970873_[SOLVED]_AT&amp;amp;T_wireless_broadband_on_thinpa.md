---
title: "[SOLVED] AT&amp;amp;T wireless broadband on thinpad T60"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by woodpusherghd on 2008-11-04
I have AT&T wireless broadband using Sierra Wireless minipci card 8765.  I can connect using GnomePPP but can't seem to get Network Manager to recognize the card in Intrepid.  Anyone get this card to work with Network Manager in a thinkpad?

---

### Post by woodpusherghd on 2008-11-26
Apparently, the Kernel doesn't recognized the sierra mini pci card as a modem. This was corrected by creating a modems.fdi file in /etc/hal/fdi/information. Additionally, I discovered that the modem was using the usb serial driver limiting it's download speed to about 430 kbs. I discovered the sierra driver source code incorrectly identified the card (MC8765) as product id 6803 instead of 6805. After editing the source code, compiling and installing, I can connect via Network Manager with download speeds of 1.5 Mbs.

---

### Post by pinoyboyf4i on 2009-04-15
woodpusherghd, can you please post your modems.fdi file.  I have a T60 with the same MC8765 card on 8.10 and I cannot get anything to work.  wvdial, kppp, pppd, umtsmon all connect but I cannot connect to any websites.  I downloaded the 1.6.0 version of the sierra drivers and corrected the sierra.c to reflect 6805 instead of 6803.

---

### Post by pinoyboyf4i on 2009-04-15
Never mind.  The info you posted lead me to this link:

[http://www.nabble.com/Sierra-Modem-Problem-td22447969.html]("http://www.nabble.com/Sierra-Modem-Problem-td22447969.html")

So I changed the /usr/share/hal/fdi/information/10freedesktop/10-modems.fdi file to reflect the Vendor Id 6805 instead of 6803. 

I also made sure the following two lines are in my /etc/modules file.
[INDENT]usbserial vendor=0x1199 product 0x6805
sierra[/INDENT]

Next, I added Right mouse click Network Manager applet --> Edit connections --> Mobile broadband tab --> Add --> Forward --> Select AT&T (Tethering with data acceleration) then click Forward --> Apply --> Close 

After a reboot, Network Manager recognizes the card as a Mobile Broadband card.  I checked off Enable Wireless then selected the AT&T Mobile Broadband profile and it connected.  Woo hoo!

At some point I'll reinstall 8.10 to see if the original sierra drivers work instead of downloading the sierra 1.6.0 drivers and changing sierra.c to reflect Product ID 6805 rather than 6803 for the Sierra MC8765 card.

Thanks woodpusherghd!

---

