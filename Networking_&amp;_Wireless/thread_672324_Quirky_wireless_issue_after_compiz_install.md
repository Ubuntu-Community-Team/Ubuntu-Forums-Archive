---
title: "Quirky wireless issue after compiz install??"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by jsteiner on 2008-01-19
I need some insight with a new wireless issue that I'm having.  Here are the details. I'm running 7.10 with the generic 2.6.22-14.47 kernel, Gnome 2.20.1 with compiz 1:0.6.1+git20071008-0ubuntu1.1 on a Dell Inspiron 6000.  My router is a Linksys wrt100 with wpa1 enabled.  This issue is unique to my one laptop, only with this Ubuntu install. It appears to me that after installing and configuring compiz my wireless card stopped fully initializing. I really don't see the relation between compiz and wireless. My first observation was that the WiFi light on the laptop no longer comes on.  My drivers are for the wireless card are loading properly. Through playing around I discovered that if I make any change with the network-admin tool so that /etc/network/interfaces is rewritten my wireless then picks up an IP and works perfectly.  I've diff'ed the interfaces file before and after using the network-admin utility and there are no differences.  When I reboot I lose the wireless again until I go through he same process again.  One thing that is interesting is that when the wireless is up and working properly the WiFi light on the machine will not come on.  If I swap drives in the machine to another build or another OS the light is working.  I need some advice on this. 

Jan 19 10:58:08 shaggy kernel: [   15.312000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
Jan 19 10:58:08 shaggy kernel: [   15.312000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan 19 10:58:08 shaggy kernel: [   15.312000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Jan 19 10:58:08 shaggy kernel: [   15.316000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

My interfaces file:

#iface eth0 inet dhcp
auto eth2
#iface eth2 inet dhcp
auto ath0
#iface ath0 inet dhcp
auto wlan0
#iface wlan0 inet dhcp
iface eth1 inet dhcp
wpa-psk 0ac94046305dbf9cf60cd6ffa418fa94888447c215f10a4f3a260cf14c8c7430
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Daphne03

This is an ifconfig when the card is working after a network-admin changes the /etc/network/interfaces file:

jsteiner@shaggy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:D6:4C:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:10:AC  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe83:10ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:5 dropped:5 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9210 (8.9 KB)  TX bytes:5039 (4.9 KB)
          Interrupt:18 Base address:0x2000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This is an ifconfig after a reboot:

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:10:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2000 Memory:dfcfd000-dfcfdfff 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:83:10:AC  
          inet addr:169.254.7.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Any ideas what is going on here?

I've read the follow:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.p...hlight=linksys](http://ubuntuforums.org/showthread.p...hlight=linksys)
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by jsteiner on 2008-01-20
Well, I've kind of got it figured out but don't know why.  I read some threads about problems with network-admin on 7.10.  I uninstalled it and install wicd.  I then cleaned out all  of my /etc/network/interfaces entries.  I ran wicd and configured eth1.  My wireless know works after a reboot.  The WiFi light still is not functional but I can live with that little thing.  I'm not sure if I can turn my radio on and off with the Fn-F2 key sequence yet.

---

