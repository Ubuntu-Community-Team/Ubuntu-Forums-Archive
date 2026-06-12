---
title: "Wireless keeps turning off at startup"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by GatorV on 2008-08-29
Hey everyone, I'm having a issue since the last month hehe, my wireless keeps turning off whenever I login to gnome. When I turn on my computer, whe arriving to the GDM I see the wireless led on, then if I login to KDE, the wireless is on, but if I login to gnome the wireless turns off, I think it's my profile but I don't know where to look exactly for this.

Does any one know where can I look?

Thanks in Advance

---

### Post by Crafty Kisses on 2008-08-30
Post the results of this command:
```
lshw -C network
```

---

### Post by GatorV on 2008-08-30
Here is the output:
```

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:27:1a:9c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 01
       serial: 00:0f:b0:fe:bc:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

I forgot to say that the only way to turn it on is by issuing this command:
```

sudo modprobe -r iwl3945
sudo modprobe iwl3945

```

I have to switch Wlan on and off twice and enter that commands six times for wlan to come on...

I think there is a setting or something at my startup that's getting the wlan off..

---

