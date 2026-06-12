---
title: "Trying to get wireless working on my P2120 fujitsu laptop"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by ckblackm on 2007-07-12
I'm trying to get wireless working on my fujitsu p2120 laptop w/ xubuntu
 installed (feisty), and am running into some difficulty. iwconfig says
 wlan0 has no wireless extensions, and lshw shows wlan0 as being disabled.
 Any ideas on how to fix this?

 thanks,
 Christopher.

 ------
 root@ckblackm-laptop:/home/ckblackm# lsmod | grep prism
 prism2_pci             70784  0
 p80211                 31884  1 prism2_pci


 root@ckblackm-laptop:/home/ckblackm# iwconfig
 lo        no wireless extensions.

 eth0      no wireless extensions.

 wlan0     no wireless extensions.

         *-network:1 DISABLED
              description: Ethernet interface
              product: Prism 2.5 Wavelan chipset
              vendor: Intersil Corporation
              physical id: 12
              bus info: pci@00:12.0
              logical name: wlan0
              version: 01
              width: 32 bits
              clock: 33MHz
              capabilities: cap_list ethernet physical
              configuration: broadcast=yes driver=p80211_prism2_pci
 driverversion=0.2.5 latency=64 link=no multicast=yes resources:
 iomemory:e8017000-e8017fff irq:9

---

### Post by ckblackm on 2007-07-15
Here's some more information in case anyone has the time to help me:

ckblackm@ckblackm-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:00:C1:2B:4D  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:ff:fec1:2b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2227825 (2.1 MiB)  TX bytes:258169 (252.1 KiB)
          Interrupt:9 Base address:0x8800

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Memory:dfa0a000-dfa0b000

If I don't use the -a flag for ifconfig... wlan0 doesn't show up.

thanks,
Christopher.

---

### Post by MyR on 2007-07-15
by any chance is there a button or key combination you need to press to turn on your wireless?

if that isn't the problem, can you post the output of
```
lspci -v | less
```
peace

---

### Post by ckblackm on 2007-07-15
I'm assuming you just want the wireless part...

00:12.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Fujitsu Limited. Unknown device 1169
        Flags: medium devsel, IRQ 9
        Memory at e8017000 (32-bit, prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

---

### Post by MyR on 2007-07-15
here's ubuntu's community documentation for the card:
[https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan?highlight=%28WifiDocs%2FDevice%29)

heres a thread based of your card. it looks promising:
[http://ubuntuforums.org/showthread.php?t=446010](http://ubuntuforums.org/showthread.php?t=446010)

here it is at launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63989)

peace

---

### Post by ckblackm on 2007-07-16
That seems to have gotten it... I'm now connected wirelessly.  Thanks a mil!

---

