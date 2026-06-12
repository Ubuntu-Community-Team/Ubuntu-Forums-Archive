---
title: "PRO/Wireless 3945ABG stopped working"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by andersondk on 2008-07-31
I have a Dell Latitude D830 laptop with a PRO/Wireless 3945ABG wireless card.  It has been working great for 3 months.  I rebooted and now it no longer is recognized by the system.  (Does not show up in /sbin/ifconfig etc.)

From the output of lshw -C network, it seems that the card is recoginzed by the kernel and the driver is loaded, but no device name has been assigned.

I have tried removing the module (modprobe -r iwl3945) and reloading it (modprobe -a iwl3945) but to no avail.

I have tried booting up to previous kernels (2.4.24-16 thru 2.4.24.19) and that has also not worked.

I have put the iso install disk back in and booted up to that, but the card is still not recognized.

I have replace the card.

I am now out of ideas.

Any suggestions would be greatly appreciated.


Thanks

Doug


Details:

uname -a
Linux andersondk 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux


sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ab:69:1c
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feab:691c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14136992 (13.4 MB)  TX bytes:2438988 (2.3 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2600 (2.5 KB)  TX bytes:2600 (2.5 KB)



sudo lspci -v
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 218
        Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Legacy Endpoint IRQ 0


sudo lspci -n | grep 0c:00.0
0c:00.0 0280: 8086:4222 (rev 02)


sudo lshw -C network
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ab:69:1c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5755m-v3.29 ip=192.168.0.103 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

sudo lsmod | grep iwl3945
iwl3945                89844  0
iwlwifi_mac80211      219108  1 iwl3945

sudo modprobe -l | grep iwl3945
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko

---

### Post by chili555 on 2008-07-31
How about letting us see:```
sudo cat /var/log/messages | grep switch
```Thanks.

---

