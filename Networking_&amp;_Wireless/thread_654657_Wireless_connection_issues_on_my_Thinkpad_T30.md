---
title: "Wireless connection issues on my Thinkpad T30"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by ksteubing on 2007-12-31
I'm a newbie to Ubuntu(just loaded 7.10) I like everything so far except for wireless.  I have a Thinkpad t30 and have Belkin router which works for my Thinkpad t61 and IMac...no problem.  I can see the signal and load my 128 bit encryption key and have checked it 10 times....and it just keeps trying but then gives up and reverts back to my ethernet connection.  I've tried the disconnecting my ethernet and unclicking the enable roaming mode box as suggested in one of the forums and that didn't work.  I'm using an open system on my other thinkpad (windows XP Prof).

I've run the check for the driver and connection to the router...and here are the results.  I hope someone can help as I've gone throw all the troubleshooting and nothing is working.
steubing@steubing-laptop:~$ sudo lshw -C network 
[sudo] password for steubing: 
   >   *-network:0             
       description: Wireless interface 
       product: Prism 2.5 Wavelan chipset 
       vendor: Intersil Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       logical name: wifi0 
       version: 01 
       serial: 00:05:3c:08:28:1c 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm cap_list logical wireless ethernet physical 
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b 
  *-network:1 
       description: Ethernet interface 
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 42 
       serial: 00:09:6b:60:3d:17 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.2.4 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s 
steubing@steubing-laptop:~$ sudo lshw -C network 


steubing@steubing-laptop:~$ iwconfig 
lo        no wireless extensions. 
irda0     no wireless extensions. 

eth0      no wireless extensions. 

wifi0     IEEE 802.11b  ESSID:"Belkin_G_Plus_MIMO_947119#"  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:3F:94:71:19   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off 
          Power Management:off 
          
wlan0     IEEE 802.11b  ESSID:"Belkin_G_Plus_MIMO_947119#"  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:3F:94:71:19   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=56/70  Signal level=-38 dBm  Noise level=-95 dBm 
          Rx invalid nwid:0  Rx invalid crypt:228  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0 

steubing@steubing-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:09:6B:60:3D:17  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::209:6bff:fe60:3d17/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:115623 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:62567 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:173275402 (165.2 MB)  TX bytes:4522731 (4.3 MB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

wifi0     Link encap:UNSPEC  HWaddr 00-05-3C-08-28-1C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2524 (2.4 KB)  TX bytes:9889 (9.6 KB) 
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr 00:05:3C:08:28:1C  
          inet6 addr: fe80::205:3cff:fe08:281c/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:28 overruns:0 frame:0 
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:9585 (9.3 KB) 
          Interrupt:11 

steubing@steubing-laptop:~$

---

