---
title: "Native Wireless Driver"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by jheaton5 on 2008-09-28
When I installed ubuntu Hardy 8.04 on my laptop I could not activate my wireless card(Intel® Wireless WiFi Link 4965AGN).  I downloaded a driver from Intel.  I later found out that I had the wireless switch turned off. duh.  When I turned the switch on, I then had a wireless connection.  Well, as it turns out I do not have  an 'N' connection.  Must have the wrong driver.  According to the Intell/Linux website, since Kernel 2.6.24 (mine is 2.6.24-19-generic) the right driver is integrated into the kernel.  How can I uninstall the downloaded driver and use the integrated driver?:confused:

---

### Post by jheaton5 on 2008-09-28
Here is what the system is reporting:

lshw -C network 
*-network               
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
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.100 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
---------------------------
iconfig
wlan0     Link encap:Ethernet  HWaddr 00:13:e8:46:c9:75  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe46:c975/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1435854 (1.3 MB)  TX bytes:331399 (323.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-46-C9-75-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---------------------------

lshw only reports wmaster0
ifconfig reports wlan0 and wmaster0 but only wlan0 has traffic

is this normal or is there a conflict? :confused:

---

### Post by digitalvectorz on 2008-09-28
did you try System > Hardware Drivers?   If there's a new one installed and enabled, maybe try to uncheck it (to disable it) and restart?  (if it doesn't work you can always enable it again).

---

### Post by digitalvectorz on 2008-09-28
Actually, I re-read that.  You said that you're wireless card is Intel® Wireless WiFi Link 4965AGN

> 
When I installed ubuntu Hardy 8.04 on my laptop I could not activate my wireless card(Intel® Wireless WiFi Link 4965AGN).


Well if you're card is 4965AGN, then you do have 'N' compatability - you just probably don't have 'N' capability on your router (I would think.)  

But also, it says you're using the iwl4965 driver - that is the default driver that the kernel would be using for your card, anyways, i do believe.

---

### Post by jheaton5 on 2008-09-28
Systems > Hardware Drivers does not show this driver.  There is a note about third party drivers being present but not supported.

thanks anyway

I booted up under Windows Vista and checked the settings there.  I'm getting through put at 130 mbps there and only 54 mbps here.

---

### Post by digitalvectorz on 2008-09-28
I may have misinterpreted you.  Are you saying that you don't have the 'N' connection with the current driver (that you SHOULD be getting?) or are you saying that your card doesn't support the 'N' connection?

If i was under the wrong impression (that your card doesn't support the 'N' connection) my apologies, i'll dig up some more.

---

### Post by digitalvectorz on 2008-09-28
You may want to try looking to see if the old driver (whatever it was the documentation said the default was) is blacklisted in /etc/modprobe.d/blacklist

and or

try blacklisting the driver you installed to prevent the newly installed drivers from loading, forcing the system to use it's default?

worth a shot.

---

### Post by jheaton5 on 2008-10-05
Old driver is blacklisted
Router is Linksys WRT160N
New Linux driver installed from  [compat-wireless project]("http://linuxwireless.org/en/users/Download"), following the instructons on that page.  Wireless still did not work.  I downloaded and installed the firmware for this driver.  Nothing.  I used modprobe -f and now can see the driver in Hardware Drivers.  The driver is checked but not used.  if I disable and re-enable the driver it shows in use.  Network manager then will show a wireless network.  I still cannot connect to the network.

System now reports:
joel@joels-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
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
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:67:18:57
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
joel@joels-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:67:18:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78700 (76.8 KB)  TX bytes:78700 (76.8 KB)

joel@joels-laptop:~$

---

### Post by jheaton5 on 2008-10-05
I am not able to go back to the way it was before I did all of the above.  Perhaps new driver is not compatable with 8.04 Hardy.  I will try 8.10 when it is released on October 30.

If anyone can recommend a fix now I will be eternally greatful.  The wire to my ethernet connection is in the way and oh, so archaic.

Be well,

---

### Post by jheaton5 on 2008-10-05
bump

---

### Post by jheaton5 on 2008-10-05
bump

---

### Post by jheaton5 on 2008-10-06
bump

---

### Post by WannabeFantasma on 2009-01-21
EDIT: NVM wireless is working normal

---

