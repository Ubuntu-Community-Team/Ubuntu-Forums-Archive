---
title: "lost wireless connection after update"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by bamboojj on 2009-05-17
Hi all,I am complete new to Ubuntu,I lost wireless connection after the last update. here is my comp information:

Code:

uname -a
Linux jojoju-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux


Here is my network info after typing: 'sudo lshw -C network":

jojoju@jojoju-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:72:72:c0
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:e9:7d:77:24:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jojoju@jojoju-laptop:~$ 


Can anyone help me on this issue? I will much appreciate if you can. Thanks so much!

---

### Post by lkraemer on 2009-05-18
With the Atheros AR242x, you need to do a make after downloading
a new kernel.

This might be of help:
[http://ubuntuforums.org/showthread.php?t=1142199](http://ubuntuforums.org/showthread.php?t=1142199)

I'd suggest you check to see if newer drivers are available, and download
them if there are updates.  Then follow the directions on the link, assuming you are using the MadWifi Drivers.

REMEMBER: You can select the PREVIOUS Kernel from the Grub Boot menu
when booting, and your Wifi will be fully functional, so you can download the updates.

Every time in the future that you download a new Kernel, you will have
to repeat the make process.

Good Luck.

lkraemer

---

