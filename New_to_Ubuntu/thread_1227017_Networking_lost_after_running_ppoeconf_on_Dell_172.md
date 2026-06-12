---
title: "Networking lost after running ppoeconf on Dell 1720"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by FLURPY on 2009-07-30
If I install Ubuntu, it picks up my network, and I can see my Wifi network.

To connect to it, I run pppoeconf, and can then connect and surf internet.

When I reboot however, I cannot see my network - everything is grayed out.

I have a Dell 1720 laptop running Ubuntu 9.04.

If anyone know how to fix this, please post solution.

---

### Post by cozmicharlie on 2009-07-30
Right click on the network applet in the panel, go to 'edit connections" and go to the tab with your connection (should be broadband in your case".  You should see an option to "connect automatically" - check that, close and it should connect automatically when you restart.

---

### Post by superprash2003 on 2009-07-30
also post output of ifconfig from the terminal

---

### Post by FLURPY on 2009-08-02
Problem not solved.  Thanks for replies though.
Autoconnect is enabled, but once I reboot, I cannot see any network whatsoever.
My Laptop has an Intel 3945ABG wireless card.  

My terminal output log on ifconfig is:
flurpy@flurpy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b6:c4:84  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

pan0      Link encap:Ethernet  HWaddr a2:eb:71:ec:27:4c  
          inet6 addr: fe80::a0eb:71ff:feec:274c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:540 (540.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:8c:70:8e  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe8c:708e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:487897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546194541 (546.1 MB)  TX bytes:42557606 (42.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-8C-70-8E-30-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Any help will be appreciated since I have to reinstall ubuntu everytime I want to go on internet.

---

### Post by FLURPY on 2009-08-11
still don't have itworking properly.
i manage by sudo gedit /etc/network/interfaces in terminal.

it reads like this withoutthe #lines

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

#auto eth0
#iface eth0 inet manual


i then add the #, and after reboot my network is visible again and I can go online by running pppoeconf again.

but ppoeconf reads those lines everytime.

Those lines makes my network invisible to system.
Any ideas of either having pppoeconf not modifying the line everytime, or to fix the problem so I don't have to run pppoeconf every time

help will be appreciated

---

