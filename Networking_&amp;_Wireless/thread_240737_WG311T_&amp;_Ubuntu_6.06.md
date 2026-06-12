---
title: "WG311T &amp; Ubuntu 6.06"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by showty on 2006-08-21
I am a total Linux newb.. but here goes.
I tried it a while back (Fedora Core 4) and couldnt get my wireless to work, so I left it for a bit.. today I tried again and installed Ubuntu with no hassles, it even detected my Netgear WG311T card, because I can connect to my wireless network! Seems that Ubuntu includes MadWifi because the WG311T is an Atheros based card.

But, unfortunately, the internet connection and general wireless connection is very crappy. It works for about 10 minutes, then just stops working for another 2 or so.. it is extremerly frustrating..

What else can I try? Should I use Synaptics to install ndis wrapper? What will ndis wrapper do?

---

### Post by lupine_nickt on 2006-08-21
The Atheros drivers are generally very good; you might just have a bad signal, wherever you are? 

If you can give the results of 'iwconfig ath0 |grep Link' (replace ath0 if it's incorrect), that'll tell you what your general signal quality is. Also, if you can ping your gateway a thousand times (ping -i 0.2 -c 1000 <gatewayip>) -- <gatewayip> is usually something like 192.168.0.1, and can be found by running route -n and looking under the 'Gateway' column, for the row which has 0.0.0.0 under the Destination column. Do that when your internet is working well, and when it's not. 

High packet loss (rather than just, say, really high ping) would suggest interference rather than driver problems; low link quality would back that assumption up.

Try switching channels (if there are no other wifi networks nearby, channel 11 or 13 is likely to be the least polluted) - sudo iwconfig ath0 channel 11 and see if you can increase the transmit power: sudo iwconfig ath0 txpower 100mW, IIRC.

xF,

...Nick

---

### Post by showty on 2006-08-21
bleh.. It automatically updated last night (new kernel + restricted modules and stuff) and now I cant get the wireless to work at all..
](*,)  dammit I am desperate to use linux..

---

### Post by showty on 2006-08-22
Ok got it working again, still get the dropouts..

My signal strength is around 75%, and its not a lack of signal, I get uninteruppted internet on Windows..

I havent installed anything custom/whatever, so can someone explain to me what it is using to work sometimes (madwifi.. ndis-wrapper whatever..) and explain to me what each does? I need to solve this or Ubuntu is rather useless to me without net..

---

### Post by lupine_nickt on 2006-08-22
It is probably using the native linux driver (midwifi) - you can check this by running lsmod from a terminal... if you see modules with ath_ (e.g. ath_pci), then you're using madwifi; a module called ndiswrapper would be, well, ndiswrapper ;).

Whichever one you're using, you could try downloading the latest version and installing it manually [www.madwifi.org](www.madwifi.org) ; [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

Since you can get good reception in Windows, it is probably the driver, so an update is the most likely way to get it working (the versions of madwifi and ndiswrapper included in Ubuntu are fairly old)...

xF,

...Nick

---

