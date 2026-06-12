---
title: "Broadcom 4311 with ndiswrapper problem"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by MattPurland on 2007-05-07
Hi,

I know there's a lot of threads about this driver, but I couldn't find my exact problem. I have a Compaq F500 which has the 4311 chip. Basically, I've got the latest version of NDISWrapper installed and the driver installed fine. But when I run iwconfig the wlan0 doesn't show up at all, even though ndiswrapper is running and installed fine with the correct driver.

I'm running Ubuntu 7.04 with ndiswrapper 1.43

Any ideas?

Thanks

---

### Post by dbott67 on 2007-05-07
Can you post the output of the following commands:
```
scpl@dns2:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
scpl@dns2:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.128.59  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
scpl@dns2:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
scpl@dns2:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.128.59 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
scpl@dns2:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1

```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
cat /etc/iftab > iftab.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by MattPurland on 2007-05-07
Thanks for your help, somehow i got it working! Not sure how, but it is :) Thanks!

---

