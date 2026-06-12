---
title: "need help with my wireless network connection"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by zero7404 on 2008-10-13
i get inconsistent behavior from my wireless connection in ubuntu, trying to figure out how to solve it....

is there a way to rebuild the wireless networking or remove the drivers and reinstall them ? i have a feeling that some updates i performed might have messed up the wireless on my installation.

thanks

---

### Post by superprash2003 on 2008-10-13
post output of the following commands
1)iwconfig
2)lshw -C network

---

### Post by zero7404 on 2008-10-13
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"dlink07"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1C:F0:57:42:1B   
          Bit Rate=48 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=77/100  Signal level:-65 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:ca:55:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.102 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:cf:47:72
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5754m-v3.23 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:f8:79:53:b3:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2008-10-14
well you seem to be connected to dlink07.. please post output of ifconfig.. are you able to ping your router?

---

### Post by zero7404 on 2008-10-14
ifconfig as follows

> eth0      Link encap:Ethernet  HWaddr 00:21:9b:cf:47:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6284 (6.2 KB)  TX bytes:6284 (6.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:ca:55:11  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:feca:5511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1002437 (1.0 MB)  TX bytes:170849 (170.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-CA-55-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


i used network tools to ping 192.168.0.1 (router IP) for 5 times, all 5 were sucessful.

the problem occurs when i start up ubuntu (i have a dual-boot configuration), not always. i wait for drive activity to be done, then try to connect. i have since turned off automatic connect under network connections>edit for this connection. my last few manual connections have been fine. when i experience the problem, i restart my machine into vista and the connection seems to be fine.

not sure if something is wrong with the network config on the installation or not, so i deleted network manager yesterday and reinstalled it, that did not seem to change things.

---

### Post by superprash2003 on 2008-10-15
so you are getting an ip... you are able to ping the router.. are you able to access the internet?? post output of ping google.com

---

### Post by zero7404 on 2008-10-15
> **superprash2003 said:**
> so you are getting an ip... you are able to ping the router.. are you able to access the internet?? post output of ping google.com

yes i am able to access the internet. i posted my problem because almost 1/2 the time when i try to connect to my network it keeps returning with the password prompt window to enter the key and when it does that, it won't connect no matter how many times i reenter my network passkey.

it seems as tho this is a glitch with the OS and bootup.

i am about to scrap ubuntu completely....

as recently some start up problems have surfaced, after beginning normal bootup, i get a series of loud beeps the only way to stop it is to shut the machine off.
when i load up with the recovery option, do a check on the file system, everything passes and i continue normal bootup into the OS fine.

---

