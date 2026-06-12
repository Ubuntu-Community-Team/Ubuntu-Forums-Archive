---
title: "Problems with WG111v2, getting connected but no IP"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by johlin on 2008-05-11
I have recently tried getting a WG111(v2) working on my sister's computer on which I installed Ubuntu. I have tried reformatting a dozen times with slightly different strategies afterwards. The card did not work out of the box so I blacklisted the driver and installed ndiswrapper (with a wired connection) and set it up with the latest Windows driver for the card. The card did light up from time to time and with wpasupplicant I even got it to connect with WPA2. The problem is however that I do not get an IP. I can see the PC as connected in my router (Linksys WRT54G with Tomato) but without an IP number. The outcome was the same if I tried without encryption.
I did try activating DHCP or setting a static IP but it made no difference.
I did in a few cases see an IP number in network information or whatever that dialog was called. It was however way different from the 192.168.1.x-numbers I usually get. I couldn't ping anything when this happened either though.

Have you gotten your WG111 to work with some special tricks? I followed a few tutorials but they didn't work for me.

If I run iwscan or similar, I can see my network in the list of networks, don't know if that helps.

---

### Post by rm00re on 2008-05-12
i got mine working but it can't connect to any secure network (Wep), probable an easy fix but I was so happy to get it working I haven't tried anything. I installed ndiswrapper from the live cd and then pretty much fallowed this
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/)

I used the graphic interface, which made things easer. you said you're using the latest drivers. try the windows 98 from this release. That's what I used.
[http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)

---

