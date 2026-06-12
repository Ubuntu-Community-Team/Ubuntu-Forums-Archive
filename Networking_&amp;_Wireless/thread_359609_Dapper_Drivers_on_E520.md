---
title: "Dapper Drivers on E520"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by rob_909 on 2007-02-12
When installing Ubuntu 6.06 on the new dell E520, many of the drivers are not present....including the ethernet, so I basically cannot do anything. Some say that a kernel update will get all the drivers I have missing, but I can't get on the internet to do that. 

lspci:

0000:00:00.0 Host bridge: Intel Corporation: Unknown device 29a0 (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 29a1 (rev 02)
0000:00:19.0 Ethernet controller: Intel Corporation: Unknown device 104c (rev 02 )
0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 02)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 02)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 02)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2812 (rev 02)
0000:00:1f.2 RAID bus controller: Intel Corporation: Unknown device 2822 (rev 02 )
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d1 (rev a1)
0000:03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem

How do I get the ethernet controller.........ifconfig has no eth0 or ethernet at all. I need the Intel Pro 10/100 Ethernet Network Card driver I believe.....where can I find it? How do I install it after transfering it over from another computer?

And if that all goes well.......I can worry about the other 10,000 missing drivers and kernel updates.

---

### Post by rob_909 on 2007-02-12
Forgot to mention.........82562V is the network card model
[http://downloadfinder.intel.com/scri...9&submit=Go%21](http://downloadfinder.intel.com/scri...9&submit=Go%21) has some drivers for it....

Is this my problem, or is there a source package that I need to get?

---

