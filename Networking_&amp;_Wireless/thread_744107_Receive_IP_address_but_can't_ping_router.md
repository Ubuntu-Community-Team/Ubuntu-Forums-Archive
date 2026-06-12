---
title: "Receive IP address but can't ping router"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Thorndeux on 2008-04-03
Hi,

although the title of this thread sounds a lot like the one posted earlier today by mlentink, it is a different problem.

I'll describe the actual problem first and then what I did before it occurred:
On my Ubuntu/XP dual boot machine I can't ping the router from Ubuntu (7.10), although I do get an IP address. Also, I can't ping externally and access the internet. When I boot into XP everything works fine.


ifconfig gives me this:

```
thorn@ubunthorn:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:A4:63:A8  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:264 (264.0 b)  TX bytes:264 (264.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:47:A8:03  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe47:a803/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5547 (5.4 KB)  TX bytes:942 (942.0 b)
          Interrupt:20 Base address:0x4000 
```

So it seems the interface in question gets the IP 192.168.1.3 but when I try to ping the router it says that's not permitted:

```
thorn@ubunthorn:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: [COLOR="Red"]Operation not permitted[/COLOR]
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms
```

So what exatly does not permit the 'operation'? Must be on the Ubuntu side, as it works fine under XP.

I did ifdown/ifup and I don't know what to do with the output:

```
thorn@ubunthorn:~$ sudo ifdown wlan0
[sudo] password for thorn:
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
[COLOR="Red"]There is already a pid file /var/run/dhclient.wlan0.pid with pid 4599[/COLOR]
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:47:a8:03
Sending on   LPF/wlan0/00:11:95:47:a8:03
Sending on   Socket/fallback
[COLOR="Red"]DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Operation not permitted[/COLOR]
thorn@ubunthorn:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:47:a8:03
Sending on   LPF/wlan0/00:11:95:47:a8:03
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
[COLOR="Red"]ip length 314 disagrees with bytes received 534.[/COLOR]
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
[COLOR="Red"]ip length 314 disagrees with bytes received 534.[/COLOR]
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
[COLOR="Red"]bound to 192.168.1.3[/COLOR] -- renewal in 41655 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
```

It seems that ifdown fails to release the IP and I get the same IP from ifup. Still I can't ping the router:
```
thorn@ubunthorn:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: [COLOR="Red"]Operation not permitted[/COLOR]
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2009ms

```


So, if you can help me already, please go ahead - I'm stuck on this one.



Here the background story - might give some additional clues:

I got a new router, a Netgear WGR614 v7, and I configured it on my desktop machine with Gutsy. Everything worked great until I added encryption (WPA2). Ubuntu was mostly unresponsive - I couldn't start any applications (or terminal) and I couldn't shut it down. Thus I pressed the power button.

After this Ubuntu booted fine until the login screen. After login it froze with the background being the default background colour.

I fixed it by removing from /etc/network/interfaces all the WPA2 related stuff. So now, Ubuntu boots fine (although it seems it takes a bit longer as usual) but, as described above, I can't access the web.

---

### Post by chili555 on 2008-04-03
Do you have *both* your ethernet and wireless connected?```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:A4:63:A8  
          inet addr:192.168.1.200
``````
wlan0     Link encap:Ethernet  HWaddr 00:11:95:47:A8:03  
          inet addr:192.168.1.3
```Why? I would fix that first. Disconnect the wire, reboot and then see if the wireless is working as expected.

---

### Post by Thorndeux on 2008-04-03
> **chili555 said:**
> Do you have *both* your ethernet and wireless connected?```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:A4:63:A8  
          inet addr:192.168.1.200
``````
wlan0     Link encap:Ethernet  HWaddr 00:11:95:47:A8:03  
          inet addr:192.168.1.3
```Why? I would fix that first. Disconnect the wire, reboot and then see if the wireless is working as expected.

Thanks for the hint, chili555, but I think you are mistaken. eth0 is not actually connected (not even plugged in - if I was close enough to the router, I'd use it...), I just had static IPs at one point and it's still configured that way.

I've had the static IP like this in the past and there was never a conflict with wifi.

---

### Post by Thorndeux on 2008-04-03
I restarted the router and the modem yet another time and now for some mysterious reason it works!!

---

