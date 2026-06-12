---
title: "No dhcp leases offered by dnsmasq when I try to configure what I want."
date: 2024-01-06
forum: Networking &amp; Wireless
---

### Post by 0cs935-bill on 2024-01-06
This is on a fully patched Ubuntu 22.04LTS.

This concerns dnsmasq **when it is a subsystem to NetworkManager**. It's apparently completely different than if dnsmasq is run stand alone.

I'm attempting to get dhcp working from dnsmasq when it is automatically started from the NetworkManager system. It took me a while to realize that dnsmasq was not taking it's configuration from where the dnsmasq documentation says it will, from /etc/dnsmasq.d . A _man NetworkManager.conf_ explains it takes its instructions from /etc/NetworkManager/dnsmasq.d and never mentions there's a second location that apparently is used also or instead of, /etc/NetworkManager/dnsmasq-shared.d .

Without any conf file anywhere, I get this via journalctl:
Jan 06 06:04:25 zima.private.ycc dnsmasq-dhcp[1235]: DHCP, IP range 192.168.2.10 -- 192.168.2.254, lease time 1h


When I put my conf file into /etc/NetworkManager/dnsmasq.d, it was completely ignored because here is what I get via journalctl:
Jan 06 06:09:55 zima.private.ycc dnsmasq-dhcp[1685]: DHCP, IP range 192.168.2.10 -- 192.168.2.254, lease time 1h
It was only when I moved that conf file into /etc/NetworkManager/dnsmasq-shared.d that I got any indication that it was listening to me.


Here is the entirety of my dnsmasq.conf file. As can be seen, I've commented major portions out for testing.
```
log-dhcp
port=0
domain-needed 
bogus-priv
interface=wlp1s0
domain=private.ycc
dhcp-range=192.168.2.50,192.168.2.254,255.255.255.0,12h
#dhcp-range=192.168.2.2,static
#dhcp-range=192.168.2.3,static
#dhcp-range=192.168.2.4,static
#dhcp-range=192.168.2.5,static
#dhcp-range=192.168.2.6,static
#dhcp-range=192.168.2.7,static
#dhcp-range=192.168.2.8,static
#dhcp-range=192.168.2.9,static
#dhcp-host=D4:62:EA:7B:E8:42,billhuawei.private.ycc,192.168.2.2,infinite  
#dhcp-host=7C:6C:F0:47:21:9B,janetphone.private.ycc,192.168.2.3,infinite  
#dhcp-host=24:C6:13:4F:F1:B9,billtablet.private.ycc,192.168.2.4,infinite  
#dhcp-host=24:F0:C3:0C:3F:C9,janettablet.private.ycc,192.168.2.5,infinite  
#dhcp-host=F8:A9:A0:4A:BA:08,janetnexus.private.ycc,192.168.2.6,infinite  
#dhcp-host=50:2C:C6:2B:26:32,gree.private.ycc,192.168.2.7,infinite
```


When I have the conf file only in the /etc/NetworkManager/dnsmasq-shared.d and nothing in /etc/NetworkManager/dnsmasq.d, this is what I get via journalctl:
Jan 06 06:21:25 zima.private.ycc dnsmasq-dhcp[1186]: DHCP, IP range 192.168.2.50 -- 192.168.2.254, lease time 12h
Jan 06 06:21:25 zima.private.ycc dnsmasq-dhcp[1186]: DHCP, IP range 192.168.2.10 -- 192.168.2.254, lease time 1h
Jan 06 06:21:25 zima.private.ycc dnsmasq-dhcp[1186]: DHCP, sockets bound exclusively to interface wlp1s0


When I put the exact same conf file also into /etc/NetworkManager/dnsmasq.d, this is what I get via journalctl:
Jan 06 06:49:35 zima.private.ycc dnsmasq-dhcp[1185]: DHCP, IP range 192.168.2.50 -- 192.168.2.254, lease time 12h
Jan 06 06:49:35 zima.private.ycc dnsmasq-dhcp[1185]: DHCP, IP range 192.168.2.10 -- 192.168.2.254, lease time 1h
Jan 06 06:49:35 zima.private.ycc dnsmasq-dhcp[1185]: DHCP, sockets bound exclusively to interface wlp1s0


For some reason, it insists on an overlapping range no matter what I do. Either way, dhcp isn't working. 


When an Ubuntu box tries to get a connection, the connection is made without the dhcp lease. On Android units, the entire connection fails probably because it can't get a dhcp lease.


Does anyone know how to set dnsmasq up **when it's in a NetworkManager environment**? The documentation for this is wrong or nonexistent.

---

### Post by 0cs935-bill on 2024-01-06
Discovered a bit of information from this article at [https://copyprogramming.com/howto/using-dnsmasq-with-networkmanager:](https://copyprogramming.com/howto/using-dnsmasq-with-networkmanager:)
> Contrary to claims made here and elsewhere, NetworkManager disregards all dnsmasq configuration files, including those located in its own directory. This can be verified by examining the source code of NetworkManager, where a relevant comment can be found.


 To prevent undesirable side-effects such as sending bogus IP addresses as the gateway, it is important to ensure that dnsmasq does not use any config file, especially if the default config file location is valid and combined with the provided options. 
 
Also discovered where the phantom dhcp range is coming from; it's hard coded on the command line:
```
root@ha:~# ps -ef|grep masq
nobody      3323    3278  0 10:43 ?        00:00:00 /usr/sbin/dnsmasq --conf-file=/dev/null --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=192.168.3.1 --dhcp-range=192.168.3.10,192.168.3.254,60m --dhcp-lease-max=50 --dhcp-leasefile=/var/lib/NetworkManager/dnsmasq-wlp3s0.leases --pid-file=/run/nm-dnsmasq-wlp3s0.pid --conf-dir=/etc/NetworkManager/dnsmasq-shared.d

```

That command line also shows that it will read config information from /etc/NetworkManager/dnsmasq-shared.d despite what the article claimed and is why I get what I want but then it's stepped on by the command line rubish.


I guess the solution is to dump NetworkManager since it's brain damaged.

---

### Post by #&amp;thj^% on 2024-01-06
I wonder though if this would be enough for your testing:
```
sudo killall -STOP NetworkManager
```
this will stop NetworkManager running and auto-scanning.
if needed you can re-enable it with:
```
sudo killall -CONT NetworkManager 
```
This has been an interesting go round.

---

### Post by 0cs935-bill on 2024-01-06
I've tried various things including killing NM, but everything I tried has one or more gotchas. I'm moving on.

Netplan is where things are heading even for desktop so I'm currently downloading Ubuntu Server 22.04.3 and when my humongously speedy 1mBps internet connection finally allows ( I only get a fraction of that) I'm also downloading Ubuntu 23.10 desktop that already uses Netplan. From reading, I gather that NetworkManager is still around but I'm hoping I can configure what I need by slapping it upside the head via the higher order of control offered by Netplan. 

Once I discovered that they hardcoded information on a command line with no access to a configuration file && that their documentation flat out lies && that I've spent many long days chasing this phantom, I resigned to have a beer, fight the desire to throw things and move on. The absolute worst thing about Linux is that the documentation sucks.

---

### Post by #&amp;thj^% on 2024-01-06
Yep I agree I just did it myself to no avail. 
I couldn't agree more on "The absolute worst thing about Linux is that the documentation sucks. " 
Save A Beer for me would ya? LOL

---

### Post by 0cs935-bill on 2024-01-06
I had my beer and then I drank yours.:lolflag:

---

### Post by #&amp;thj^% on 2024-01-06
;)

---

