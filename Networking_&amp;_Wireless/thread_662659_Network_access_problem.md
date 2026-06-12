---
title: "Network access problem"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by ladjack on 2008-01-09
hi 2 all!

**my machine:**
os: ubuntu 7.10
krnl ver.: 2.6.22-14-generic
chipset: ati rs480m
nic1: broadcom netlink bcm5788 gigabit ethernet (eth0)
nic2: broadcom bcm4318 802.11b/g (eth1)
i use ONLY IPv4

**my network:**
ip: 192.168.0.20/24
def gw: 192.168.0.1
dns: 192.168.0.2 (in fact it doesn't matter...)
proxy(squid) ip: 192.168.0.1:3128 (...serve all dns-requests)

1st i've done is disable "bcm43xx" (eth1) module in /etc/modprobe.d/blacklist, as don't need it.
Then i assign proper values for TCP/IP on my eth0.
Set up global network proxy settings, also set proxy settings in firefox.

**Reboot...**

Launch firefox...no page is loaded (any page, no matter wich one)
Launch pengui (IM or whatever) ... it doesn't work to. My squid logs give me TCP_DENY answer for CONNECT method.
Launch ssh admin@192.168.0.1...doesn't work...log: Read from socket failed: Connection reset by peer

**Reboot...into freebsd (TCP/IP settings the same)**

All works fine: ssh, internet (opera, ff), wget, fetch
[B]
Reboot...into windows xp (TCP/IP settings the same)[/B]

All works fine: putty, internet (opera, ff), icq, etc.
[B]
Reboot...into ubuntu[/B]

Go to my friend-admin, he uses proxy to (squid, btw. it's parent cache for my squid), reset TCP/IP settings to fit his network...

All works fine...

I am in stuck...help is needed.

Thnx in adv.

---

### Post by Dngrsone on 2008-01-09
I would think that the DNS server IP *does* matter, and that is likely where your problem lies.

If your gateway is providing DNS resolution for your network, then put the gateway IP in there.  Otherwise, try plugging in the IP of the DNS host that your router/switch/modem is using.

---

### Post by ladjack on 2008-01-09
```
If your gateway is providing DNS resolution for your network
```

name resolution provide my squid server on gateway...so at least firefox should work, coz a've pointed it to proxy_ip_addr:3128

---

### Post by Dngrsone on 2008-01-09
Then plug your gateway's IP in the DNS block-- 192.168.0.1

---

### Post by ladjack on 2008-01-09
But there is NO SERVICE running on my gateway wich will serve my request on 53 port...
OK, any way, i've try it and it is doen't work.

---

### Post by Dngrsone on 2008-01-09
[img]http://xs209.xs.to/xs209/06476/eh.gif[/img]  What request on 53 port?

Either your gateway provides DNS resolution * as a service* or it does not.

Either you need proxy information plugged into Firefox for it to get to the internet or not.

Also, why is your wireless card showing up as eth1 instead of wlan0 or ath0, I wonder...

---

### Post by ladjack on 2008-01-10
```
What request on 53 port?
```

see /etc/services

```
Either your gateway provides DNS resolution as a service or it does not.
```

it doesn't. but squid does.


```
Either you need proxy information plugged into Firefox for it to get to the internet or not.
```

yes, ff need to be pointed to proxy. and i did it. and it works under freebsd and winxp.

```
Also, why is your wireless card showing up as eth1 instead of wlan0 or ath0, I wonder..
```

have no idea, also it doesn't matter.

i think it is all about IPv6 mac addresses, that ubuntu assign to my eth0...couse my gate echoes such messages:

Jan 9 14:23:12 proxy kernel: arp: unknown hardware address format (0x0000)

any ideas?

p.s. Dngrsone, thnx for answers ;)

---

### Post by ladjack on 2008-01-10
i have installed xubuntu 6.10 and it solves the problem....what else can i say?

---

