---
title: "Cannot Get Network Setting via DHCP"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by mayliszt on 2007-03-27
Since yesterday, I cannot get network setting via DHCP.
It suddenly did not work after I left the computer aside for a while, so I cannot find the reason.
Though I updated my ubuntu, but this is not the reason, because it still worked after the updating.

Now I have to get an IP with my Windows XP and then assign it as a static IP to my ubuntu.

Can any one give me any suggestion?

Here are my diagnose:
Hard ware is fine, and DHCP sever is working fine, because my Windows XP can get IP from it.
Network card driver is fine, because static IP still works.

The problem seems to be the communication with DHCP server.

Is it because of this message of /etc/init.d/networking restart ?
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416

------------------  /etc/init.d/networking restart ------------------------
root@junningl-laptop:/etc/network# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 14958
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:7d:e3:a5
Sending on   LPF/eth0/00:15:58:7d:e3:a5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 142.103.1.1 port 67
Ignoring unknown interface eth1=eth1.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

--------/etc/networking/interfaces----------

auto eth0
iface eth0 inet dhcp


------------------- ifconfig eth0 -------------------
eth0      Link encap:Ethernet  HWaddr 00:15:58:7D:E3:A5  
          inet addr:128.189.137.146  Bcast:128.189.137.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe7d:e3a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:21696 txqueuelen:10 
          RX bytes:127417487 (121.5 MiB)  TX bytes:5864266 (5.5 MiB)
          Base address:0x3000 Memory:ee000000-ee020000

---

### Post by Hortinstein on 2007-03-27
your lucky...the only traffic i can get working is DCHP...

---

### Post by Mr. C. on 2007-03-28
This is curious:

```
Ignoring unknown interface eth1=eth1.
```

But this is very bad:

```
collisions:21696
```

Your system should not be getting so many Ethernet collisions.

Can you describe your networking setup (eg. router/modem, other PCs, switches, hubs) ?

You cannot take the IP address assigned dynamically to Windows XP.  Upon shutdown, Windows releases this address back to the DHCP server.  It is no longer yours until your DHCP client requests and is granted its use.  Don't assign it statically.. let's fix the root of the problem.

MrC

---

### Post by mayliszt on 2007-03-28
Thank you very much, MrC, for answering my post.

------------------
Ignoring unknown interface eth1=eth1.
-------------------
-> I have the device eth1, but I delete it from the file interfaces because I never use it.

-------------------
collisions:21696
-------------------
-> I have no idea about this.

My hardware:
    IBM T60, intel network card,
    internet: I use LAN in my dorm.
    Everything works fine before.

    My Windows XP setting is dynamic IP.
    I tried to solve the problem by changing the interfaces file and then running the /etc/init.d/networking restart command.

---

### Post by mayliszt on 2007-03-28
MrC, below is a new try after changing to dhcp:
----- interfaces file -----
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

# I have no idea why I have so many devices.
# I have a wireless card, a wired card and a moderm.
# Actually I am only interested in eth0

------ message of networking restart -------
root@junningl-laptop:/etc/network# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                               There is already a pid file /var/run/dhclient.eth0.pid with pid 6278
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:7d:e3:a5
Sending on   LPF/eth0/00:15:58:7d:e3:a5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 142.103.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 6561
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:ca:7e:d7
Sending on   LPF/eth1/00:18:de:ca:7e:d7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.30 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:7d:e3:a5
Sending on   LPF/eth0/00:15:58:7d:e3:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 128.189.137.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 128.189.137.254
bound to 128.189.137.146 -- renewal in 288136 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:de:ca:7e:d7
Sending on   LPF/eth1/00:18:de:ca:7e:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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

### Post by Mr. C. on 2007-03-28
Sorry for the delayed reply.

In System->Administration->Network, disable all devices except eth0.

Once done, close the dialog, and in a Terminal window, restart your network:

```
/etc/init.d/networking restart
```

See if this resolves the issue.

After some network activity, please check

```
ifconfig eth0
```

and look for those collisions.

MrC

---

### Post by mayliszt on 2007-03-29
Thanks, MrC.
It seems it does not work.

I get the IP. Though it is always 128.189.137.146, I think it is ok.
But I still cannot use the network because
(1) the collision is still there.
(2) the gateway does not allow me to go out. I pinged the gateway, but I got "Packet filtered". BTW, I can ping my neighbors.

I think maybe there two possible reasons:
(1) nothing is wrong with my computer. It is the problem of the network. Some one illegally assigned himself the IP I got, so there are collisions.
(2) My computer has problem with talking to the DHCP, so actually it did not get a IP from DHCP but always uses the old IP though it seems it tried to talk with DHCP.

BTW, my wireless can use DHCP without any problem.


############ network restart ###########
root@junningl-laptop:/etc/network# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:58:7d:e3:a5
Sending on   LPF/eth0/00:15:58:7d:e3:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 128.189.137.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 128.189.137.254
bound to 128.189.137.146 -- renewal in 281837 seconds.
                                                                                                                      [ ok ]
############ ifconfig ###################3
root@junningl-laptop:/etc/network# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:15:58:7D:E3:A5  
          inet addr:128.189.137.146  Bcast:128.189.137.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe7d:e3a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:682362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8492 txqueuelen:10 
          RX bytes:66970652 (63.8 MiB)  TX bytes:4601565 (4.3 MiB)
          Base address:0x3000 Memory:ee000000-ee020000 

root@junningl-laptop:/etc/network# ping [www.google.ca](www.google.ca)

############ Ping the gateway #########
root@junningl-laptop:/etc/network# ping 128.189.137.254
PING 128.189.137.254 (128.189.137.254) 56(84) bytes of data.
From 128.189.137.254 icmp_seq=1 Packet filtered
From 128.189.137.254 icmp_seq=2 Packet filtered
From 128.189.137.254 icmp_seq=3 Packet filtered
From 128.189.137.254 icmp_seq=4 Packet filtered

--- 128.189.137.254 ping statistics ---
8 packets transmitted, 0 received, +4 errors, 100% packet loss, time 7004ms

######### ping my neighbor
root@junningl-laptop:/etc/network# ping 128.189.137.148
PING 128.189.137.148 (128.189.137.148) 56(84) bytes of data.
64 bytes from 128.189.137.148: icmp_seq=1 ttl=64 time=2.48 ms
64 bytes from 128.189.137.148: icmp_seq=2 ttl=64 time=0.712 ms
64 bytes from 128.189.137.148: icmp_seq=3 ttl=64 time=0.700 ms

--- 128.189.137.148 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.700/1.299/2.486/0.839 ms

---

### Post by Mr. C. on 2007-03-29
Ok, you do have an IP address, and it appears to be valid.  If DHCP fails, you get no address, not an old one.  The system has no memory of old IP addresses.  The fact that you always get the same IP is another indication that DHCP is working correctly.  DHCP servers attempt to reassign the same IP address if they are able (actually, your system requested it).

The collisions may simply be a matter of how your network is configured (are you using a hub?).

If someone using the same IP address as you, the problems will be much more severe, and obvious.  Collisions on ethernet are normal when no switches are involved (again, this is why I ask if you have a hub).

Packet filtered is not necessarily a problem.  If ping to any other remote address works, your network is functional.

So, it appears that your internet connection is fine.  I'm not sure what additional probelms you are experiencing.  Please explain.

Also, just to be one step ahead, please show the output from:

```
cat /etc/resolv.conf
ping 17.254.3.183
nslookup apple.com
```

MrC

---

### Post by Mooie on 2007-03-29
I have a friend whos laptop i am trying to get set up wireless so he can get online. He is getting this too, he uses a prism 2.5 miniPCI card, and i think its recognized now, but it wont pick up his router. when he runs "sudo dhclient eth0" it returns this:
> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:b5:26:53
Sending on LPF/eth1/00:0e:35:b5:26:53
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in  persistent database - sleeping.

---

### Post by Mr. C. on 2007-03-29
Please don't hijack someone else's thread.  Responses become too confusing, and in the end, no help is gained.

I personally have a policy to not provide assistance in hijacked threads.  I'll be glad to help in another thread.

MrC

---

### Post by mayliszt on 2007-03-29
I myself do not use hub or router.
I just plug the cable in the port in my dorm.
But I am not sure how our network is built.

Below is the out put of the run
-------------------------------------------------------
root@junningl-laptop:/etc/network# cat /etc/resolv.conf 
search resnet.ubc.ca.
nameserver 137.82.1.1
nameserver 142.103.1.1
root@junningl-laptop:/etc/network# ping 17.254.3.183
PING 17.254.3.183 (17.254.3.183) 56(84) bytes of data.
From 128.189.137.254 icmp_seq=3 Packet filtered
From 128.189.137.254 icmp_seq=4 Packet filtered
From 128.189.137.254 icmp_seq=5 Packet filtered
From 128.189.137.254 icmp_seq=14 Packet filtered
From 128.189.137.254 icmp_seq=15 Packet filtered
From 128.189.137.254 icmp_seq=16 Packet filtered
From 128.189.137.254 icmp_seq=17 Packet filtered
From 128.189.137.254 icmp_seq=18 Packet filtered
From 128.189.137.254 icmp_seq=19 Packet filtered
#### 128.189.137.254 is the gateway

--- 17.254.3.183 ping statistics ---
21 packets transmitted, 0 received, +9 errors, 100% packet loss, time 20010ms

root@junningl-laptop:/etc/network# nslookup apple.com
;; connection timed out; no servers could be reached

---

### Post by Mr. C. on 2007-03-29
Ok, likely your dorm (or other) does not have switches to each room, and you are all under one "collision domain".  This is a very old way to use ethernet.  Today, it is a switchport to each desktop.

Short of talking to your IT guys there who manager your area, there won't be much you can do about collisions.  A few is fine.  But when there are excessive numbers, your networking will be slowed considerably.

Hub's dont protect against other listeners on the same hub, so beware.

MrC

---

### Post by mayliszt on 2007-03-30
Thank you very much Mr. C., for this marathon diagnose.
Best wishes to you.

---

### Post by Mr. C. on 2007-03-30
You're welcome.

Spend a few of those hard-earned $$$ and pick yourself up a cheap firewall/router/switch.  You will likely see better performance, and will have significantly better security.

Best of luck,
MrC

---

