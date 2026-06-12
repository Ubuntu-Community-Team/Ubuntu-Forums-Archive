---
title: "Netgear WG111v2 wireless dongle &amp; Hardy"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by emperorming on 2008-05-17
I upgraded from Gutsy to Hardy to find my wireless no longer worked after a reboot. I'm now back to Gutsy. I'm using a Netgear WG111v2 wireless dongle using the RTL8187 driver in ndswrapper with WEP.  I've blacklisted the driver & all seems to be well apart from occasional crap outs & I have to reboot to bring the network back.  My question is, how do I get the wireless to work if I upgrade to Hardy again? I'd prefer to continue using the WG111 if I can.  All suggestions pitched at a non-technical person extremely welcomed!!

---

### Post by mcgarry83 on 2008-06-02
Im having a problem with this adapter too. It worked out of the box with Hardy (no ndiswrapper or anything), however the connection works for a little while then drops. It still shows I am connected and even displays the signal strength, but I have no internet. I tried installing ndiswrapper like I used to use and had some problems getting it to work. Wifi radar doesnt seem to work with it now either. Its just acting very strange. The only way to fix it when it drops for me is to unplug the adapter wait about 30 secs and then plug it back in.

---

### Post by yoho on 2008-08-07
Hi, I'm also having problems with this adapter on Hardy (have tried using wifi-radar and wicd but no luck...). For me, the connection worked but very slow, in fact according to wifi-radar I'm connected using wireless-b protocol, so only getting 1-2Mbps. Also couldn't access hotspots other than my home network.

The solution I've had to live with is to roll back to Gutsy using ndiswrapper (unless someone has worked out a way around it on Hardy?)...

Just wanted to share my experiences to see what other methods others have tried :-)

---

