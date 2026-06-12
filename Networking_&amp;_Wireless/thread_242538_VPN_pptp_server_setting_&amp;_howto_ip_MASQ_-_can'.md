---
title: "VPN pptp server setting &amp; howto ip MASQ - can't access externel internet"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by pineday on 2006-08-23
ubuntu ver : dapper
pptpd : 1.2.3 & default setting.
client : windows xp

/etc/pptpd.conf
localip 172.17.0.1
remoteip 172.17.1.1-254,172.17.2.1-254

/etc/ppp/pptpd-options : default setting

and I(client) connect pptp vpn server. then connect success.
internel network well(172.17.1.3 ..1.4 ..).

but, client --> vpn server --> externel internet
client can't access externel internet.(don't using internet, only internel network access)

How to access externel internet?

I try to ip masq setting. (many method rule)
eth0 is externel interface.
# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
etc..

when client access internet(web page). client find ext server(web server). but can't get web page. 
browser status bar msg : waiting for ..{site name}

How vpn client use externel internet? (not client's TCP/IP option - uncheck "use default gateway on remote network")

addition :
```

root@ubuntu-vpn:/etc/ppp# ip ro
172.17.2.3 dev ppp0  proto kernel  scope link  src 172.17.0.1
{real_ip_}.0/30 dev eth0  proto kernel  scope link  src {real_ip_}.2
default via {real_ip_}.1 dev eth0

root@ubuntu-vpn:/etc/ppp# ip a
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:02:2a:c1:60:96 brd ff:ff:ff:ff:ff:ff
    inet {real_ip_}.2/30 brd 211.229.208.3 scope global eth0
    inet6 fe80::202:2aff:fec1:6096/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:0a:5e:52:e4:7d brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0
7: gre0: <NOARP> mtu 1476 qdisc noop
    link/gre 0.0.0.0 brd 0.0.0.0
29: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP> mtu 1396 qdisc pfifo_fast qlen 3
    link/ppp
    inet 172.17.0.1 peer 172.17.2.3/32 scope global ppp0

```

---

### Post by pineday on 2006-08-28
Is impossible use iptables ?

How can use internet? (windows clients)

In my case. show attach files!

---

### Post by jurkki on 2006-08-28
did you remember in addition to masq. iptables rules set ip_forwarding?

echo "1" >/proc/sys/net/ipv4/ip_forward

---

### Post by pineday on 2006-08-28
echo "1" >/proc/sys/net/ipv4/ip_forward

Yes. I try to.

full setting is.
```

iptables -F; iptables -t nat -F; iptables -t mangle -F
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
eth0 is external internet interface.

I try to set again.
some clients 
 - can't use all external internet .
another some clients 
 - some sites is not usable.(msn.com , live.com, myspace.com , ... many sites.)
 - some sites is usable.(yahoo.com, ubuntuforums.org, google.com , technorati.com ... some sites & connectiong speed so slowly..)
 - each clients : differ usable sites .

and I try to testing ping test.
I found. usable sites is ping packets reachable. but not usable sites is ping unreachable.

why?
cause(I thought)
1. pptp server setting is wrong.
2. routing table is incorrect.
3. iptable setting is wrong.
and etc..

plz. some comment. I want to solve this problem. :confused:

---

### Post by pineday on 2006-08-28
Is impossible use "iptables"?
necessary another tools ?

Is impossible? only iptables

---

### Post by pineday on 2006-09-04
I solve this problem.
problem is : ubuntu dapper's pptpd default option.(at least my case)


/etc/pptpd.conf - default & modify only remoteip, localip 
/etc/ppp/pptpd-options
default is :
```

refuse-pap
refuse-chap
refuse-mschap

require-mschap-v2
require-mppe-128

```

I change this optioin.
```

require-chap --> enable

require-mschap-v2
#require-mppe-128 --> disable

```

and test , check "use default gateway on remote network".

iptable rule is 
```

iptables -F; iptables -t nat -F; iptables -t mangle -F
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

**client --> vpn-server --> external internet ( is OK!! )**

---

### Post by tmantoro on 2008-06-22
I installed and configured pptp, kerbero, winbind and samba, using ubuntu 7.01. I can login from AD and currently, I can browse to almost external internet web pages but not for couple webs, for example dilbert.com.

My pptpd config is
```

[FONT="Comic Sans MS"]lock
debug
nologfd
nobsdcomp
proxyarp
require-mschap-v2
require-mppe
ms-dns xxx.xxx.xxx.xxx
ms-dns xxx.xxx.xxx.xxx
plugin winbind.so
ntlm_auth-helper "/usr/bin/ntlm_auth --helper-protocol=ntlm-server-1"
auth[/FONT]

```

Can somebody give me suggestions, why I can't browse to some of those webs?

Thanks,

-tm

---

