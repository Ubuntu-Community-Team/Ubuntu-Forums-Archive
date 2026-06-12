---
title: "network UNCLAIMED"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by Aprop on 2015-12-17
Hello, 
I recently installed a fresh copy of Ubuntu 14.04.3 LTS 64 bit on my laptop(Lenovo g50). 

I'm trying to start up the wi-fi but I don't know how.

When I run the lshw -C network command I get this:

description: Network controller
product: Broadcom Corporation
Vender: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 02
width: 64 bits
clock: 33Mhz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:f0c00000-f0c07fff memory:f08000000-fobfffff

What do I need to do to get this working? 
Any help is appreciated.
Thank you.

---

### Post by slickymaster on 2015-12-17
*Moved to ***Networking & Wireless*** sub-forum*

Hi Aprop, welcome to the forums. Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Aprop on 2015-12-17
[code]########## wireless info START ##########

---

### Post by deepakdeshp on 2015-12-17
Please see if this helps

[http://forums.linuxmint.com/viewtopic.php?f=53&t=208499&sid=16bba303c35fcfb7dcdac9dff1eda549](http://forums.linuxmint.com/viewtopic.php?f=53&t=208499&sid=16bba303c35fcfb7dcdac9dff1eda549)

---

### Post by Aprop on 2015-12-18
Thanks but thats not going to work.

---

### Post by Aprop on 2015-12-18
Something happened when I loaded up the drivers from the gui. I'm going to erase everything and start over. Any further problems and I'll re-post. Thank you everyone.

---

