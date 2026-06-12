---
title: "noob can't connect wired with router"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by linuxted on 2007-09-05
I'm really stuck.

When I use my cable modem directly I'm golden

When I connect the cable modem to a Netgear WGR614NA or a Linksys WRT54G and use an ethernet cable to the computer I cannot get a connection.

I've tried 

cd /etc/init.d/
sudo ./networking restart

and get:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 7037
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:5b:47:96:00
Sending on   LPF/eth0/00:11:5b:47:96:00
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:5b:47:96:00
Sending on   LPF/eth0/00:11:5b:47:96:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
ip length 327 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 327 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 35517 seconds.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by noob12 on 2007-09-05
What it looks like is that eth0 actually got an IP address assigned.  You should be connected on your LAN at least.

The error messages are all due to the fact that you also seem to have sections for eth1, eth2, ath0, and wlan0 in your **/etc/network/interfaces** file.  You don't have any such devices.  You can just remove those from the file or comment them out by preceding the lines with #.

There is only one real oddness in the output that might be a sign of a bigger problem
> 
ip length 327 disagrees with bytes received 534.
accepting packet with data after udp payload.

but the output indicates that things proceeded fine anyway.

From the state you showed you should be able to **ping 192.168.1.1**.  If you can get responses, then you are connected on your LAN behind the gateway.  If that works, but you can't get to the internet, first check the configuration and connection status of the router to the net.    Also post the output of these commands on your Ubuntu box:
```

route -n

cat /etc/resolv.conf

```

---

### Post by linuxted on 2007-09-06
> **noob12 said:**
> What it looks like is that eth0 actually got an IP address assigned.  You should be connected on your LAN at least.

The error messages are all due to the fact that you also seem to have sections for eth1, eth2, ath0, and wlan0 in your **/etc/network/interfaces** file.  You don't have any such devices.  You can just remove those from the file or comment them out by preceding the lines with #.

There is only one real oddness in the output that might be a sign of a bigger problem

but the output indicates that things proceeded fine anyway.

From the state you showed you should be able to **ping 192.168.1.1**.  If you can get responses, then you are connected on your LAN behind the gateway.  If that works, but you can't get to the internet, first check the configuration and connection status of the router to the net.    Also post the output of these commands on your Ubuntu box:
```

route -n

cat /etc/resolv.conf

```

Ping is working I think...

64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.421 ms

--- 192.168.1.1 ping statistics ---
21 packets transmitted, 21 received, 0% packet loss, time 20004ms

I'm not sure what this is telling me...

cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search comcast.net


nameserver 192.168.1.1



Thanks

---

### Post by noob12 on 2007-09-06
That indicates you can communicate with the router just fine.

You forgot to post the output of **route -n**.  Please do.

Also, see if you can ping an address on the internet and whether you can resolve a host name.
Try these commands.  Let us know the results.

```

ping 208.67.222.222

host www.yahoo.com

```

---

### Post by linuxted on 2007-09-07
> **noob12 said:**
> That indicates you can communicate with the router just fine.

You forgot to post the output of **route -n**.  Please do.

Also, see if you can ping an address on the internet and whether you can resolve a host name.
Try these commands.  Let us know the results.

```

ping 208.67.222.222

host www.yahoo.com

```

I got the router to work *wired* by resetting it and giong to [www.routerlogin.net](www.routerlogin.net) to reconfigure it!
:guitar:

Now to the next issue... I got a wireless pci adapter and plugged it into the computer to try a wireless connection.  I was hoping it would have just worked instantly (the software that came with it wasn't finding a "C" drive so I lost faith in using the software disk).

What should I do to get the wireless to connect?  I have a Netgear WG311NA

Thank you

---

### Post by noob12 on 2007-09-07
That's another story.  You should start a new thread for that.  People will help; maybe even me; a topic mentioning your WG311NA and wireless is more likely to get an audience that knows something about that.   When you do start your thread, try to include the output of these commands to let people know what you are running and what the hardware is.
```

uname -r

lspci -nn

sudo lshw -C network

```

---

### Post by linuxted on 2007-09-07
> **noob12 said:**
> That's another story.  You should start a new thread for that.  People will help; maybe even me; a topic mentioning your WG311NA and wireless is more likely to get an audience that knows something about that.   When you do start your thread, try to include the output of these commands to let people know what you are running and what the hardware is.
```

uname -r

lspci -nn

sudo lshw -C network

```

Will do.  Thanks for your help up to this point

---

