---
title: "FireHOL &amp; Ubuntu 8.04"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Moso on 2008-05-25
Hi!

I want to use FireHOL with my Ubuntu 8.04 but some things aren't working like expected...

First things first: the version installed via **apt-get install firehol** is version *firehol.sh,v 1.256 2007/05/22 22:52:53 ktsaou* and the version of get-iana is *get-iana.sh,v 1.10 2007/05/05 23:38:31 ktsaou*.  The version of get-iana can't update the **/etc/firehol/RESERVED_IPS** anymore.

So I used **wget [http://firehol.sf.net/firehol.tar.gz](http://firehol.sf.net/firehol.tar.gz)** to get the latest version and update my two main FireHOL files to versions *firehol.sh,v 1.271 2008/03/17 22:08:43 ktsaou* and *get-iana.sh,v 1.12 2008/03/17 22:08:43 ktsaou*.

This is my **firehol.conf**:

```
iptables -A INPUT  -p UDP -d 255.255.255.255 --destination-port 67:68 -j DROP
iptables -A OUTPUT -p UDP -d 224.0.0.251     --destination-port 5353  -j DROP

tcpmss auto

home_ips="192.168.1.0/24"

server_SAgent4_ports="udp/3259"
client_SAgent4_ports="default"

#transparent_proxy "80 3128 8080" 8080 "proxy root bin" inface not "ppp+" dst not "127.0.0.1 192.168.1.254"

interface "eth0" home src "${home_ips}"
        policy reject
        server "cups dhcp dns http https icmp SAgent4 samba ssh webcache webmin"        accept
        client "http https icmp samba ssh"                                              accept

interface "ppp+" internet src not "${home_ips} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10
        server "http https ssh webmin"                                                  accept
        server "ident"                                                                  reject with tcp-reset
        client "all"                                                                    accept

router home2internet inface "eth0" outface "ppp+"
        masquerade
        route "all"                                                                     accept

router internet2home inface "ppp+" outface "eth0"
        route "ident"                                                                   reject with tcp-reset
```

The *transparent_proxy* directive is commented because it is not working for the server itself.

When the server wants to access HTTP this is what appears on **/var/log/messages**:

```
'OUT-unknown:'IN= OUT=ppp0 SRC=189.27.226.196 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=17490 DF PROTO=TCP SPT=35373 DPT=8080 WINDOW=5808 RES=0x00 SYN URGP=0
```

I already discussed this issue with Costa Tsaousis, the author of FireHOL and it pointed to me that the server is using an interface not defined in **firehol.conf** and that appears to be a routing problem.

Costa wrote:
> 'OUT=ppp0' means that the interface the machine is sending the traffic via, is ppp0 
'DST=127.0.0.1' means that the traffic is going to 127.0.0.1 which as we all know is the localhost. 
 
So, your kernel is thinking that is going the send traffic to 127.0.0.1 through ppp0, which of course is not allowed and cannot happen (127.0.0.1 is the ip address of the interface 'lo').

Later Costa wrote:
> Leandro, 
 
you are missing the 127.0.0.0 route. 
 
Check the ubuntu support. It should be there. 
This is mine: 
 
box ~ # route -n 
Kernel IP routing table 
Destination Gateway Genmask Flags Metric Ref Use Iface 
10.11.12.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0 
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1 
239.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 eth0 
127.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 lo 
224.0.0.0 0.0.0.0 240.0.0.0 U 0 0 0 eth0 
0.0.0.0 192.168.1.254 0.0.0.0 UG 0 0 0 eth1

And really, the output of **route** and **route -n** in my Ubuntu is:
```
root@matrix:~# route
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
189.27.224.1.ad *               255.255.255.255 UH    0      0        0 ppp0
localnet        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0
```
and
```
root@matrix:~# route -n
Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
189.27.224.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```

Please see more info on:
[http://sourceforge.net/forum/forum.php?thread_id=2041245&forum_id=196547](http://sourceforge.net/forum/forum.php?thread_id=2041245&forum_id=196547)

Please help!  FireHOL is a great tool and I really want to use it with Ubuntu.

---

### Post by Moso on 2008-05-26
bump! :(

---

### Post by Moso on 2008-05-31
I tried to add manually the loopback route, disable IPv6 support and changed my /etc/hosts file.

Still no success...  :(

---

### Post by Moso on 2008-06-03
There is no more need of the route to loopback interface?

Anyone?

---

