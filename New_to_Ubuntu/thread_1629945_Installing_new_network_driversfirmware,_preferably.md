---
title: "Installing new network drivers/firmware, preferably terminal"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by KarlG on 2010-11-24
Greetings!

Well for a starters, when it comes to managing Linux environments I'm quite new. I love Ubuntu though. But since I work as a Windows-tech at an IT-department (with a lot of Unix/Linux servers) I figured I would try out getting a hang of the terminal system (bash).

Well here's what I would like to know.

I'm having trouble with my wifi-card and that made a question pop into my head. How in the name of the almighty do one install new hardware drivers on this thing. I would almost at any circumstance try to surf up the answers myself, but since my card (and this is on my home computer) screws me over all the time (disconnects) I'm having a hard time.

So to the point. If I would like to upgrade my network drivers, what should I do?

---

### Post by cariboo on 2010-11-24
Generally you can't update your network card drivers like you would in Windows. The drivers are included with the kernel, so you are always getting the latest stable drivers. It would help if you let us know what chipset your wireless driver uses. If you aren't sure, just open a terminal and type:

```
lspci | grep Network
```

the output should look something like this:

```
lspci | grep Network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

Once you have determined the chipset, you can type:

```
sudo lshw -C network
```

The above command will tell you if the device is detected properly and what driver is loaded:

```
lshw -C network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
cariboo@redstone-natty:~$ sudo lshw -C network
[sudo] password for cariboo: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:41:e4:2f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.246.2 ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
  
```

I removed the output for my wired connection, as it isn't relevant here. 

If you could post the output from the above to commands, it will go a long way in helping you sort out your wireless problems.

---

### Post by KarlG on 2010-11-24
Thanks for reading my post!
Here's the result of the commands:


```

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```



```
 *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:20:46:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=228.61.2.24 ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:df3fe000-df3fffff

```

---

