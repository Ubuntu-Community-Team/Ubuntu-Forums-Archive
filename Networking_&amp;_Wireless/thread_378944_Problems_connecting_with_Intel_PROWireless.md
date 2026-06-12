---
title: "Problems connecting with Intel PRO/Wireless"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Scottyk on 2007-03-07
I have tried everything I can think of so I am asking you guys for help. My laptop sees my network I have a 93% signal strenght and its sending packets but for some reason its not accepting them. I am useing WEP and I have tried all the keys. Here is my info:

**iwconfig:**

lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:FE:07:ED   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:53  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:59:21:0C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x8800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:79:F6:44  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe79:f644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:527 errors:53 dropped:53 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3312 (3.2 KiB)
          Interrupt:11 Base address:0x6000 Memory:e0204000-e0204fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4376 (4.2 KiB)  TX bytes:4376 (4.2 KiB)

**iwlist scan:**

lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:10:FE:07:ED
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm  
                    Extra: Last beacon: 4072ms ago

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


**sudo gedit /etc/network/interfaces**
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet static
wireless-essid linksys
wireless-key s:49774B692D
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet static
wireless-essid linksys
wireless-key s:49774B692D
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1


Thanks for all your help!!

---

### Post by Floppyjoe on 2007-03-07
Do you have your interfaces listed twice in /etc/network/interfaces or is that a typo?

---

### Post by Scottyk on 2007-03-08
Thats a type o my bad I pasted it twice. Any ideas? thanks!!

---

### Post by chili555 on 2007-03-08
I think you are not yet properly associated with your router. You only have an IP address in ifconfig, because you specified one in interfaces. The true test is if you can ping -c3 192.168.1.1. If you get no packets returned, it's because your router probably doesn't like your key and won't let you in the door.

Here is a post that may help: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

