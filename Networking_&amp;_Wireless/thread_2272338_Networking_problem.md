---
title: "Networking problem"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by satimis on 2015-04-06
Hi all,

New Box
=======
CPU AMD FX-8320 (new)
Asus mobo M5A97 Le R2.0 (new)
RAM 8G DDR3 1333 (from old box)

HDD (in combination)
ADATA 120G (from old box) OS - Ubuntu 14.04
WD Black 1.5TB (from old box) - for installing VMs of VirtualBox

Remark:
All components from the old box, mentioned above, were working properly before without problem.  Old motherboard - Asus M4A97 Deluxe
[http://www.asus.com/Motherboards/M4A79_Deluxe/](http://www.asus.com/Motherboards/M4A79_Deluxe/)


Just completed building a new desktop PC.  As the ordered Transcend "SSD370 1TB 2.5" SATA 3" will be delivered after the Easter Holidays I plugged in the old SSD and HDD in combination for temporarily use.  At booting it popup;```

Waiting for network configuration
Watting up to 60 more seconds for network configuration ...

```


Then after bootup I changed /etc/network/interface```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

```

Rebooted PC.  Then it worked.


$ ifconfig -a```

br0       Link encap:Ethernet  HWaddr fe:6b:6c:f0:0d:90  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::fc6b:6cff:fef0:d90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:12685 (12.6 KB)

eth2      Link encap:Ethernet  HWaddr f0:79:59:65:34:78  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5128 (5.1 KB)  TX bytes:5128 (5.1 KB)

```


Then again I edited /etc/network/interface```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet manual

# add bridge ports
auto br0
iface br0 inet static 
	....
       	bridge_ports    eth2
	....

```

Rebooted PC then networking work.


Why Asus motherboard detects the onboard network as eth2 instead of eth0?

Is there any way to change it back to eth0?

Thanks

Regards
satimis

---

