---
title: "Internet in Windows, no internet in Ubuntu"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by miniKOX on 2015-09-03
Hello.

I have got such a problem. I have got a machine, with dual-boot(Windows 7 and Ubuntu) with Atheros AR5B95 wireless card.

In both systems wireless card connects to network, the problem is, that in Windows 7 browser connects with internet, but in Ubuntu even ping is not working, I can't even access to a router site("gate"), though I am connected to wireless network.

I have got no idea how to deal with it, so I am asking for help, maybe someone else had similar problem.

---

### Post by TheFu on 2015-09-03
Can you ping the router by LAN IP?

---

### Post by miniKOX on 2015-09-04
When I ping a router it gives me response: 
```

5 packets transmitted, 0 received, 100% packet loss
``` 
it's not pinging, I do not know why, but the machine is connected to network.

---

### Post by TheFu on 2015-09-04
Please post the exact command used with output. This saves time.
Please include the ping by IP and output from **sudo lshw -C network** and **route**

Thanks for the code tags. Those help.

---

### Post by miniKOX on 2015-09-04
Hello.

From **ping **:
```

ping 192.168.0.1 -I wlan0 -c 5
PING 192.168.0.1 (192.168.0.1) from 192.168.0.107 wlan0: 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4030ms

```

From ** sudo lshw -C network **
```

*-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 88:ae:1d:09:65:ae
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:53000000-5303ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:88:55:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.107 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:52000000-5200ffff


```

From **route**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0


```

---

### Post by miniKOX on 2015-09-04
Hello.

From **ping **:
```

ping 192.168.0.1 -I wlan0 -c 5
PING 192.168.0.1 (192.168.0.1) from 192.168.0.107 wlan0: 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4030ms

```

From ** sudo lshw -C network **
```

*-network               
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 88:ae:1d:09:65:ae
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:53000000-5303ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:88:55:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.107 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:52000000-5200ffff


```

From **route**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0


```

I don't know if it has a sense - it sounds silly, but when my second computer(with Windows8) is ON, the internet start to work, and works fine. May it be something with this?

---

### Post by TheFu on 2015-09-04
What does **ping 192.168.0.1**  return? Do not specify the interface, but have the wired connection unplugged for at least 20 sec before.

The wifi chip involved has a long history of issues with Linux, but I thought those were sorted a few years ago.
Are you using network manager or wicd or doing the management manually?

As to whether a different computer, connecting over wifi, can make this work ... perhaps. It may force the wifi router/AP into a mode that is supported by the card in this laptop.  There are ways to disable hardware encryption - saw a few of those as solutions for this specific wifi chip over at askubuntu.  I've been having issues with ubuntuforums this afternoon, so wanted to post this ASAP.  No other issues with any other websites, however.

[https://askubuntu.com/questions/479229/14-04-ar9k-wireless-driver-reclaim](https://askubuntu.com/questions/479229/14-04-ar9k-wireless-driver-reclaim)

---

### Post by miniKOX on 2015-09-05
I do not have wire connection even plugged, all goes by wireless card(-I  wlan0 - just to be sure i specified it) and the **ping** gives as I  showed:

```

PING 192.168.0.1 (192.168.0.1) from 192.168.0.107 wlan0: 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4030ms

```

But since I used the solution that You gave in link:
```


echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

sudo modprobe -rfv ath9k

sudo modprobe -v ath9k

```

The internet started to work normally. Now works fine, thank You very much for your help and time :D. I am just curious what miracle has happen, that the internet did not wanted to work before, only worked with second computer ON, and why now works fine?

---

### Post by TheFu on 2015-09-05
You changed the options for the driver - disabled hardware encryption in the card. I suppose there is a bug in the Linux driver for that, so forcing the software driver to handle encryption is best. The modprobe commands removed the driver, then reloaded it.  The manpage for modprobe provides more details.

I specifically wanted to see the normal ping to determine if there was odd routing happening. When someone does the ping like you did, that usually means they've got some strange networking and might have ignored the routing. That is why I asked for a normal ping.

Some of this stuff is just a guess. Having more facts CAN help.  I would have liked to see the exact command used inside the code tags too, but that is just me.

Anyways - if this is solved, please mark it so in the thread tools to help others.

---

### Post by miniKOX on 2015-09-05
For **ping** I used a command:
```
 sudo ping 192.168.0.1 -I wlan0
```
Am I pinging bad way? In Windows it is enough to write 
```
 ping domain or ad.d.r.ess 
```
Not in Linux?
As internet started to work, also **ping** a long way to USA to Google works fine, returning some "ttl...(something)" or something like that, but I can not exactly say You what it is, because I do not have an access to this machine now.

---

### Post by TheFu on 2015-09-05
ping doesn't need sudo. Learn when and why to use sudo sooner than later.

ping doesn't need an interface specified. THAT was the issue I had.  Just wanted 
```
ping 192.168.0.1
``` - nothing else. Why make it harder when it isn't needed?

Don't know much about windows anymore. I'm a pure end-user there, though I did write windows programs in C/C++ for about a decade. Was also writing for Unix and Linux and BSD systems.  On windows, I feel so very limited. The OS just doesn't like developers in the way that all Unix systems do.  I'm down to 3 things for Windows these days - everything else is done on Linux/BSD.

But the question remains ... is this issue solved or not? If so, please mark this thread SOLVED using the thread tools.

---

