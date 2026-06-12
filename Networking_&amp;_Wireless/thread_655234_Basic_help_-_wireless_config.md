---
title: "Basic help - wireless config"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by David_UK on 2008-01-01
Hi

I'm pretty new to linux, and I'm trying to set up wireless connection on a test box.

1.  I think I have installed drivers correctly using ndiswrapper.  It's a USB netgear wg111v2 using the 0846:6a00 chips.  The indicator light flashes from time to time, but doesn't stay on.

2.  wlan0 is visible in 'network', ndiswrapper -l gives 'net111v2 installed, device present'.

3.  I have a wireless AP called 'test' with no encription.  I have entered 'test' as the essid in network settings, but left the WEP field blank.

4.  This does not connect to the 'net, and I can't ping anything.

5.  iwconfig gives:
wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2346 B   Fragment thr=2400 B   
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

6. iwlist scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:0A:96:8C
                    ESSID:"test"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


I'm sure I am missing some fundamental point in the setup - any ideas?

Thanks

---

### Post by Predator[23rd] on 2008-01-01
is your NIC configured? type **ifconfig** and see if your wireless has an IP ...

---

### Post by David_UK on 2008-01-01
Predator - Hi, and thanks.  It's the configuration I think I need help with....

user@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:FB:C3:52  
          inet6 addr: fe80::210:dcff:fefb:c352/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4474372 (4.2 MiB)  TX bytes:1007927 (984.3 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5922 (5.7 KiB)  TX bytes:5922 (5.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:F0:6F:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1494 (1.4 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:6C:F0:6F:E7  
          inet addr:169.254.9.252  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

### Post by Predator[23rd] on 2008-01-01
looks like your NICs are not configured.

edit /etc/network/interfaces

[I]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[/I]

this should work. restart your network with **/etc/init.d/networking restart**

---

### Post by David_UK on 2008-01-01
Predator

Hang on, bizarre.  It's just started working.  I had seen forum discussions about the phantom appearance of wireless networks after some time - odd!

Thanks for your help though - I might be back later when I try to set up the encription!

David

---

### Post by Predator[23rd] on 2008-01-01
> **David_UK said:**
> Hang on, bizarre.  It's just started working.

:guitar:

mate, I gave up thinking about why something just started to work or stopped working without any obvious reason. computer hardware is beyond control nowadays and software never was under control.

just cross your fingers, punch in some basic lines and hope it "solves" your problem. :D

---

