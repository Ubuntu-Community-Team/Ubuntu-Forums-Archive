---
title: "Disabled wireless card"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by jheaton5 on 2008-10-05
Here is the system info
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:46:c9:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

How do I enable the device?

---

### Post by jmbargar on 2008-10-05
Please, give more information about your problem and post the iwconfig and ifconfig output.

---

### Post by jheaton5 on 2008-10-05
joel@joels-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joel@joels-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:67:18:57  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe67:1857/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3173369 (3.0 MB)  TX bytes:514749 (502.6 KB)
          Interrupt:218 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85000 (83.0 KB)  TX bytes:85000 (83.0 KB)

joel@joels-laptop:~$ 

For the rest of the story see the thread "Native Wireless Driver" in this forum.  I could not get any help with that thread so I decided to post a thread with a new name.

Thanks for responding.

---

### Post by jheaton5 on 2008-10-05
after some tinkering with iwconfig I get these results:

joel@joels-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joel@joels-laptop:~$

---

### Post by jheaton5 on 2008-10-06
bump

---

### Post by kevdog on 2008-10-06
I'm going to guess its a driver related problem.  I'm not familar with the iwlagn driver.  Can you find anymore info on this driver?

---

### Post by jmbargar on 2008-10-06
Is possible that your problem was related with the module that manage your wireless card. If you have the Windows driver, you can try to install it using ndiswrapper. If it works, you will know where was the problem in order to search a free driver if exist. Here is the project page:

[http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/")

and here is a HowTo in order to use it:

[http://ubuntuforums.org/showthread.php?p=40016]("http://ubuntuforums.org/showthread.php?p=40016")

Good luck!

---

### Post by jheaton5 on 2008-10-06
Thanks, I didn't relate the episode with ndiswrapper.  I used the tutorial you mentioned.  It didn't work either.  I think I may have the wrong firmware downloaded or perhaps I'm supposed to do something to install or compile the ucode?

What's frustrating is that I get 130Mbps in Vista.

---

### Post by jheaton5 on 2008-10-07
kevdog,

I got the driver off of the Intel/linux site [here]("http://www.intellinuxwireless.org/"). I followed the link to the iwlwifi project and from there to the compat-wireless project for kernels 2.6.24 and up.  That page takes you to [this site]("http://linuxwireless.org/en/users/Drivers/iwl4965") where I downloaded the driver and the firmware.

joel@joels-laptop:~$ uname -a
Linux joels-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
joel@joels-laptop:~$

---

### Post by jheaton5 on 2008-10-07
Going back to Windows for the time being.  I'll try again with a fresh install of 8.10 when the stable version is released.

---

### Post by jheaton5 on 2008-10-07
4.10 Intel PRO/Wireless 4965AGN draft-802.11n (Centrino)
Driver status : 	Experimental
Driver name : 	iwl4965.o
Version : 	0.1.3
Where : 	[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)
[http://intellinuxwireless.org/?p=mac80211](http://intellinuxwireless.org/?p=mac80211)
Maintainer : 	James P. Ketrenos <ipw2100-admin@linux.intel.com>
Zhu Yi <yi.zhu@intel.com>
Mailing list : 	[https://lists.sourceforge.net/lists/listinfo/ipw3945-devel](https://lists.sourceforge.net/lists/listinfo/ipw3945-devel)
Documentation : 	Readme
Configuration : 	Wireless Extensions
Statistics : 	Wireless Extensions
Modes : 	Managed, Ad-Hoc
Security : 	WEP, 802.1x, WPA
Scanning : 	Wireless Extensions
Monitor : 	Yes
Multi-devices : 	?
Interoperability : 	802.11b, 802.11g, 802.11a depending on hardware
Other features : 	Firmware loading via HotPlug, 802.11e (QoS)
Non implemented : 	-
Bugs : 	?
License : 	GPL
Vendor web page : 	[http://www.intel.com/](http://www.intel.com/)
4.10.1 The device
The Intel PRO/Wireless 4965 is the fourth 802.11 product designed by Intel, following the previous PRO/Wireless 3945 product (section 4.8 ). It mostly adds support for draft-802.11n support, i.e. MIMO.

MIMO uses multiple antennas to simultaneously transmit or receive signal, and using some clever processing can achieve much greater range or speed than regular transmissions. The 802.11n standard is not yet finalised, which is why those products are called draft-802.11n compliant. It offer bitrate up to 300 Mb/s (most users won't see that in practice), and may double the range indoors.

Like their previous chipset, the 4965 is only available as a MiniPCI card for Intel Centrino processor, integrated in various laptops, and not available as a separate add-on card.
4.10.2 The driver
For the 4965, Intel decided to directly based their driver on the new mac80211 kernel stack (see section 4.9). This driver is part of the iwlwifi package, and currently requires a version of mac80211 with Intel changes to support draft-802.11n. This driver also require a specific firmware the ensure regulation compliance.

---

