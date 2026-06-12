---
title: "Trouble loading webpages"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by victoria6 on 2014-05-19
I am running Ubuntu 13.10 and cannot load webpages and do other tasks involving the internet. In the panel it says it is connected to the internet, but I can't load webpages in either Chromium or Firefox, download things in Software Center, and so on.

---

### Post by lz1dsb on 2014-05-20
Do you use any proxy in your network?

---

### Post by victoria6 on 2014-05-20
I don't believe so...

---

### Post by grahammechanical on 2014-05-20
When Network Manager says that Ubuntu is connected it means that Ubuntu is connected to the router. Is the router connected to the Internet Service Provider (ISP)? When you load Ubuntu do you get a message that says something about Avahi being disabled because Ubuntu is on a local domain? That message will appear when Ubuntu connects to the router and the router is not connected to the ISP. Please confirm that the router is connected to the ISP and on to the Internet.

Regards.

---

### Post by victoria6 on 2014-05-20
I don't get that message, and am able to connect to the internet on other computers, so I think the router is okay.

---

### Post by varunendra on 2014-05-21
Hi again, looks like we are in for another joy ride.. (yeah, I remember that rtl8723ae trouble..)

When it appears to be connected, please post back the outputs of -
```
route -n
ifconfig -a
nm-tool
ping -c2 google.com
```
..and can you ping the IP of your router/gateway?

---

### Post by victoria6 on 2014-05-21
Good to see you again! I guess we're in for another ride of Ubuntu not liking me or my internet. :-p

I attached what those commands gave me.

I'm not sure what you mean by ping the IP for my router/gateway...

---

### Post by SeijiSensei on 2014-05-21
It doesn't appear that your router is giving you a DNS server.  Try running these commands:
```
host www.google.com 10.0.1.1
host www.google.com 8.8.8.8
```
The first tries to use your router as a DNS server.  Most home and small office routers are configured to work as a DNS server by default.  The second command makes the same query using Google's public nameserver at 8.8.8.8.  Do either or both of these commands work for you?

---

### Post by victoria6 on 2014-05-21
This is what I get 

```
$ host [www.google.com]("http://www.google.com") 10.0.1.1
Using domain server:
Name: 10.0.1.1
Address: 10.0.1.1#53
Aliases: 


[www.google.com]("http://www.google.com") has address 74.125.228.211
[www.google.com]("http://www.google.com") has address 74.125.228.209
[www.google.com]("http://www.google.com") has address 74.125.228.212
[www.google.com]("http://www.google.com") has address 74.125.228.208
[www.google.com]("http://www.google.com") has address 74.125.228.210
[www.google.com]("http://www.google.com") has IPv6 address 2607:f8b0:4004:806::1011
$ host [www.google.com]("http://www.google.com") 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 


[www.google.com]("http://www.google.com") has address 167.206.145.153
[www.google.com]("http://www.google.com") has address 167.206.145.172
[www.google.com]("http://www.google.com") has address 167.206.145.162
[www.google.com]("http://www.google.com") has address 167.206.145.177
[www.google.com]("http://www.google.com") has address 167.206.145.158
[www.google.com]("http://www.google.com") has address 167.206.145.163
[www.google.com]("http://www.google.com") has address 167.206.145.157
[www.google.com]("http://www.google.com") has address 167.206.145.182
[www.google.com]("http://www.google.com") has address 167.206.145.173
[www.google.com]("http://www.google.com") has address 167.206.145.183
[www.google.com]("http://www.google.com") has address 167.206.145.178
[www.google.com]("http://www.google.com") has address 167.206.145.168
[www.google.com]("http://www.google.com") has address 167.206.145.187
[www.google.com]("http://www.google.com") has address 167.206.145.167
[www.google.com]("http://www.google.com") has address 167.206.145.152
[www.google.com]("http://www.google.com") has address 167.206.145.148
[www.google.com]("http://www.google.com") has IPv6 address 2607:f8b0:4006:807::1013
```

And it still doesn't connect on Chromium.

I'm not sure if that means it worked or not.

---

### Post by varunendra on 2014-05-22
What are the outputs of :
```
ping -c2 10.0.1.1
ping -c2 8.8.8.8
```

And it seems you have set the DNS servers (10.0.1.1 and 8.8.8.8) manually in Network Manager. Can you change it to 8.8.8.8 and 8.8.4.4 ? (to be entered as (without quotes) : "8.8.8.8, 8.8.4.4" in Network Manager's IPv4 settings for the wireless connection.)

You may have to restart networking (command : "sudo service networking restart") or reboot the computer to let the change take effect immediately.

---

### Post by SeijiSensei on 2014-05-22
> **varunendra said:**
> And it seems you have set the DNS servers (10.0.1.1 and 8.8.8.8) manually in Network Manager.

I don't think her DNS servers are set anywhere.  My guess is that her router isn't providing a DNS server during the DHCP handshake.

Victoria, if you can use your router's management software, see if its DHCP server settings include one or more DNS servers.  You can use 10.0.1.1 as the primary with 8.8.8.8 as the backup.

If that doesn't work, you can specify the servers manually like this.  Open the file /etc/resolvconf/resolv.conf.d/head with an editor as root with sudo, then add these two lines to that file:
```

nameserver 10.0.1.1
nameserver 8.8.8.8

```
This will set these as your nameservers in the future.  If you are on your local network, your machine will use 10.0.1.1.  If you're travelling, it will use 8.8.8.8.

---

### Post by varunendra on 2014-05-22
> **SeijiSensei said:**
> I don't think her DNS servers are set anywhere.  My guess is that her router isn't providing a DNS server during the DHCP handshake.

The nm-tool outputs show those DNS servers, which means the Network Manager has got them from somewhere, either from DHCP, or from manual configuration in NM gui.

Usually, unless explicitly defined in DHCP settings of the router, nm-tool reports just one DNS (the gateway itself) if acquired from DHCP. The router (gateway) then takes care of DNS request forwarding. Since there are two DNS servers defined, one being google's (as per "nm-tool" output), they must have been defined manually either in NM gui, or in the DHCP settings of the router. NM is just more likely. :)

Of course whatever nm-tool reports doesn't matter if the interface is being controlled by the /etc/network/interfaces file. But so far I am assuming we are dealing with default methods.

@ victoria6,
Talking of defaults, please also show us the outputs of (if the problem persists even after trying what I or SeijiSensei suggested) -
```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by victoria6 on 2014-05-22
"sudo service networking restart" totally crashed Ubuntu. It got really glitchy and I force restarted and then Ubuntu wouldn't load, so I restarted again and it works. Well I mean, Ubuntu isn't dead, 'cause I got really worried there for a second. :S But webpages still don't load.

```
$ ping -c2 10.0.1.1PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
64 bytes from 10.0.1.1: icmp_seq=1 ttl=255 time=9.08 ms
64 bytes from 10.0.1.1: icmp_seq=2 ttl=255 time=6.54 ms


--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 6.545/7.816/9.088/1.274 ms
$ ping -c2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=42 time=37.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=42 time=112 ms


--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 37.007/74.786/112.566/37.780 ms
```

```


$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
```

---

### Post by varunendra on 2014-05-23
Have you tried what SeijiSensei suggested? That is -
> **SeijiSensei said:**
> If that doesn't work, you can specify the servers manually like this.  Open the file /etc/resolvconf/resolv.conf.d/head with an editor as root with sudo, then add these two lines to that file:
```

nameserver 10.0.1.1
nameserver 8.8.8.8

```
This will set these as your nameservers in the future.  If you are on your local network, your machine will use 10.0.1.1.  If you're travelling, it will use 8.8.8.8.

If that doesn't work, I'd suggest removing the '10.0...' line altogether, and replace the lines with -
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
If you can ping these IP addresses, there is no reason why you shouldn't be able to browse internet unless you have enabled some proxy settings or a firewall is preventing you.

If none of these helps, time to dig deeper - please follow this post to download and run a new (experimental) version of 'wireless_script', and post back its report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

