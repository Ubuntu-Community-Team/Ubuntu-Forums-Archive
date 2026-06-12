---
title: "dhcp bind9 gateway server broken after upgrading to 20.04LTS"
date: 2020-11-30
forum: Networking &amp; Wireless
---

### Post by adam-hardy on 2020-11-30
I run an ubuntu server to act as the internet gateway for my small office / home server and by upgrading from ubuntu 18 to 20.04LTS I have crocked it. I now only have internet access via the actual server, but not for any dhcp clients. 

At least problems 2 cropped up due to the upgrade which I have discovered. 

Firstly my [FONT=courier new]iptables[/FONT] setup broke, which I've now fixed (the iptables command moved from [FONT=courier new]/sbin[/FONT] to [FONT=courier new]/usr/sbin[/FONT])

Secondly, the [FONT=courier new]bind9[/FONT] config broke, I'm not sure why the new bind9 didn't like my old config, but I have ironed out the issue.

Obviously though there is still something wrong.

A dhcp client, e.g. my laptop, can retrieve an IP address, gateway and nameserver, but can't surf the net. When I try to ping internet hosts from the client, it fails with "Destination Host Unreachable". I assume that somehow, my server is blocking the client, but I have run out of ideas to fix it now. 

Where should I investigate now?

iptables? bind9? isc-dhcp-server? ppp?

I'm tempted to provide a tsunami of config files now but I guess the answer will lie in the output of various diagnostic commands.

All help gratefully received ](*,)

---

### Post by SeijiSensei on 2020-11-30
Give a client a static IP address in the range managed by the router. Does that work?

Open a browser on a client and point it to an IP address. You can use [http://45.79.217.116/](http://45.79.217.116/), a server I maintain if you like. You should get the Apache test page. If that works, you have a DNS-resolution issue.

Make sure there is either a MASQUERADE or an SNAT rule in the "nat" table in your iptables ruleset.  Run the command
```
sudo iptables -t nat -L -nv
```
to make sure.

PPP? Is this machine on a dialup connection of some kind?

---

### Post by adam-hardy on 2020-11-30
Yes, you nailed it \\:D/   

A static IP address works. 

I'm not so sure about [FONT=courier new]iptables[/FONT] - I only every touch it about once a year and my memory of actually setting it up is sketchy to say the least. Your command produces this:

```
adam@gondolin:~$ sudo iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 5161 packets, 548K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 2024 packets, 252K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 10421 packets, 783K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 10421 packets, 783K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2390  264K MASQUERADE  all  --  *      ppp0    192.168.0.0/24       0.0.0.0/0           
adam@gondolin:~$ 

```

Is that postrouting rule enough? I mean, this script always has worked with only minor modifications ever necessary.

[FONT=courier new]ppp[/FONT] is the protocol that sets up the broadband connection with the dsl modem. I never understood it, it always just worked. It somehow creates its own interface based on the NIC it's attached to - [FONT=courier new]enp5s0[/FONT] - like this:

```

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.10  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::e2d5:5eff:fead:b027  prefixlen 64  scopeid 0x20<link>
        ether e0:d5:5e:ad:b0:27  txqueuelen 1000  (Ethernet)
        RX packets 440848  bytes 442179661 (442.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 321922  bytes 59040287 (59.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf7200000-f721ffff  

ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1472
        inet xxx.xxx.xxx.xxx  netmask 255.255.255.255  destination xxx.xx.11.38
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 434619  bytes 431974248 (431.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 318415  bytes 51910323 (51.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Again like [FONT=courier new]iptables[/FONT], it's always worked.

So if it is a DNS issue, that points to [FONT=courier new]bind9[/FONT] - or something else?

---

### Post by SeijiSensei on 2020-11-30
You specify the DNS servers that the clients should use in dhcpd.conf. Is there a reason you're running your own copy of BIND9? Unless you have your own domain and need to manage its zone files, I don't see much value in running it on your router. I'd just have dhcpd hand out the DNS servers that your provider offers. Or you can use the Google servers at 8.8.8.8 and 8.8.4.4 or Cloudflare's at 1.1.1.1. There are other [free DNS servers]("https://www.allconnect.com/blog/best-free-dns-servers") out there, too.

If you don't have a domain, is your BIND9 installation set up to be a "caching nameserver?" Maybe this will help: [https://blog.suenotek.com/post/bind9-caching-dns-server-on-ubuntu-20-04-lts-or-ubuntu-18-04-lts/](https://blog.suenotek.com/post/bind9-caching-dns-server-on-ubuntu-20-04-lts-or-ubuntu-18-04-lts/)

The masquerading rule looks fine. Do you block any traffic on the "LAN" side of the router?  You need to let the clients talk to port 53 via UDP in order to resolve names if you're running BIND9. You should have a rule like
```
iptables -A INPUT -i enp5s0 -p udp --dport 53 -j ACCEPT
```
or possibly
```
iptables -A INPUT -s 192.168.2.0/24 -p udp --dport 53 -j ACCEPT
```
Of course that would only matter if you block traffic from your local network. If all your rules are on the Internet side, then you don't need to permit DNS traffic specifically.

---

### Post by adam-hardy on 2020-12-01
The iptables rules accept everything from the internal NIC.

I think I'm using [FONT=courier new]bind9[/FONT] because I run [FONT=courier new]backuppc[/FONT] on the server and refer to the clients by host name. About 5 years ago I dumped [FONT=courier new]dnsmasq[/FONT]  for bind9 for several reasons, and I may just have assumed that I  needed a name server for handling the host names - I assume there's no  clever trick for doing host name resolution with [FONT=courier new]dhcpd[/FONT], otherwise I'd love to dump [FONT=courier new]bind9[/FONT]. 

That's making me think. Of course I could set all the clients that need back-ups to static IPs and keep the host names in [FONT=courier new]/etc/hosts[/FONT]. 

I thought the default [FONT=courier new]bind9[/FONT] configuration ***was*** as a caching name server but it looks like there was a setting I hadn't set. That was pretty dumb. 

The last thing I'll do is take off ipv6 handling. Maybe something is going wrong there.

---

### Post by adam-hardy on 2020-12-01
Defeat. 

bind9 was too complex and there's not enough tutorials or Q&A solutions out there on the web, and some of the stuff that it does is totally perplexing. 

What finally killed me was that I could get it going and it would work OK, but then bind9 would write out its config or something, and it would stop working and the checkone tests would fail.

So now I've got just dhcpd and I'll maintain it via its config files.

---

### Post by SeijiSensei on 2020-12-01
You can add the clients to /etc/hosts on the server for backuppc. 
```

192.168.2.1    myserver
192.168.2.101  client1 [alias1] [alias2]
192.168.2.102  client2
[etc.]

```

This works if the server needs to resolve local names, but the clients do not. If you need the clients to be able to identify the machines by name, then you can create /etc/hosts files on them. Windows supports this method as well via the file C:\Windows\System32\Drivers\etc\hosts.

---

