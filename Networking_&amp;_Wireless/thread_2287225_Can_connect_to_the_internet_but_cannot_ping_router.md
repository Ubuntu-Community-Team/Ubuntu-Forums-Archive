---
title: "Can connect to the internet but cannot ping router."
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by shane_2 on 2015-07-17
Hi all,

I am having a little bit of trouble both with my wireless adapter and my wired ethernet adapter(same exact problem).  If I connect to the router with either one I can surf away fine, ping all the machines connected on the network, ping outside to [www.google.com]("http://www.google.com") BUT cannot ping 192.168.2.1(my own router).  I am currently doing this through ethernet to rule out any wireless issues, I have changed the /etc/resolv.conf file but it seems ok to start with.  The route -n seems good too.  Im not sure where else I can turn to ping my router.  I can also get to 192.168.2.1 through the browser fine(for the router config page).  I can ping the router just fine on my other windows laptop.  Below are a few of the command screens.  Thanks.


ifconfig
[TABLE="width: 500"]
[TR]
[TD]eth0      Link encap:Ethernet  HWaddr 00:24:e8:e5:ca:97  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fee5:ca97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:13978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10242 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:14872693 (14.8 MB)  TX bytes:1302923 (1.3 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186105 (186.1 KB)  TX bytes:186105 (186.1 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:3b:df:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/TD]
[/TR]
[/TABLE]

iwconfig
[TABLE="width: 500"]
[TR]
[TD]lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.
[/TD]
[/TR]
[/TABLE]

route -n
[TABLE="width: 500"]
[TR]
[TD]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
[/TD]
[/TR]
[/TABLE]

cat /etc/resolv.conf
[TABLE="width: 500"]
[TR]
[TD]nameserver 192.168.2.1
nameserver 192.168.208.1
nameserver 91.142.110.20
domain Belkin
search Belkin
[/TD]
[/TR]
[/TABLE]

thanks guys.

---

### Post by weatherman2 on 2015-07-17
Are you sure your router responds to pings?  Can you ping it with other computers?  A quick login to your router to check its configuration to make sure it doesn't have responding to pings disabled (some routers can, as a privacy/security measure) set.

---

### Post by weatherman2 on 2015-07-17
Oh, never mind - saw that you can ping it from other laptops...

---

### Post by shane_2 on 2015-07-17
just tried it with a static ip, im not set up for static ip so it didnt allow me to connect to the web but I could ping my router then! if thats any good.

---

### Post by weatherman2 on 2015-07-17
Can you login to your router and make a DHCP reservation?  Not sure if that would make any difference but worth a try.  That's usually my preferred method of doing static IP vs. setting it directly on the client.

---

### Post by shane_2 on 2015-07-17
just disabled my routers firewall and i can ping it just fine, pretty sure it has to do with just allowing certain machines through either by mac address or ip address.  A bit temperamental but thats life :)

---

