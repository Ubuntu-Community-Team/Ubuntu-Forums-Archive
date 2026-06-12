---
title: "Belkin N1 Wireless Desktop Card almost working"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by geislefc on 2007-11-21
I am trying to configure a desktop machine to connect to a Belkin N1 Broadband Router using the Belkin N1 Wireless Desktop Card (net5416.inf, Atheros chipset) on an AMD Athalon 1.4Ghz with 1 Gigabyte of RAM with a current version of Gutsy Gibbon kernel 2.6.22-14-386.
[INDENT][INDENT]At this time, I have System->Administration->Windows Wireless Manager showing me what I believe to be the correct device, however, I had to associate the device and driver using the 'dangerous' **ndiswrapper -a** function after I stumbled on the following:
[INDENT]lawrence# ndiswrapper -l         
lawrence# ndiswrapper -i Belkin/InstallationFiles/Driver/net5416.inf
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
lawrence# ndiswrapper -l                                            
net5416 : driver installed
lawrence#[/INDENT]
A driver with no associated device, so...
[INDENT]lawrence#  **ndiswrapper -a 168c:ff1d net5416 **               
WARNING: Driver 'net5416' will be used for '168C:FF1D'
This is safe _only_ if driver net5416 is meant for chip in device 168C:FF1D
lawrence# **ndiswrapper -l **          
net5416 : driver installed
device (168C:FF1D) present
[/INDENT]
However, when trying to write the modprobe file, I saw the following:
[INDENT]lawrence# ndiswrapper -m
module configuration already contains alias directive
[/INDENT]
Nevertheless, I continued with
lawrence# modprobe -r ndiswrapper
lawrence# modprobe ndiswrapper 
lawrence# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]
At this point the Windows Wireless Manager announces that the hardware is present.  running ifconfig shows no IP granted.  I reboot the system (hey, it sometimes helps) and run ifconfig again, only now it tells me that the device is no longer wlan0 but wlan1...still no IP from the router. 
[INDENT]lawrence# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:29:54:07:B4  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe54:7b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:146 txqueuelen:1000 
          RX bytes:1518046 (1.4 MB)  TX bytes:431125 (421.0 KB)
          Interrupt:5 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9612 (9.3 KB)  TX bytes:9612 (9.3 KB)

wlan1     Link encap:Ethernet  HWaddr 00:11:50:F7:D9:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:ee800000-ee810000 

lawrence# iwconfig wlan1
wlan1     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lawrence# 

[/INDENT]
Reading around on the threads gives me the idea to look at /etc/network/interfaces where I find a reference to wlan0.  I back up the file and change it to wlan1.  Finally  I attempted to ping the wireless router (192.168.2.1) using the following:
ping -I wlan1 192.168.2.1

lawrence# ping -I wlan1 192.168.2.1
PING 192.168.2.1 (192.168.2.1) from 192.168.1.3 wlan1: 56(84) bytes of data.
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
From 192.168.1.3 icmp_seq=4 Destination Host Unreachable
From 192.168.1.3 icmp_seq=6 Destination Host Unreachable
From 192.168.1.3 icmp_seq=7 Destination Host Unreachable
From 192.168.1.3 icmp_seq=8 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7999ms
, pipe 3
lawrence# [/INDENT]
192.168.1.3 is the DHCP address my desktop has been granted by the wired router that is currently working.
Any suggestions would be appreciated since I'm hoping to continue my 'getting hit on the head' lessons.
Fritz

---

