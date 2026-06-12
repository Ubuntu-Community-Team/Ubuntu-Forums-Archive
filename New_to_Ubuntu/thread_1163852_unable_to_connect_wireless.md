---
title: "unable to connect wireless"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by alex ness on 2009-05-19
Hi there

This is my wireless card Intel (R) PRO/Wireless LAN 2100 3B Mini PCI Adaptor. the enable wireless option in network manager is disabled. 

Output from LSHW


alex@alex-laptop:~$ sudo lshw -C network
[sudo] password for alex: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 04
       serial: 00:04:23:8c:d4:47
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 8b
       serial: 00:40:d0:47:b7:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.64 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:60:a2:33:bc:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

alex@alex-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:47:b7:2e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe47:b72e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:124776367 (124.7 MB)  TX bytes:4766356 (4.7 MB)
          Interrupt:11 Base address:0x800 

eth1      Link encap:Ethernet  HWaddr 00:04:23:8c:d4:47  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:e0001000-e0001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

Any ideas, can anyone suggest something?? Please help...

Cheers

Alex

---

### Post by Kevbert on 2009-05-19
Looks like you need to turn on wireless on your laptop. If there is a front panel switch, press it just once and see if that helps (any led indicators may not display the active state).
In terminal please enter
```
iwconfig
```
This will give you the name given to wireless (wlan0, pan0 etc).
Now enter
```
sudo ifconfig wlan0 up
```
(change wlan0 for whatever you previously had displayed) to try to enable wireless.

---

### Post by porchrat on 2009-05-19
I have this same wireless module running under 8.04 and I'm sorry to say that it was a mess getting it running.

You are going to battle with getting it to run under Ubuntu because Ubuntu doesn't (as far as I could see), come with a driver for it and there isn't a readily usable one on the net.

In the end I used the Windows XP drivers with ndiswrapper and I would recommend you do the same. What laptop are you running? I run a thinkpad T40 and I got the XP drivers off of the IBM website if I recall correctly. I still have them actually.

Try using the switch on the front of the laptop and see what it does. To do this boot into Windows XP, if you still run it, then switch it on there and then shutdown and get back into Ubuntu and hopefully it will run. If it doesn't then you probably don't have the drivers and I would once again recommend ndiswrapper.

There is an open source project on the net aimed at maintaining Linux drivers for the PRO/Wireless 2100, but it hasn't been updated in a while. The project homepage is [here]("http://ipw2100.sf.net/") in case you are interested in checking it out.

---

