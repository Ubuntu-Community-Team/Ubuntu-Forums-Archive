---
title: "Need to cycle on/off wifi to make it work"
date: 2019-05-10
forum: Networking &amp; Wireless
---

### Post by underfire81 on 2019-05-10
Hello everyone!  

Since upgrading to 19.04 from 18.04 I've had difficulty maintaining a consistent wifi connection.  It will disconnect without warning and will not reconnect, at all.  I was bummed about having to go back to Windows because of this issue, but then I doubled down and decided to troubleshoot it myself since nothing I researched worked. 

I tried to fix it the following ways:

[LIST]
[*]killing the powersaving on the card
[*]running sudo service network-manager restart
[*]checked for proprietary drivers (there were none)
[/LIST]

None of these worked.  

What does work as a _temporary solution_ is opening Settings and cycling the wifi off and on again.  I would like to be solved on a more permanent basis, which is why I'm here. 

See below for my wireless card information: 
[FONT=courier new]
description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 64:6e:69:8a:3d:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.0.0-13-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=10.10.41.86 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:130 memory:c1000000-c11fffff[/FONT]

Thank you!

---

### Post by jeremy31 on 2019-05-10
See the wireless script link in my signature and post results

---

### Post by underfire81 on 2019-05-10
[http://paste.ubuntu.com/p/5ZchWdGYKY/plain/](http://paste.ubuntu.com/p/5ZchWdGYKY/plain/)

I couldn't get the text to post here, but the link above has everything.

---

