---
title: "internet bugs out on attempting crossover connection"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by penguinabuser on 2007-01-22
I have 2 comps both dual boot dapper and XP connected by crossover cable. Internet connection is on comp 1 through alcatel speedtouch usb modem. Network works fine on ethernet under  XP with comp 2 accessing the web through comp 1's connection, but I'm buggered if I can get the same result when both machines are running dapper! - The internet connection keeps on dropping out whenever I try something to bring the local connection up.
Would also like to have comp 2 running XP while comp 1 runs dapper and be able to share the  usb printer connected to comp 1! (Thinks - no more usb gadgets!)
Any help gratefully received.

---

### Post by koenn on 2007-01-22
> The internet connection keeps on dropping out whenever I try something to bring the local connection up.
Describe what you do "to bring the local connection up", (include output of commands if possible)
describe "internet connection keeps dropping out" in detail. 
you may also want to describe how you've set up comp1 (in  Ubuntu) to let it share the internet connection with comp 2

---

### Post by penguinabuser on 2007-01-24
ok, sorry about lack of detail!

output of ifconfig on comp1
eth0      Link encap:Ethernet  HWaddr 00:11:11:D1:E3:2D
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fed1:e32d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12070 (11.7 KiB)  TX bytes:23000 (22.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2108 (2.0 KiB)  TX bytes:2108 (2.0 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.127.xx.xx  P-t-P:87.127.xxx.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2166641 (2.0 MiB)  TX bytes:250428 (244.5 KiB)


what I think this means is that comp1 (ip address :192.168.0.1) is using eth0 to connect locally - through the ethernet  card to comp2 (whose ip address is 192.168.0.2) - I can ping comp2 from comp1 and vice versa using network tools.
Also shows comp1's internet link through ppp0 using my static ip address - I can also ping web addresses with network tools on comp1 if I select ppp0 as the network device, and can ping the static ip 87.127.xx.xx from comp2 over eth0 so everything seems to be connected ok. 
so: internet connection on comp1 is ppp0, ip address 87.127.xx.xx - but the modem connection ppp0 is shown as not configured under network settings.
LAN connection is eth0, comp1 settings are ip address 192.168.0.1 netmask 255.255.255.0
the gateway address is currently blank 'cos when I enter either 192.168.0.1 or my static ip (87.127.xx.xx) and click ok (or run /etc/init.d/network restart)  is when my internet connection disappears. Comp2 settings are ip address 192.168.0.2 netmask 255.255.255.0 and gateway address is 192.168.0.1
So problem seems to be getting the two machines to talk together on eth0 without throwing the ppp0 connection out.
This is beyond me at the moment esp as network settings defaults to eth0 as gateway device.

---

