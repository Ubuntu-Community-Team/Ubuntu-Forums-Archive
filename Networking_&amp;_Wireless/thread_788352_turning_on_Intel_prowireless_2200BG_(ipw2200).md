---
title: "turning on Intel pro/wireless 2200BG (ipw2200)"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Firebat451 on 2008-05-09
when I type, "sudo lshw -C network" here is what I get for my wireless network details:

> *network:1
description: Wireless interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 9
bus info: pci@0000:02:09.0
logical name: eth1
version: 05
serial: 00:12:f0:14:06:5c
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

That last part "radio off" makes me think that it's turned off, but I don't know how to turn it on.  I right clicked on network manager icon->options->enable wireless, but nothing changed.  I went to manual config, and it says eth1 is enabled, though when I disable it and try to re-enable it nothing happens.  I try to configure eth1 and if I try and change any of the options and then hit ok when I go back to the config for eth1 the options are back to what they were before.  Any ideas on how to make it say, "wireless=radio on"?

Also, I'm using Kubuntu 8.04

---

### Post by loserboy on 2008-05-09
[http://ubuntuforums.org/showthread.php?t=765319&highlight=Intel+pro%2Fwireless+2200BG+%28ipw2200%29](http://ubuntuforums.org/showthread.php?t=765319&highlight=Intel+pro%2Fwireless+2200BG+%28ipw2200%29)

any chance this could help?


people have been having lotsa wireless problems with 8.04, i'm pretty sure that card is listed as working under gutsy, so it's either something simple or a driver problem

---

### Post by Firebat451 on 2008-05-09
Wow, I feel so dumb.  I've been futzing around with different versions of ubuntu for a month now and I just had to hit Fn+F2.  Thanks alot.

---

### Post by loserboy on 2008-05-12
hehe no big deal, sometimes the hardest things to solve are the most obvious

---

