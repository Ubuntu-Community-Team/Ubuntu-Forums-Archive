---
title: "Network configuration not working after update"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by gacain on 2017-07-23
Using Ubuntu Server 16.04.2.  After update and reboot, networking is not working.

ifconfig output:

```
root@myserver:~# ifconfig
enp3s0    Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:255.255.252.0
          inet6 addr: xxxx:xxx:xxxx:xxx:xxx:xxxx:xxxx:xxxx/64 Scope:Global
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213420 (213.4 KB)  TX bytes:4632 (4.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:800780 (800.7 KB)  TX bytes:800780 (800.7 KB)
```

Ping output:

```
root@myserver:~# ping google.com
ping: unknown host google.com
```

ifdown/ifup output:

```
root@myserver:~# ifdown enp3s0
ifdown: interface enp3s0 not configured
root@myserver:~# ifup enp3s0
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Corrupt lease file - possible data loss!
Listening on LPF/enp3s0/xx:xx:xx:xx:xx:xx
Sending on   LPF/enp3s0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST of x.x.x.x on enp3s0 to 255.255.255.255 port 67 (xid=0x5a263697)
DHCPACK of x.x.x.x from 192.168.1.254
RTNETLINK answers: File exists
bound to x.x.x.x -- renewal in 288 seconds.
/etc/network/if-up.d/ubuntu-fan: 29: /etc/network/if-up.d/ubuntu-fan: /usr/sbin/fanctl: not found
run-parts: /etc/network/if-up.d/ubuntu-fan exited with return code 127
Failed to bring up enp3s0.
```

This is not a hardware failure, I can get connected by booting from CD.

Any help would be greatly appreciated.

Thank you.

---

### Post by chili555 on 2017-07-23
This line suggests that you are in a private 192.168.x.y network. > DHCPACK of x.x.x.x from 192.168.1.254Frankly, half of the world, including me, is in a private network behind a router; most are in a 192.168.x.y network. There is no security reason to obscure your addresses. On the other hand, it usually helps us to see where your configuration has gone wrong, so please show them going forward.

If this is a server, not running a desktop environment, and therefore not running Network Manager, we assume that the networking is configured in /etc/network/interfaces. May we see it?```
cat /etc/network/interfaces
```

---

### Post by gacain on 2017-07-23
chili555 - thank you for reading and for your response.  

The server (not desktop) is in a DMZ and has a real-world IP.  I would prefer not to publish it.

Output from /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet dhcp

```

Thanks again, very much.

---

### Post by chili555 on 2017-07-23
If you are getting an IP address by DHCP from good old 192.168.1.254, then either it isn't giving out the required DNS namerver addresses, the ones it's giving are improper or DNS and resolvconf are not set up correctly on the computer in question. 

I am surprised that your server is set with DHCP. If the address changes, it is difficult to find and then ssh and ftp into it. 

Can you ping by number?```
ping -c3 74.125.21.99
```I notice this:> Corrupt lease file - possible data loss!You might start fresh by removing the old lease file:```
sudo rm /var/lib/dhcp/client.leases 
```

---

### Post by gacain on 2017-07-23
The server is not getting its IP from the router at 192.168.1.254.  I'm on an AT&T fiber network, the server is getting its IP directly from AT&T's DHCP server.  I'm using dynamic dns to access from outside the LAN.  I don't love this "user friendly" AT&T router at all.  I would much rather the server be behind the firewall with port forwarding.  When I first had the fiber installed, I tried for several hours to get this to work with this router.  I tried port-forwarding in the AT&T router, but when I did that for some reason I couldn't access the server from the LAN.  I tried putting another router in the DMZ, but then I could ONLY access the server from the LAN.  Putting the server in the AT&T router's DMZ was the only way I could get reasonable access to it.  In any case, all this was working before I did the update on the server.

There were actually two dhcp lease files, I deleted them both and rebooted the server.

Output from service networking restart:

```

Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

```

Output from suggested ping:

```

PING 74.125.21.99 (74.125.21.99) 56(84) bytes of data.

--- 74.125.21.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

This was sort of interesting - I issued this command 3 or 4 times, and each time it tried to send 3 packets, then hung.

Again, many thanks for helping me with this.

---

### Post by chili555 on 2017-07-23
> The server is not getting its IP from the router at 192.168.1.254. But yet you said:> root@myserver:~# ifdown enp3s0
ifdown: interface enp3s0 not configured
root@myserver:~# ifup enp3s0
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Corrupt lease file - possible data loss!
Listening on LPF/enp3s0/xx:xx:xx:xx:xx:xx
Sending on   LPF/enp3s0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST of x.x.x.x on enp3s0 to 255.255.255.255 port 67 (xid=0x5a263697)
[COLOR="#FF0000"]DHCPACK of x.x.x.x from 192.168.1.254[/COLOR]
RTNETLINK answers: File exists
bound to x.x.x.x -- renewal in 288 seconds.
/etc/network/if-up.d/ubuntu-fan: 29: /etc/network/if-up.d/ubuntu-fan: /usr/sbin/fanctl: not found
run-parts: /etc/network/if-up.d/ubuntu-fan exited with return code 127
Failed to bring up enp3s0.Isn't 192.168.1.254 the gateway address of the AT&T router? Doesn't it give a 192.168.1.xyz address? I think I understand the DHCP in the server as the AT&T device likely doesn't permit static addresses. Yes?

I am very concerned about these symptoms:> Failed to bring up enp3s0And:> Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.And:> ping: sendmsg: Operation not permittedWhat does the message say?```
systemctl status networking.service
```Is this an iptables or other firewall issue? [https://serverfault.com/questions/372975/ping-sendmsg-operation-not-permitted-error-after-installing-iptables-on-arch-g](https://serverfault.com/questions/372975/ping-sendmsg-operation-not-permitted-error-after-installing-iptables-on-arch-g)

By the way, I am very familiar with:>  I'm on an AT&T fiber network,
....
 I don't love this "user friendly" AT&T router at all. I have and use a similar setup myself. In my case, a 5268AC. I have a router behind it.

---

### Post by gacain on 2017-07-23
Once again, thank you for your response.

I'm using that same router.

As I said, I don't believe I'm using an optimal setup, but this was the only way I could get everything working.  I tried doing what you are doing, with my own (Netgear) router behind the AT&T router, but no joy.  I'm not new to networking, but I'm new to AT&T, and things don't seem to work as expected here.  It may be that I have a defective router.

All that said, the system DOES work perfectly when I'm using the "Repair a broken system" option from the server boot/install CD, but NOT when I'm booting from the hard drive, so I don't think this is an issue with the way I have the router/LAN set up.

I'm going to look at the firewall settings per your advice when I have a little more time later today.  Along these lines, I'm using UFW for firewalling, and I've just noticed that it is failing to start when I boot the server, and will not start from the CLI.

Thanks again.

---

### Post by gacain on 2017-07-24
chili555 - as always, thank you for your response.

This evening, based on your recommendation, I had a look a the whole firewall situation on this server, especially looking into why ufw was not working.  It was looking for /etc/ufw/user.rules, and not finding it.  I went to that directory and found the file user6.rules, which I decided to copy to user.rules.  Bingo - everything solved.

I'm going to revisit the idea of getting this server behind the hardware firewall, where I want it to be.  

In the meantime, many, many thanks for your patience and diligence in helping me get to the solution.

---

