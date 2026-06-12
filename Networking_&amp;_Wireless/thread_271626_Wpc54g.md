---
title: "Wpc54g"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by mayben on 2006-10-04
I am using a custom build laptop with a linksys wireless G pcmcia adapter (model # WPC54G). I cant connect to any wireless network. I went to the getting started forums first and read all the docs on how to connect to wireless networks and howto troubleshoot wifi. None of which helped.

I checked device manager and lshw and the device and driver showed up fine.

Under network settings I deactivated my ethernet and made the only default gateway my wireless connection.

Under properties of my card I enabled the connection put in my ssid and chose DHCP for configuration.

Yet after activating I still cant connect to the web and when I go back under network settings my wireless card is set BACK to not active status.

In terminal under iwconfig it lists everything correctly except my frequency is off and my AP is "invalid".

When I attempt to change the channel or frequency I get this error.

"SET failed on device eth1 ; Operation not permitted."

My wireless device worked last night right before I installed Ubuntu.
I am new to linux so I am now out of idea's on how to fix this. Any ideas anyone?



So I tried ndiswrapper. Still no go. It still gets deactivated in networking. So I tried a different version of the card (I currently have v1 I I used a brand new v3) it still didn't work. I then tried a USB wireless adapter (netgear w111 g v2 I think) and still same problem....Any idea's anyone?

---

### Post by montguy on 2006-10-19
> **mayben said:**
> 
When I attempt to change the channel or frequency I get this error.

"SET failed on device eth1 ; Operation not permitted."



Did you use sudo?

---

