---
title: "Using a router  with a jetpack with Ubuntu 14.04"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by sequimbob on 2015-09-02
I am not sure I am in the right forum.  If not please point me towards the right one. I live full time in an motor home.  I am presently running a HP Pavilion g7-2069wm Notebook PC, 6gb ram, Ubuntu 14.04.  I connect to the internet through my Verizion MIFI4510 wireless jetpack or sometimes through wireless in campgrounds. I want to setup a wireless network in my motor home with a wireless security camera, a printer and another ubuntu computer.  I have been told that I need a router to do this.  Usually routers connect to a modem with a cable but I would rather  connect the router to the internet wirelessly, if possible.  Can this be done and how? Does this require a special type of router? If so what type? I am new to networking so I might be asking some dumb sounding questions. Any help would be greatly appreciated. Thanks.

---

### Post by sandyd on 2015-09-02
Since you already have a laptop, you can simply add a compatible wireless adaptor (USB?) to create a new wireless network from your computer.
See [https://help.ubuntu.com/lts/ubuntu-help/net-wireless-adhoc.html](https://help.ubuntu.com/lts/ubuntu-help/net-wireless-adhoc.html) for instructions on how to create a new wireless network from your computer.

If the network settings does not do it automatically (It's been a long time since i've ever tried this), you will either need to
a) Setup a DHCP Server and configure NAT
b) Bridge both wireless adaptors so that DHCP on the new wireless network can pass onto the wireless network you are connected to.

---

### Post by sequimbob on 2015-09-04
Can you have two wireless adapters on one computer? I already have a built in wireless but can't connect anything other than the jetpack to it at the same time.  If I can use two adapters that will work fine.  Thanks. I'll give it a try.

---

### Post by sandyd on 2015-09-04
Yes, you can have two wireless adaptors.

---

### Post by jeremy31 on 2015-09-04
I think your Jetpack should work without a router for at least using the printer as my US Cellular hotspot works for connecting my laptop to my printer that is connected to the hotspot

---

### Post by sandyd on 2015-09-04
I didn't suggest connecting everything to the Jetpack because the OP mentioned that he sometimes connected to different networks. That would require that the Wifi security camera and the recording device be on the same network (i.e. the public wifi)

I didn't think he would want his security camera traffic passing through there which is why I simply reccomended using the laptop. Then, you only need to change the wifi connection on one device (the laptop) when wanting to connect to a different network, and the security camera traffic stays on his network.

---

### Post by sequimbob on 2015-09-04
Thanks for all the replies.  I bought a usb wireless adapter, plugged it in and got everything going.  Works like a charm.  Thanks again

---

