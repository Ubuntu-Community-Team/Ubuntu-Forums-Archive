---
title: "Wireless Connection Problem - Laptop &amp; Xubuntu"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Doug11987 on 2008-08-28
Hi. I have just started using Xubuntu (with Live CD to try it out) on my laptop. It currently shows all the wireless networks around and lets me enter the WEP key, but then cannot connect. 

There are several options for entering the key - WEP 128, WEP 64/128ASCII, WEP 64 HEX & LEAP. I guess I should be using the first as it is the only one to let me enter the complete key.

Is this a known problem and there a (easy) solution? I know theres no problem with the network as it works fine with my laptop on XP.

Thanks, Doug.

PS: It's version 7.04 or something - definitely 7, don't know for sure as I'm now at work!

---

### Post by Crafty Kisses on 2008-08-28
Post results of:
```
lshw -C network
```

---

### Post by Doug11987 on 2008-08-28
Codename, 

Where do I put that Command in (this is my first time with anyhting other than windows...)???

I will post it when I get home,

Thanks!

---

### Post by Doug11987 on 2008-08-28
> **Codename said:**
> Post results of:
```
lshw -C network
```

Here are the results, it displayed a load for the wired connection but I can't use that so have skipped it out:

Description: Wireless Interface
Product: PRO/Wireless 3945ABG network connection
Vendor: Intel Corporation
Physical ID: 0
Bus Info: pci @ 0000:05:00.0
Logical Name: eth1
Version: 2
Serial: 00:13:02:7d:d1:50
Width: 32 bits
Clock: 33mhz
Capabilties: bus_master cap_list ethernet physical wireless
Configuration: broadcast=yes drive=ipw3945 driver version=1.2.2    mp.ubuntu1 firmware= 14.2.1:0 () latency=0 module=ipw3945     multicast=yes wireless=unassociated


The version I am using is 7.10 and currently have XP on my computer.

On a side note it's a bit sluggish, I am assuming thats because its on CD at the mo, and if I dual boot it will be fine (my laptop runs XP fine and is Centrino Duo 1.6Ghz, 1Gb Ram)

Thanks in advance, Doug.

---

