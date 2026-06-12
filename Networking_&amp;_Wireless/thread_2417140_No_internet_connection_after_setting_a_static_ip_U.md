---
title: "No internet connection after setting a static ip Ubuntu 18.04"
date: 2019-04-21
forum: Networking &amp; Wireless
---

### Post by wantedstarling on 2019-04-21
Hello, I am trying to set a static ip on my Ubuntu Desktop installed on Virtualbox. My settings are:

```
[FONT=Verdana]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
[/FONT]
[FONT=Verdana]auto enp0s3
iface enp0s3 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 8.8.8.8 192.168.2.1[/FONT]

```

If I run ifconfig I get this:

```
[FONT=Verdana]gm@gm-VirtualBox:~$ ifconfig
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.100  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::a00:27ff:fed7:4618  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:d7:46:18  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 76  bytes 8261 (8.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]
[FONT=Verdana]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 117  bytes 9195 (9.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 117  bytes 9195 (9.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT]


```

The IP is set but no connection, if I ping to 192.168.2.1 which is my gateway I get a reply. On every post I saw around the internet I read I have to set a dns after version 12 which I did but still no connection. Note, as I mentioned above I am running Ubuntu on VirtualBox and I changed the settings from NAT to Bridged adapter, hope this doesn't cause any problem.

Thank you for your time

---

### Post by SeijiSensei on 2019-04-21
If you can ping the gateway, then you have a connection. What happens if you try to ping 8.8.8.8?

---

### Post by wantedstarling on 2019-04-21
I also get a reply from there too

```

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]64 bytes from 8.8.8.8: icmp_seq=1 ttl=119 time=266 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=119 time=141 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=119 time=281 ms
[/FONT]
```

---

### Post by SeijiSensei on 2019-04-21
Then you probably have a DNS problem.  Try this temporary fix.  Move /etc/resolv.conf to /etc/resolv.conf.disabled.  Then create a new /etc/resolv.conf with an editor like this:

```
nameserver 8.8.8.8
```

You'll need to do all this with root privileges via sudo.

Now try pinging something by name like "ping www.google.com".  Any better?

Those are some pretty poor ping times, by the way. On my desktop machine (with Verizon FiOS) I get
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=122 time=14.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=122 time=16.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=122 time=16.9 ms

```

The times you're getting are more akin to what people got back in the days of modem connections.  Once you get things sorted out, try running a test at speedtest.net.

DNS resolution has been a moving target with Ubuntu for the past few years. Make sure you're using instructions specifically for 18.04.  The most reliable method is to configure your router to send the DNS server IPs via the router's DHCP server rather than specifying them manually.  Since the connection is bridged, you should get the same DNS servers for the VB guest as you do for the VB host.

---

### Post by wantedstarling on 2019-04-21
[LEFT][COLOR=#222222][FONT=Verdana]For the ms you saw on my ping request, It was because I was downloading in the background, stopped it and ms dropped to 30 approximately. Anyway, I created the new resolv.conf with only 8.8.8.8 in it, restarted, tried to ping and got [/FONT][/COLOR]```
[COLOR=#222222][FONT=Verdana]ping [www.google.com:]("http://www.google.com/") Name or service not known[/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana] I will restore back with the snapshot I kept. About the instructions you said, I am watching a guide for Ubuntu 14.04 and thought it would be the same process, I am trying to make a server for zimbra.[/FONT][/COLOR][/LEFT]

---

### Post by SeijiSensei on 2019-04-21
First, I'd remove the static configuration and see if you can set up your router to give your machine the 192.168.2.100 address. Usually this is done with a "reservation" in the DHCP server. Then let the DHCP server manage everything.

Name resolution in 18.04 is not the same as it was for 14.04.

In 18.04, go to /etc/resolvconf/resolv.conf.d/ and edit the file called "head". Put the "nameserver 8.8.8.8" entry in that file then restart.  When resolvconf builds /etc/resolv.conf again it will put that line above any other nameserver entries.

Note that this won't work in 19.04 (or 18.10, I believe) which use systemd-resolved rather than resolvconf. Since 18.04 has long-term support, you won't want to change from that anyway if you're building a server.

As I said, DNS resolution in Ubuntu has been a moving target for the past couple of years.

Good luck with [Zimbra](https://www.youtube.com/watch?v=gA08bGxmkNk)!

---

