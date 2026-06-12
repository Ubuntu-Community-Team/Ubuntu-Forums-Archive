---
title: "Wireless option doesn't show in network settings or network-admin"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by mickbw on 2007-05-18
I realize they are the same program but the GUI title says Network Settings

I was having trouble getting a wireless connection on my Inspiron 1501 Dell laptop using Feisty.  It had been working without a problem and I actually think it would have worked again if I simply rebooted the cable modem to begin with.  

Anyway I didn't do that, followed the directions I originally used to set up the wifi on the dell at  [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html).  Now everything looks right including the wifi indicator lighting up on the laptop.  The problem is that Wireless does not show as an option in network-admin now.

When I run iwconfig lo and eth0 say no wireless connections.  

Any suggestions.  This is really bugging me now.

---

### Post by dfreer on 2007-05-18
could you post your /etc/networking/interfaces, and the actual output from iwconfig and ifconfig?

---

### Post by mickbw on 2007-05-18
I did gedit on the /etc/networking/interfaces and nothing was displayed.  I found the interfaces file in /etc/network :
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

ifconnfig:
eth0      Link encap:Ethernet  HWaddr 00:19:B9:67:9C:3F  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe67:9c3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1101957 (1.0 MiB)  TX bytes:169347 (165.3 KiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10376 (10.1 KiB)  TX bytes:10376 (10.1 KiB)

Thanks for the help,

Michael

---

