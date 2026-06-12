---
title: "Wireless on Trimslice stopped working"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by andy-4 on 2014-09-10
I have a Trimslice with and armel version of ubuntu running. The wireless was working ok but at some point it vanished completely, and the gui network admin says "The system network services are not compatable with this version". I have avoided upgrading as I am afraid that the armel version is being phased out and my applications may stop running if I go to armhf.

Here is the output of wireless-info.txt:

[ATTACH]256323[/ATTACH]

Thanks
Andy

---

### Post by varunendra on 2014-09-11
Welcome to the forums andy-4!

I have absolutely no experience with arm based setups, but it seems you were probably using the manually compiled proprietary driver, and had a kernel upgrade recently, after which you need to compile and install it again. Currently, you have blacklisted the native driver, and the proprietary one isn't loaded either.

The "..system network services.." error is usually caused by an incompatible entry in /etc/network/interfaces file. In your case, it could be the "" Studio @ home" line, but I'm not sure.

Suggestion for now, try the native driver "rt2800usb" by removing it from the blacklist.

---

### Post by andy-4 on 2014-09-15
Well, fantastic! I corrected the /etc/network/interfaces file, removed the rt2800usb from the blacklist and rebooted. I got the network up with an IP 10.42.0.1.  I set this up some time ago when the gui networking was still working, as an adhoc wireless network. When this was working, I could connect to the arm pc wirelessly using RDP, and run programs etc. (This is for seeing my navigation program while in sitting the cockpit of my boat). However I can ping this IP from the arm pc itself, but other devices do not see it. Do you know where I can set this up to be visible using the terminal, as the gui networking program still advises "The system networking services are not compatable with this version". The IP does not appear in /etc/network/interfaces. 

eth0      Link encap:Ethernet  HWaddr 00:01:c0:12:15:0e  
          inet addr:111.112.113.16  Bcast:111.112.113.255  Mask:255.255.255.0
          inet6 addr: fe80::201:c0ff:fe12:150e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2166840 (2.1 MB)  TX bytes:21287722 (21.2 MB)
          Interrupt:130 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208253853 (208.2 MB)  TX bytes:208253853 (208.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:95:6b:7d  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:f0ff:fe95:6b7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:58438 (58.4 KB)

PING 10.42.0.1 (10.42.0.1) 56(84) bytes of data.
64 bytes from 10.42.0.1: icmp_req=1 ttl=64 time=0.415 ms
64 bytes from 10.42.0.1: icmp_req=2 ttl=64 time=0.297 ms
64 bytes from 10.42.0.1: icmp_req=3 ttl=64 time=0.286 ms
64 bytes from 10.42.0.1: icmp_req=4 ttl=64 time=0.294 ms
64 bytes from 10.42.0.1: icmp_req=5 ttl=64 time=0.267 ms

--- 10.42.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 0.267/0.311/0.415/0.057 ms

The wireless-info.txt file has changed considerably, but still incomprehensible to me! I attach it here.

In closing, thanks very much for helping me so far.
Andy

I tried the instructions at thenewbieblog.worpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu which should make the IP of the pc 10.0.0.1 as per the /etc/network/interfaces file. 

iface wlan0 inet static
address 10.0.0.1
netmask 255.255.255.0

However after a reboot it still comes up as 10.42.0.1 so I need to know where this could be coming from.

wlan0     Link encap:Ethernet  HWaddr 00:0d:f0:95:6b:7d  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:f0ff:fe95:6b7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16513 (16.5 KB)

Thanks in advance.
Andy

---

### Post by praseodym on 2014-09-15
Clean up the /etc/resolv.conf to the nameservers you need.

---

### Post by varunendra on 2014-09-16
No experience with arm based installations, no experience with ad-hoc networks, so can't offer much help there. Please do as praseodym suggests.

---

### Post by andy-4 on 2014-09-18
I am not sure about resolv.conf - I ran resolconf -u. The file itself warns me not to edit it. I've now got the wireless hotspot working on the arm machine, and that is where the 10.42.0.1 IP comes from. However the arm machine is not visible or even pingable on it's IP or SSID from other wireless computers close enough to it. All I am trying to achieve is be able to run RDP from a tablet and connect to the arm machine. RDP works over the eth0 interface when the arm machine is plugged into the same router, but I want it to be contactable via wireless. So my question now is: With the wireless hotspot set up perfectly (as far as I can see), why would it not be visible to other computers. Maybe hardware?
Thanks for staying with me on this!
Andy

---

### Post by andy-4 on 2014-09-19
Using dnsmasq I have now got the trimslice pc to appear as a wireless network in my Debian laptop's list when I click on the networking icon. When I select it it requests the WAP password which I give, and it then appears to be trying to allocate an IP address to the Debian laptop. However it never gets there. So I have tried to find out why this is. Anyone know?

---

