---
title: "Losing around 30% of bandwidth on wireless with new ADSL router"
date: 2017-02-03
forum: Networking &amp; Wireless
---

### Post by mc-rpg on 2017-02-03
I'm using a new wireless router (TP-LINK TD-W8960N) now and everything works fine but for some reason I'm losing close to 30% of bandwidth in ubuntu 14.04 on my laptop (Dell Inspiron 14z n411z) when I'm connected to that router's wireless. I actually thought it was a configuration issue and tweaked almost any router setting I knew of before realizing it was actually an ubuntu-only issue. Windows gets the full speed on speedtest as well as all the androids (weirdly) and iOS devices. I'm the only one connected to said wireless and no process was using the network when I performed the tests and the results have been very consistent for days now. It's worth noting that I have largely no networking issues on this laptop so it seems there is something particular to this router's chipset that it's not sitting entirely right with ubuntu.

This is my wireless chipset:

```
id:	
network
description: 	Wireless interface
product: 	Centrino Wireless-N 1030 [Rainbow Peak] [8086:8A]
vendor: 	Intel Corporation [8086]
physical id: 	
0
bus info: 	
pci@0000:02:00.0
logical name: 	
wlan0
version: 	34
serial: 	ea:e7:ea:7c:22:e3
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	iwlwifi
driverversion	=	3.13.0-107-generic
firmware	=	18.168.6.1
ip	=	10.0.0.40
latency	=	0
link	=	yes
multicast	=	yes
wireless	=	IEEE 802.11bg
resources:	
irq	:	47
memory	:	d0600000-d0601fff
```

And the kernel I'm on right now: Linux 3.13.0-107-generic x86_64

Any help would be appreciated.

---

### Post by TheFu on 2017-02-03
Well, what speeds are you seeing?
and
What speeds are you expecting to see?

BTW, google found this: [https://ubuntuforums.org/showthread.php?t=2268355](https://ubuntuforums.org/showthread.php?t=2268355)

---

### Post by mc-rpg on 2017-02-03
> **TheFu said:**
> Well, what speeds are you seeing?
and
What speeds are you expecting to see?

BTW, google found this: [https://ubuntuforums.org/showthread.php?t=2268355](https://ubuntuforums.org/showthread.php?t=2268355)

Thanks! Setting 11n_disable=8 on my /etc/modprobe.d/iwlwifi.conf file seems to have solved the issue. I'll test more thoroughly throughout the week.

---

