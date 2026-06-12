---
title: "Getting USB Wireless card to work with ndiswrapper"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by g3k0 on 2009-08-22
Hello. I have a netgear wg111t usb wireless card on my desktop.  I have been trying to set it up following other posts here and have it mostly done.
I did ndiswrapper -i netwg11t.inf and also for athfmwdl.inf
I did ndiswrapper -m
I appended ndiswrapper on modprobe.preload
iwconfig shows wlan0
```

ben@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"netgear"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ben@ubuntu:~$ 


```

I am assuming essid should be the name of my router which I set it to.

The light blinks on it but how do I connect to a wireless network~!!!

Thanks

(PS. Using 9.04)

edit:

```

ben@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:db:52:e1  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fedb:52e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:823399 (823.3 KB)  TX bytes:151145 (151.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:75:8f:1b:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10952 (10.9 KB)  TX bytes:10952 (10.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b4:7f:49  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:2f:b4:7f:49  
          inet addr:169.254.5.255  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

ben@ubuntu:~$ 


```

```

ben@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     No scan results

ben@ubuntu:~$ 


```

BTW I am hardwired at the  moment

---

### Post by PukingPenguin on 2009-08-22
First, run ```
iwlist scanning
```to output what the card is seeing.
 
Then you can confirm you access point info is correct. 

If it is, the try ```
sudo dhclient
```
and post the output here, if it fails.

If it succeeds, you're welcome.

If not, make sure you have all encryption turned off (at the router), and try again.

---

### Post by g3k0 on 2009-08-22
I actually edited and put in the scan in the first post when you were replying I guess.  It came back with nothing.

---

### Post by bkratz on 2009-08-22
> **g3k0 said:**
> I actually edited and put in the scan in the first post when you were replying I guess.  It came back with nothing.


I believe that network manager can only handle either the wired or the wireless connection one at a time. So run your iwlist scan when disconnected from wired connection.

---

### Post by g3k0 on 2009-08-22
Same thing with it unplugged  :(
```
n@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by Buuntu on 2009-08-22
Did you run ```
sudo modprobe ndiswrapper
``` after you had installed the drivers?

---

### Post by g3k0 on 2009-08-22
ben@ubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
ben@ubuntu:~$ 

I did and I got this.

---

### Post by g3k0 on 2009-08-23
Still not working, but I got iwlist scan to see my router and ran dhclient

```

ben@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:4E:1E:3D:1C
                    ESSID:"c040"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:24:B2:2D:8B:7E
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning.

ben@ubuntu:~$ sudo dhclient
[sudo] password for ben: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/52:55:91:b3:83:38
Sending on   LPF/pan0/52:55:91:b3:83:38
Listening on LPF/eth1/00:04:75:8f:1b:01
Sending on   LPF/eth1/00:04:75:8f:1b:01
Listening on LPF/eth0/00:03:47:db:52:e1
Sending on   LPF/eth0/00:03:47:db:52:e1
Listening on LPF/wlan0/00:1b:2f:b4:7f:49
Sending on   LPF/wlan0/00:1b:2f:b4:7f:49
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ben@ubuntu:~$

```

---

### Post by g3k0 on 2009-08-23
Solved!!!! NETGEAR is case sensitive in my ssid! GAH. lol I noticed after I got the iwlist scanning to work and saw it there.

Thanks to everyone that helped lol.:lolflag::guitar:

---

### Post by Buuntu on 2009-08-23
Great.

It might not load after you reboot.  To get it to load at boot up you have to edit your /etc/modules file and add ndiswrapper in a new line.

---

