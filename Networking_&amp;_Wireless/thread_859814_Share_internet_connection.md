---
title: "Share internet connection?"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Hendore on 2008-07-14
Hey, I had everything setup great on Windows but I was curious on giving Ubuntu a test drive. I have a wireless router downstairs which receives internet input from a modem. I then have a PC upstairs that connects to the router using a wireless adapter. This works fine and I have internet access on my PC but heres my problem, I have a Playstation3 next to my PC but the wireless adapter in the PS3 is pretty bad and picks up the router downstairs with ~15% signal. So I have another router connected to my PC via a crossover cable then I'm connecting the PS3 to this router instead of the one downstairs. The PS3 connects to it no problem but theres no internet connection going to the router from the PC. Like I said, it was working perfect with this setup on windows after sharing the wireless device but I can't seem to do the same on Hardy Heron. I would be very grateful with any help on sharing the PC's internet connection over the second router.

Thank you for your time.

---

### Post by Hendore on 2008-07-15
Anyone got any ideas on fixing this?, I really don't want to be forced to use Windows because of a small problem.

---

### Post by issih on 2008-07-15
If I've grasped the problem correctly, you want to share the internet connection of your ubuntu box (coming in from the wireless connection) to the ps3 via a router. if thats the case then you should look at installing Firestarter:

```
sudo apt-get install firestarter
```

Its actually a firewall configuration tool, but the little wizard lets you easily set up connection sharing.

Hope that helps

---

### Post by Hendore on 2008-07-15
Yes, thats exactly what I'm wanting to do, I'll look into firestarter. Thanks alot.

---

### Post by Hendore on 2008-07-15
OK, so i followed the wizard and everything seemed to be going fine with firestarter, on.y problem now is NetworkManager is only allowing me to have 1 device enabled at a time. Would it be possible to disable NetworkManager and edit the interfaces file to do what I want?

---

### Post by issih on 2008-07-15
Odd, you really should be able to enable both the ethernet and the wireless ports. You can certainly do it without using the applet, but if you use the manual configuration section available from the applet, then that is just a front end to help you edit the file correctly, so I'd try in there first.

---

### Post by Hendore on 2008-07-16
> **issih said:**
> Odd, you really should be able to enable both the ethernet and the wireless ports. You can certainly do it without using the applet, but if you use the manual configuration section available from the applet, then that is just a front end to help you edit the file correctly, so I'd try in there first.

I was using the applet, I changed the settings of both wlan0 and eth0 devices using the NetworkManager applet but it kept disabling one when enabling the other device :(

---

### Post by dmizer on 2008-07-16
the wlan0 and eth0 devices must have ip addresses on different subnets.

for example, if your wlan0 ip address is 192.168.1.100, your eth0 cannot be 192.168.1.x (where "x" is any number between 1 and 254).  i suggest using something completely differnt for your eth0 adapter.  for example: 10.0.0.x or 172.16.0.x

---

### Post by Hendore on 2008-07-16
> **dmizer said:**
> the wlan0 and eth0 devices must have ip addresses on different subnets.

for example, if your wlan0 ip address is 192.168.1.100, your eth0 cannot be 192.168.1.x (where "x" is any number between 1 and 254).  i suggest using something completely differnt for your eth0 adapter.  for example: 10.0.0.x or 172.16.0.x

OK, just tried that, my wlan0 ip is set to 192.168.2.4 and the eth0 device ip is set to 192.168.10.1 but still no luck :(

---

### Post by dmizer on 2008-07-16
please post the contents of: /etc/network/interfaces

---

### Post by Hendore on 2008-07-16
> **dmizer said:**
> please post the contents of: /etc/network/interfaces

This is the setup NetworkManager gave me:

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid belkin54g

iface eth0 inet static
address 192.168.10.1
netmask 255.255.255.0

auto wlan0

```

---

### Post by dmizer on 2008-07-17
okay ... post the output of this:
```
sudo /etc/init.d/networking restart
sudo ifup eth0
```

---

### Post by Hendore on 2008-07-17
Thanks for taking the time to help me out :)

```

matthew@tuxbox:~$ sudo /etc/init.d/networking restart
[sudo] password for matthew: 
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9501
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:3f:74:31:24
Sending on   LPF/wlan0/00:17:3f:74:31:24
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:3f:74:31:24
Sending on   LPF/wlan0/00:17:3f:74:31:24
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.2.4 from 192.168.2.1
DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.4 from 192.168.2.1
bound to 192.168.2.4 -- renewal in 931214895 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
                                                                         [ OK ]
matthew@tuxbox:~$ sudo ifup eth0
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.

```

---

### Post by dmizer on 2008-07-17
looks like it worked.

you should now see that both interfaces have an ip. check the output of:
```
sudo ifconfig
```

---

### Post by reyajaswal on 2008-07-17
hi there, 
I have a wireless router downstairs which receives internet input from a modem. I then have a PC upstairs that connects to the router using a wireless adapter. This works fine and I have internet access on my PC but heres my problem, I have a Playstation3 next to my PC but the wireless adapter in the PS3 is pretty bad and picks up the router downstairs with ~15% signal. So I have another router connected to my PC via a crossover cable then I'm connecting the PS3 to this router instead of the one downstairs.can you please tell me how can i resolve this problem...please sout my problem.

thanks !!

---

### Post by Hendore on 2008-07-17
> **dmizer said:**
> looks like it worked.

you should now see that both interfaces have an ip. check the output of:
```
sudo ifconfig
```

Yup, the IP's are set correct on both:

```

matthew@tuxbox:~$ sudo ifconfig
[sudo] password for matthew: 
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:37:c9:2f  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe37:c92f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79640 (77.7 KB)  TX bytes:37791 (36.9 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190049 (185.5 KB)  TX bytes:190049 (185.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:74:31:24  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe74:3124/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:434647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:416788726 (397.4 MB)  TX bytes:36145913 (34.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-74-31-24-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Hendore on 2008-07-17
> **reyajaswal said:**
> hi there, 
I have a wireless router downstairs which receives internet input from a modem. I then have a PC upstairs that connects to the router using a wireless adapter. This works fine and I have internet access on my PC but heres my problem, I have a Playstation3 next to my PC but the wireless adapter in the PS3 is pretty bad and picks up the router downstairs with ~15% signal. So I have another router connected to my PC via a crossover cable then I'm connecting the PS3 to this router instead of the one downstairs.can you please tell me how can i resolve this problem...please sout my problem.

thanks !!

??? Is this a serious post? Looks alot like my original :P

---

### Post by dmizer on 2008-07-17
looks good to me.  now i have no idea how to tell you what to do to configure firestarter for internet connection sharing.  it's possible to do ICS without firestarter, and i think it's fairly easy.

so, i suggest that you uninstall firestarter, and try this howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Hendore on 2008-07-17
Thanks allot man, I followed the guide and it wasn't working with the router connected so I just discarded the router and plugged the Ethernet cable straight from the PC -> PS3 and it connected first attempt. I'm going to assume it's the routers settings. Thanks again =]

---

### Post by dmizer on 2008-07-17
with internet connection sharing, your ubuntu computer IS the router.  you could have used the router if you set the router to function as a hub only (disable NAT), but a straight through cable works just as well.

glad you got things working!  i spent a couple hours editing that guide today, so it's good to know that it worked as expected.

---

