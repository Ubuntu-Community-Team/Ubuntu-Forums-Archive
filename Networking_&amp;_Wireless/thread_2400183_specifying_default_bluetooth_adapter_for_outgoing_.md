---
title: "specifying default bluetooth adapter for outgoing connections"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by siliconjesus1 on 2018-09-03
Apologies in advance if this is a duplicate, but none of the other answers I have come across match. 

I have two bluetooth adapters that are both in use on a host, one built in (hci1), and one via usb dongle (hci0). I'm making RFCOMM connections out from the host, and the api I'm using (pybluez) to do that doesn't allow me to specify which adapter to use. I can force connections out of a specific adapter by downing the other one, but I need to use both radios at the same time. 

I'm hoping there is something I can do within Ubuntu to make the "default" adapter hci0?

Thanks in advance.

---

