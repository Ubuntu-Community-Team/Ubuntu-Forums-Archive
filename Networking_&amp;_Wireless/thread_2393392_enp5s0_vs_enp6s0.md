---
title: "enp5s0 vs enp6s0"
date: 2018-06-02
forum: Networking &amp; Wireless
---

### Post by poorguy on 2018-06-02
Hello Everyone,

I discovered on the back of a ***Dell Optiplex XE Desktop*** that I have ***2 Ethernet inputs***.

When I go into my ***Network Manager*** I see I'm connected to **enp5s0**

My other choice which shows ***Off ***and ***Unplugged*** is labeled [B]enp6s0


 [/B]What is the difference and does it matter which I use.
I googled it but as always way over the knowledge I have.

I just need a simple answer that a regular user can understand.


Thanks


```

@Dell-OptiPlex-XE:~$ inxi -Fxz
System:    Host: Dell-OptiPlex-XE Kernel: 4.15.0-22-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Dell product: OptiPlex XE serial: N/A
           Mobo: Dell model: 0TNXNR v: A01 serial: N/A BIOS: Dell v: A05 date: 01/09/2013
CPU:       Dual core Intel Core2 Duo E7400 (-MCP-) arch: Penryn rev.10 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11172
           clock speeds: max: 2800 MHz 1: 1596 MHz 2: 1596 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1152x864@75.00hz
           OpenGL: renderer: Mesa DRI Intel Q45/Q43 version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel 82801JD/DO (ICH10 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic
Network:   Card-1: Broadcom Limited NetLink BCM57780 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 05:00.0
           IF: enp5s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Broadcom Limited NetXtreme BCM5761 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 06:00.0
           IF: enp6s0 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (2.8% used)
           ID-1: /dev/sda model: ST3320418AS size: 320.1GB
Partition: ID-1: / size: 293G used: 8.3G (3%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 185 Uptime: 32 min Memory: 1266.6/7876.4MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
@Dell-OptiPlex-XE:~$ 

```

---

### Post by Irihapeti on 2018-06-02
It would partly depend on what you are using the machine for, and if there are any major differences in the specs of the two cards.

E.g. if you need high-speed internet (say for gaming) and one nic is a lot faster than the other, then use the faster nic. Otherwise, it probably doesn't make any difference.

That's my low-tech answer, anyway. :)

---

### Post by poorguy on 2018-06-02
Hey Irihapeti,


That's a good enough answer that I can understand.

As best I can figure is on adapter is for ***super high speed internet*** and the other adapter is for [I][B]standard regular speed internet .

[/B][/I]Both of these are integrated adapters.

First I've ever seen as this.

It's working great so I'll leave it connected as I have it now.

I'll keep searching and see what I can find.


Thanks ;)

---

