---
title: "WLAN Performence is very poor wir rt2500PCI"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Bigben77 on 2008-11-14
Hello Everybody,

I'm new to Ubuntu ! I Installed the 8.10 on my Dell Optiplex 745 including the WLAN Nic Driver (rt2500PCI). The Adapter works an connects to the Access Point but the throughput is very low (22kb/s). 

I got the System Dualboot installed with Vista(:(), on Vista the average throughput is about ~1100 kb/s. 

I think, it must depend on the adapter configuration ...

sudo lshw -C network says:

 *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: wmaster0
       version: 01
       serial: 00:0c:f6:10:38:2c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.128.50 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11

I'd be glad if anyone could help me !

Thanks in advance,

Benjamin

---

### Post by pietermansz on 2008-11-15
Same here with me ; connection info states 1 Mb/s (should be 54Mb/s) but when monitoring it is about 150 b/s.

pieter@dellaptop:~$ lsmod |grep rt2
rt2500pci                        24064  0 
rt2x00pci                        15104  1 rt2500pci
rt2x00lib                        36224  2 rt2500pci,rt2x00pci
rfkill                           17176  1 rt2x00lib
led_class                        12164  1 rt2x00lib
mac80211                         216820  2 rt2x00pci,rt2x00lib
cfg80211                         32392  2 rt2x00lib,mac80211
eeprom_93cx6                     10240  1 rt2500pci


any ideas?

---

### Post by bmullan on 2008-11-15
I have a diff card but was having same problem until I turned off IPv6

Click help in Ubuntu
type in IPV6

there is one entry listed that tells you how to turn it off.

see if that makes a difference.

I'm not sure why IPv6 is on by default in Ubuntu anyway as there are practically no Service Providers offering it yet.

---

### Post by bgenc on 2008-11-15
here is my lshw -C network output and I have the exact same problem. The wireless performance in XP is amazing. In Ubuntu, it is at most 50kb/s. Most of the time much less. The signal quality is 1/2 of what I get in XP.

  *-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: wmaster0
       version: 01
       serial: 00:09:f3:71:f1:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt2500pci ip=192.168.2.2 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11bg

---

### Post by Bigben77 on 2008-11-16
Hello ! Thanks for the hint turning off ipv6, but it diddn´t work out ... 

Benjamin

---

### Post by jnorthr on 2008-11-16
crazy idea, but for what it's worth: any chance there are other devices in your machine's area that may interfere with reception, say like a microwave, or T.V. ? Try to relocate your machine to see if reception improves.  :(

---

### Post by pietermansz on 2008-11-30
Problem is solved here

[http://ubuntuforums.org/showthread.php?t=766724&highlight=rt2500&page=2]("http://ubuntuforums.org/showthread.php?t=766724&highlight=rt2500&page=2") Shivans solution worked for me.

A little disadvantage though is that you have to do this every time you install an updated kernel.

But finally link and speed are ok !!

---

