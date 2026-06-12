---
title: "Airlink 101 AWLL2036 zd1211rw Gutsy"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by sceo on 2007-12-02
I got an Airlink 101 cuz I heard they worked pretty well out of the box on Ubuntu.  My bcm43xx wasn't working too well with ndiswrapper or without (same behavior as I will describe with this card), so I bought this Airlink USB.

The card is recognized as being plugged in (lsusb shows a Zydas), vendor # is 0ace:1215.  When I run iwlist scanning (as superuser) then it displays all kinds of wonderful information (about my channel, the MAC addr of my access point, my broadcasted ssid, everything).  nm-applet shows the network and a very strong signal, and when I click it it asks me for my WPA personal key.  I enter the correct key, and nm-applet icon starts the spinning motion.  It goes for a long time (the tooltip says something like 'waiting for network key from <mynetwork>'), then just stops and there's no connection.

It seems so close, and ironically - this is the same behavior that my broadcom was exhibiting when I tried that one.  This is a fresh install of Gutsy on a brand new drive.  I intend to install Gutsy from bare, get wireless working, then take care of everything else.  What's getting in the way of it connecting?

I tried switching from WPA, to WEP, to no encryption.  Same behavior every time.  Would LOVE some thinking on this!  I made a commitment to rid myself of Micro$oft and so this brand new SATA drive is itching for some Free Software - but can't download any!  

I have an ipw3945 in my Dell Laptop which connects to this network with WPA no problem.

Thanks in advance for any help or suggestions, Community!  :)

---

