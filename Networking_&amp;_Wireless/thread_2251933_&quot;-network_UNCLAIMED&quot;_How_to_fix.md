---
title: "&quot;*-network UNCLAIMED&quot; How to fix?"
date: 2014-11-07
forum: Networking &amp; Wireless
---

### Post by ENunn on 2014-11-07
Hello.

I cannot use wifi. I got to use it an hour ago, but know I can't connect to any network.

Here is what I get when I type lshw -C network.

This is the best I can do because I'm typing this on my iPad.

Anyways, here goes.

*-network
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:01:00.0
         logical name: eth0
         version: 05
         serial: 00:9c:02:8c:40:d7
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_ list ethernet physical tp mil 10bt 10bt-fd 1
00bt 100bt- fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversio
n=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multic
ast=yes port=MII speed=10Mbit/s
         resources: irq:40 ioport:4000(size=256) memory:90404000-90404fff memory:9
0400000-90403fff
*-network UNCLAIMED
         description: Network controller
         product: RTL8118CE 802.11b/g/n WiFi Adapter
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:02:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: latency=0
         resources: ioport:3000(size=256) memory:92500000-92503fff

Man, that took a long time to type. Hope I didn't have any spelling errors. :)
Any fix for this please?

---

### Post by Bucky Ball on 2014-11-07
Can you get online with a cable and do an update? Reboot and see if that fixes. If not ...

Make sure your cable is unplugged and boot. The cable will be used as default and will effectively switch off your wireless, but by the looks of your output, this is not the issue. Failing that ...

Try running the commands in the solution in post #5 [HERE]("http://ubuntuforums.org/showthread.php?t=2238559&p=13094943&viewfull=1#post13094943"). Be aware that this will install wicd in place of Network Manager, so if that is an issue, don't go there. Network Manager can be re-installed if this doesn't work, though.

---

### Post by ENunn on 2014-11-07
> **Bucky Ball said:**
> Can you get online with a cable and do an update?
Nope. I have no cables. I always use my neoghbor's WiFi on my laptop or my iPad because we have no internet at our house.

I don't know what to do. I went to the Realtek website to download drivers but it keeps redirecting me. Let me try to download using another distro if the wifi works and I'll get back at you.

---

### Post by chili555 on 2014-11-07
Before you go too much further, let's see:```
lspci -nn | grep 0280
uname -r
```Thanks.

---

### Post by Bucky Ball on 2014-11-07
What chili said ...

---

