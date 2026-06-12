---
title: "ASUS USB 2.0 Wireless Network Adapter"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by ________ on 2008-11-24
I've been testing the LiveCD of Ubuntu 8.10 Desktop Edition. For a very long time now, I've been wanting to install Ubuntu on this computer, and every single time I try it's this wireless adapter that never is enabled. I believe I have been trying, regularly, since 6.06. I have done some posting on the forums, I have read a some threads, some documentation, but replies have ever been scarce. (Should I bump my own thread in such situations, or is such activity frowned upon?)

No matter. The network adapter (ASUS USB 2.0 Wireless Network Adapter) isn't enabled. How would I go about correcting this? Do I need to provide more information?

---

### Post by mikewhatever on 2008-11-24
Yes, post the outputs of the following commands:
**sudo lshw -C network**
**ifconfig**
**iwconfig**

---

### Post by gnusci on 2008-11-24
Could you please read the sticky and provide more infromation:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by ________ on 2008-12-08
I read the sticky. My adapter (WL-160G) is not supported.

The output from the aforementioned commands follows:

sudo lshw -C network
  *-network
      description: Ethernet interface
      product: RTL-8139/8139C/8139C+
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: c
      bus info: pci@0000:02:0c.0
      logical name: eth0
      version: 10
      serial: 00:11:09:48:d0:3b
      size: 10MB/s
      width: 32 bits
      clock: 33MHz
      capabilities: pm bus_master cap_list ethernet physical tp mii 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes   driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
      description: Ethernet interface
      physical id: 1
      logical name: pan0
      serial: fe:00:44:ca:c7:87
      capabilities: ethernet physical
      configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


ifconfig
eth0       Link encap:Ethernet  HWaddr 00:11:009:48:d0:3b
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:23 Base address:0xc800
lo         Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:222 errors:0 dropped:0 overruns:0 frame:0
           TX packets:222 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
           RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)



iwconfig
lo         no wireless extensions.

eth0       no wireless extensions.

pan0       no wireless extensions.

---

### Post by postafflatus on 2009-04-17
I have the same wireless adapter, I really need to make that thing to work, isn't there anywhere any drivers or software to force that adapter to work? Ive tried WINE to install driver and assigned software from the CD which came with the device, but upon launch the program just crashes... Please anyone, HELP.

---

### Post by leSasch on 2009-07-04
... listening (not able to use WL-160G in Ubuntu 9.04 64bit) ...

*sudo lshw -C network* doesn't show the adapter.

---

