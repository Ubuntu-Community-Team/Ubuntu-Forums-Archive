---
title: "[SOLVED] Intel 2915 Wireless Card in Hardy Heron"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by jojohippo on 2008-04-24
Hi I'm not very good with linux so please be nice. I've been using Fedora 8 without any wireless problems and I just installed Ubuntu 8.04 but I'm not able to get my intel 2915 wireless card working.

I followed some of the instructions here on the [Ubuntu Wireless Troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") 

The LSHW Command gives me this: 
```
joe@joe-laptop:~$ sudo lshw -C network
SCSI                      
  *-network        
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:39:e1:c8
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:5f:b1:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
```

The LSMOD command gives me this 
```

ipw2200               146120  0 
ieee80211              35528  1 ipw2200
```

And the IWCONFIG command gives me this 

```
joe@joe-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm kinda lost with all the documentation and forums and I dont' know what to do next or how to read this information... can someone point me in the right direction?

---

### Post by jojohippo on 2008-04-25
bump

---

### Post by ciphex on 2008-04-26
you might try installing the fwcutter firmware package.
it gives support for some broadcom chipsets, intel uses many of these in it's wifi implementations.

use Synaptic Package Manager to search for and install fwcutter.

---

### Post by chili555 on 2008-04-26
> eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          etc.Looks like it's working just fine, to me. Before you try anything else, can you click the Network Manager icon at the upper right, the one that sort of look like two computers trying to communicate, select your ESSID, supply any encryption details and connect?

Your details I quoted look like a healthy card standing tall, waiting for instructions.

---

### Post by jojohippo on 2008-11-03
It turns out for me it wasn't a driver issue at all. The problem was an irq conflict. To fix it, I had to edit /boot/grub/menu.lst and add pci=noacpi to the end of kernel line.

---

