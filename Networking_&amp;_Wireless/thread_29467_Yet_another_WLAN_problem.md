---
title: "Yet another WLAN problem"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by sibor on 2005-04-24
Hi
I have tried to find the info in the previous posts, byt my problem seems to occur where the other are home free.

In short: I can (think I can) install the driver for my wlan, but I can't connect to the access point.

Using ndiswrapper to install WMP54G-EU driver (bcmwl5.inf from enclosed cd-rom)

Check:
  sboe02@ubuntu:~$ sudo ndiswrapper -l
  Installed ndis drivers:
  bcmwl5  driver present, hardware present 

... So it should work... right?

running:
  sboe02@ubuntu:~$ modprobe ndiswrapper

No problem... great news?

Set my ID and WEP to my network (Also tried disabling WEP... Same thing)
  sboe02@ubuntu:~$ iwconfig wlan0 essid sibor
  sboe02@ubuntu:~$ sudo iwconfig wlan0 key XXXXXXXXXX

...well this does not change the content of iwconfig...
  sboe02@ubuntu:~$ iwconfig
  lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      no wireless extensions.
  sit0      no wireless extensions.

  wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx inv    alid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

WHY???

I can contact the WLAN from my windows boot, but the information from windows is very sparse... So i can't pinpoint the problem.

The access point is configured to block all other macadresses than the one I'm using which does work from Windows. (I also tried to disable this... same thing)

ok... Tried anyway:
  sboe02@ubuntu:~$ sudo dhclient wlan0
  Internet Systems Consortium DHCP Client V3.0.1
  Copyright 2004 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

  sit0: unknown hardware address type 776
  sit0: unknown hardware address type 776
  Listening on LPF/wlan0/00:0f:66:76:74:25
  Sending on   LPF/wlan0/00:0f:66:76:74:25
  Sending on   Socket/fallback
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

Part of my kernel ring buffer:
  sboe02@ubuntu:~$ dmesg | grep "ndis"
  ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
  ndiswrapper: using irq 18
  wlan0: ndiswrapper ethernet device 00:0f:66:76:74:25 using driver bcmwl5
  ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) added

I really can't see what's wrong.. maybe something with my setup of the router, Linksys WRT54G-EU? But I can't see what.

I also tried PINGing my router/AP with both my eth0 and my wlan0. eth0 works.. wlan doesn't:
  sboe02@ubuntu:~$ ping -Ieth0 192.168.1.1
  PING 192.168.1.1 (192.168.1.1) from 192.168.1.101 eth0: 56(84) bytes of data.
  64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.80 ms
  64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.734 ms

  --- 192.168.1.1 ping statistics ---
  2 packets transmitted, 2 received, 0% packet loss, time 1000ms
  rtt min/avg/max/mdev = 0.734/1.769/2.805/1.036 ms
  sboe02@ubuntu:~$ ping -Iwlan0 192.168.1.1
  PING 192.168.1.1 (192.168.1.1) from 192.168.1.101 wlan0: 56(84) bytes of data.
  From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
  From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
  From 192.168.1.101 icmp_seq=4 Destination Host Unreachable

  --- 192.168.1.1 ping statistics ---
  5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4000ms
  , pipe 3

I hope that it is just some dumb ass fault I have made, but I really can't find it. Hoping for your help.

THX in advance
Simon Borresen

---

### Post by Cal on 2005-04-25
[QUOTE=sibor]Hi
I have tried to find the info in the previous posts, byt my problem seems to occur where the other are home free.

In short: I can (think I can) install the driver for my wlan, but I can't connect to the access point.

Using ndiswrapper to install WMP54G-EU driver (bcmwl5.inf from enclosed cd-rom)

Check:
  sboe02@ubuntu:~$ sudo ndiswrapper -l
  Installed ndis drivers:
  bcmwl5  driver present, hardware present 

... So it should work... right?

running:
  sboe02@ubuntu:~$ modprobe ndiswrapper

No problem... great news?

Set my ID and WEP to my network (Also tried disabling WEP... Same thing)
  sboe02@ubuntu:~$ iwconfig wlan0 essid sibor
  sboe02@ubuntu:~$ sudo iwconfig wlan0 key XXXXXXXXXX

...well this does not change the content of iwconfig...
  sboe02@ubuntu:~$ iwconfig
  lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      no wireless extensions.
  sit0      no wireless extensions.

  wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx inv    alid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

WHY???

I can contact the WLAN from my windows boot, but the information from windows is very sparse... So i can't pinpoint the problem.

The access point is configured to block all other macadresses than the one I'm using which does work from Windows. (I also tried to disable this... same thing)

ok... Tried anyway:
  sboe02@ubuntu:~$ sudo dhclient wlan0
  Internet Systems Consortium DHCP Client V3.0.1
  Copyright 2004 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

  sit0: unknown hardware address type 776
  sit0: unknown hardware address type 776
  Listening on LPF/wlan0/00:0f:66:76:74:25
  Sending on   LPF/wlan0/00:0f:66:76:74:25
  Sending on   Socket/fallback
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
  DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

Part of my kernel ring buffer:
  sboe02@ubuntu:~$ dmesg | grep "ndis"
  ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
  ndiswrapper: using irq 18
  wlan0: ndiswrapper ethernet device 00:0f:66:76:74:25 using driver bcmwl5
  ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) added

I really can't see what's wrong.. maybe something with my setup of the router, Linksys WRT54G-EU? But I can't see what.

I also tried PINGing my router/AP with both my eth0 and my wlan0. eth0 works.. wlan doesn't:
  sboe02@ubuntu:~$ ping -Ieth0 192.168.1.1
  PING 192.168.1.1 (192.168.1.1) from 192.168.1.101 eth0: 56(84) bytes of data.
  64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.80 ms
  64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.734 ms

  --- 192.168.1.1 ping statistics ---
  2 packets transmitted, 2 received, 0% packet loss, time 1000ms
  rtt min/avg/max/mdev = 0.734/1.769/2.805/1.036 ms
  sboe02@ubuntu:~$ ping -Iwlan0 192.168.1.1
  PING 192.168.1.1 (192.168.1.1) from 192.168.1.101 wlan0: 56(84) bytes of data.
  From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
  From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
  From 192.168.1.101 icmp_seq=4 Destination Host Unreachable

  --- 192.168.1.1 ping statistics ---
  5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4000ms
  , pipe 3

I hope that it is just some dumb ass fault I have made, but I really can't find it. Hoping for your help.

THX in advance
Simon Borresen[/QUOTE]
 I believe your wireless card is based on the athos chipset.  This is supported by the madwifi driver.  Fortunantly it is availible in one of the ubuntu repositories...  The easiest way to install it is to start up synaptic and search for madwifi.  You'll get a list of modules with cpu types, pick your type or the generic i386 version. 

Good luck, I hope it works because I just used up all of my linux juice.  Let me know if it helps.

---

