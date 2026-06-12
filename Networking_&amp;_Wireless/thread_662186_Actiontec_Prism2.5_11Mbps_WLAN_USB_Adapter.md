---
title: "Actiontec Prism2.5 11Mbps WLAN USB Adapter"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by MystyxMac on 2008-01-08
Hi, I use Ubuntu 7.10 and i have problems with the Actiontec Prism2.5 11Mbps WLAN USB Adapter.

in [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb")  documentation is said that this card is supported and working out-of-the-box. Problem is it does not.

I also tried ndiswrapper and linux-wlan-ng. All without any succes. With ndiswrapper i even get a error in dmesg. See [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,1059/catid,2/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/id,1059/catid,2/")

Can someone help me with this?

---

### Post by MystyxMac on 2008-01-09
Ok, ie found my problem. I accidentally removed the prism2_usb driver. After installing it again, i can configure wireless networks again.

But it still does not work. I get to following information from

**ifconfig:**
> 
eth0      Link encap:Ethernet  HWaddr 00:11:43:6A:20:29 
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6a:2029/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1319  Metric:1
          RX packets:12750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4089985 (3.9 MB)  TX bytes:726184 (709.1 KB)
          Interrupt:7

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


**iwconfig:**
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.


**lshw -C network:**
> 
*-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:6a:20:29
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.5 latency=32 module=b44 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Why is my wlan0 DISABLED? How can I get it ENABLED?

---

