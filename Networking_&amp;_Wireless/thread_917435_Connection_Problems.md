---
title: "Connection Problems"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Xonara on 2008-09-11
Hi. I've been using a linksys adapters and they've been giving me trouble for a while, I'm having a hard time figuring it out. On windows, using the linksys wireless config utility wouldn't let me connect, it would always say connecting. When I tried the xp config utility, it worked fine. However, sometimes the connection would still drop. Alot of the time, actually. Using 'repair connection' seemed to work.

On Ubuntu, the connection still drops alot. The nm applet still says it's getting a signal from the router, but it can't connect for some reason. Disabling networking and the re-enabling it doesn't help like 'repair connection,' and then I don't get any signal. Ubuntu will basically refuse to reconnect unless I reboot or unplug the router and then plug it back in. Even worse, unplugging the router and plugging it back in seems to aggravate some kind of nasty bug which makes the nm applet icon disappear until I reboot. The process is still running though, and killing it and then restarting the app doesn't seem to do anything. Also, I got a new adapter and I kept getting the same problems.

I'm not sure what information you need, but I'll list a few things.

Ubuntu Variant:Hardy
Network Adapter: Linksys Wireless A/G
Driver: prism54usb
Average Signal/Bars: 54%/2 (Doubt that helps >_>)


HALP :(

---

### Post by Xonara on 2008-09-11
bump

---

### Post by Dfenceking on 2008-09-12
i am also have alot of the same problems.........


DFK

---

### Post by RedPandaFox on 2008-09-12
> **Xonara said:**
> Hi. I've been using a linksys adapters and they've been giving me trouble for a while, I'm having a hard time figuring it out. On windows, using the linksys wireless config utility wouldn't let me connect, it would always say connecting. When I tried the xp config utility, it worked fine. However, sometimes the connection would still drop. Alot of the time, actually. Using 'repair connection' seemed to work.

On Ubuntu, the connection still drops alot. The nm applet still says it's getting a signal from the router, but it can't connect for some reason. Disabling networking and the re-enabling it doesn't help like 'repair connection,' and then I don't get any signal. Ubuntu will basically refuse to reconnect unless I reboot or unplug the router and then plug it back in. Even worse, unplugging the router and plugging it back in seems to aggravate some kind of nasty bug which makes the nm applet icon disappear until I reboot. The process is still running though, and killing it and then restarting the app doesn't seem to do anything. Also, I got a new adapter and I kept getting the same problems.

I'm not sure what information you need, but I'll list a few things.

Ubuntu Variant:Hardy
Network Adapter: Linksys Wireless A/G
Driver: prism54usb
Average Signal/Bars: 54%/2 (Doubt that helps >_>)


HALP :(

Do you live under a tin/aluminum roof?

---

### Post by Crafty Kisses on 2008-09-12
I'd like to see the results of this command:
```
lshw -C network
```

---

### Post by Xonara on 2008-09-12
When I entered this command: sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:87:ae:88:f2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:92:50:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.103 multicast=yes wireless=IEEE 802.11g
user@USERS-COMPUTER:~$

---

### Post by Xonara on 2008-09-13
> **RedPandaFox said:**
> Do you live under a tin/aluminum roof?

Erm... Not as far as I know. It's a trailer roof with some waterproof sheeting over wood with some insulation under that, I think. It does seem to work better near windows though :/

---

