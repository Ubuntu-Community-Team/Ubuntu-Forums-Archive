---
title: "Need help with Netgear WG111v2 USB (and LiveBox) Kubuntu Feisty"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2007-08-18
I bought this device for my laptop three weeks ago but have had no joy getting it to work.
It's recognised by the OS when I plug it in, and appears correctly in *lsusb*. When I run KWirelessManager the interface is recognised and a list of local wireless networks appears. I've tried every possible combination of DNS/manual configs to try and communicate with my router (a LiveBox from ISP Orange) but have never managed to connect.

I turned off all security on the router. I previously managed to connect to this same router from another laptop using the PCMCIA version of this card.

Can anyone please help with this? Would I be better off trying to install ndiswrapper, even though the device seems to be recognised OK?

---

### Post by Staff on 2007-08-27
NOTE: I GOT IT WORKING USING DAPPER DRAKE.


i installed ndiswrapper ( by running Synaptic Package whilst my ubuntu install disc was in ) and then followed the instructions from 

[http://ubuntuforums.org/showtread.php?t=329229](http://ubuntuforums.org/showtread.php?t=329229) 

i got netgear working using the same usb pen. if you then run networking ( from system - administration ) and select the wireless network and click properties. if you select 'netgear'from the netowrk name, press OK then you should be connected to the internet OK. at least i was using dapper drake.

---

