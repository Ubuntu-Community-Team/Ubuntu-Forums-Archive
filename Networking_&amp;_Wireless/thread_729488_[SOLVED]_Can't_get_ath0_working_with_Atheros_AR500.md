---
title: "[SOLVED] Can't get ath0 working with Atheros AR5006EG"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Quartz25 on 2008-03-19
Hello.  I just recently bought a Sony VAIO VGN-NR220E laptop, and I cannot for the life of me get the Wi-Fi to work.  The network manager does not even recognize that Wi-Fi is an option.  I then proceeded to Google and search all over these forums in search of an answer, but nothing seems to work.  After running "lshw -C network", to get this result:
```

  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:28:09:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=10.0.1.103 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

I also tried ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:1A:80:28:09:E2  
          inet addr:10.0.1.103  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:fe28:9e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1305640 (1.2 MB)  TX bytes:219309 (214.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I compiled MadWifi, installed it (ensuring to back up and remove the preinstalled copy), rebooted the machine and still the same results.  I'm running Ubuntu 7.10 Gutsy Gibbon, and Linux kernel "2.6.22-14-generic" (straight from uname -r).  Please help, I'm very confused. :confused:

Thanks in advance!

---

### Post by tigerguy on 2008-03-19
if you're laptop is running a broadcom mini card try using NimbleX2008 while you try and configure ubuntu. You do not have to install it; just run it in ram. This is if you need to be connected now.
Tigerguy

---

### Post by Quartz25 on 2008-03-19
It's not a broadcomm, it's an Atheros AR5006EG PCI card (just as it says in the output from lshw).

---

### Post by azwar on 2008-03-20
try to update & install build essential. then try to install the madwifi again. please get the latest ticket from madwifi [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

p/s =  i easily get disconnected when using madwifi driver. but since it support monitor mode, i still using it.
         anyway you can try to install NDISWRAPPER

---

### Post by Quartz25 on 2008-03-21
Excellent!  That worked!  I didn't even realize that the Ubuntu Hardware Information was getting the wrong chipset.  I'm currently submitting this reply with my laptop's Wi-Fi.  Thanks! :)

---

