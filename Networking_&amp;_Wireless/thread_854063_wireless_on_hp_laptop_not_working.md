---
title: "wireless on hp laptop not working"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by a511475 on 2008-07-09
my wireless is not working.  first time user.
here are the stats.  Please help me
a511475@a511475-laptop:~$ sudo lshw-C network 
[sudo] password for a511475: 
sudo: lshw-C: command not found 
a511475@a511475-laptop:~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:c0:9f:69:b1:bd 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
  *-network:1 
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 6 
       bus info: pci@0000:02:06.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:90:4b:b4:57:53 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
a511475@a511475-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:"dahlianoodles"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

a511475@a511475-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:69:b1:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:10 Base address:0x3000 

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:9f:69:b1:bd  
          inet addr:169.254.9.175  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:10 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1484 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1484 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:76728 (74.9 KB)  TX bytes:76728 (74.9 KB) 

a511475@a511475-laptop:~$ 

is this enough info?
it is my understanding that the driver is standard for this OS
I am so know I do not know how to interperate this info

---

### Post by df6269 on 2008-07-09
Try to use this command ifup wlan0.
Wlan0 device can be shown by ifconfig command.
#ifconfig
Scan wireless network that will make sure the wireless device workable. 
#iwlist wlan0 scanning

---

### Post by a511475 on 2008-07-09
> **df6269 said:**
> Try to use this command ifup wlan0.
Wlan0 device can be shown by ifconfig command.
#ifconfig
Scan wireless network that will make sure the wireless device workable. 
#iwlist wlan0 scanning

When I  enter ifup wlan0  I get ifup: failed to open  statefile /var/run/network/ifstate: permission denied

when I enter #ipconfig
a blank line is returned
the same for #iwlist wlan0 scanning
Help

---

### Post by a511475 on 2008-07-09
> **a511475 said:**
> When I  enter ifup wlan0  I get ifup: failed to open  statefile /var/run/network/ifstate: permission denied

when I enter #ipconfig
a blank line is returned
the same for #iwlist wlan0 scanning
Help

MORE INFO
WHEN I ENTER iwlist wlan0 scanning 
i get wlan0  no scan results
when i enter ipconfig
the wireless is not shown  only eth0 , eth0: avahi , lo
i do not know what all this means!

---

