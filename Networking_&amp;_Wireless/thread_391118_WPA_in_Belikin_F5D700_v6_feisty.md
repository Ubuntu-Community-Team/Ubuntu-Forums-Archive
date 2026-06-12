---
title: "WPA in Belikin F5D700 v6 feisty"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Dunattar on 2007-03-22
Hello,

I've just installed feisty (alpha5) and I have a Wifi PCI Card (belkin f5d7000 v6)... the installation has detected the card correctly. It can detect my AP, but I can't connect to my AP because I have my wifi encripted with WPA, and when I try to connect to my AP in the password option I can't see WPA, only WEP... (128 or 64)

How can i solve that?

Thanks in advance

---

### Post by Dunattar on 2007-03-23
Nobody can help me?

---

### Post by GozzoMan on 2007-04-21
Hi, I have exactly the same issue with the final release of Feisty (but with a USB Belkin WiFi adapter).

Have you been able to solve?

Thank you,

---

### Post by ThomasMarkas on 2007-04-22
I have similar problems. I have one Belkin PCI card, two different USB sticks and a PCMCIA card.

The Belkin PCMCIA works straight out the box on my laptop, but Feisty only shows WEP available on the new network gadget. So have disabled the wireless and defined it  myself.

But, the PCI and USB's only seem to work with WEP out the box. The new interface widget support WEP for them and also WEP when defined manually. But do not appear to support WAP.

To define WAP from the Belkin PCMCIA I defined the netowrk connection in /etc/network/interfaces

# PCMCIA 
 auto ra0
 iface ra0 inet dhcp

# pre-up iwconfig ra0 essid "RouterName"
 pre-up iwconfig ra0 mode managed
 pre-up iwpriv ra0 set Channel=4
 pre-up iwpriv ra0 set AuthMode=WPAPSK
 pre-up iwpriv ra0 set EncrypType=TKIP
 pre-up iwpriv ra0 set WPAPSK="1ce5d3168c9517ee75cc7a12da22ec2a1234834b9f30eed573000a13fbdd9b26"
 pre-up iwpriv ra0 set TxRate=0

The WPAPSK is generated using wpa_passphrase 'ssis' 'password'. The single quotes seem important.

Whatever, cannot seem to get WAP working from the new interface gadget for most of my Belkin's. It may be of some use, but I notice that cards that come up "ra0" seem to support WAP and those coming up "rausb0" do not.

So for now I am using wondering 100m Ethernet cables and Belkin USB 10/100 Ethernet Adapters F56050 which work straight out the box.

---

### Post by ThomasMarkas on 2008-02-20
Have recently upgraded to Ubuntu 7.10 (Gutsy Gibbon). The Belkin PCMCIA wifi used here works straight out the box including WPA.

However, a new addition to my cards  a Belkin Wireless G F5D7010 Ver 7000uk did not. I have posted my solution for this in 7.10 here [http://ubuntuforums.org/showthread.php?t=702823](http://ubuntuforums.org/showthread.php?t=702823)

Amazing, one release I have to configure by hand and then next it works straight out the box.:)

---

