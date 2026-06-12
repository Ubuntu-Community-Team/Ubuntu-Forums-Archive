---
title: "Non-linux network-related question"
date: 2021-08-17
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2021-08-17
I am using a bare-bones 18.04 LTS on a headless server at home. This server is wired to my router, router is wired to the modem.
I'm trying to gain access to the server from the outside, because on this server at port 19000 I have a game server running.

The modem is connected via dynamic IP. So I have retained the services of "no-ip.com". I've downloaded a software client directly to my ubuntu server and it is correctly logged in and running. On the no-ip website, I can confirm that the no-ip domain I've created is pointing to my modem. I also have the built-in client on my router logged in, but I think it doesn't matter - both report the same public IP, so they seem to both point to the entrance point.

FROM THIS POINT, it gets tricky for me.

I've set up a "Virtual Server" on my router. It triggers open when the public port 19000 receives a request. The server direct all traffic speaking to that public port to my internal ip 192.168.1.100, which is the server, and its required port, 19000. For me, the problem is solved.

HOWEVER - when I try to connect from the outside, no ping is received back. From inside the LAN, all is working flawlessly.

Am I missing anything? For example, could there be anything hindering connection from within Ubuntu? or is this just a matter of setting up my router (an old ASUS RT-N66U) properly?

---

### Post by TheFu on 2021-08-17
ICMP (aka ping) is often blocked by firewalls even when a TCP port is open.  The "I've set up a "Virtual Server" on my router." doesn't make sense.  Perhaps you placed a server no a DMZ subnet (which would be a bad idea).  Game servers really shouldn't be hosts on a home subnet.  Spend the $5/month to host it on some VPS provider so you don't risk every system on your LAN to being cracked before you have a better understanding of networking and can setup a 1000x more secure network architecture for this.

Public accessible servers really need to be on a separate subnet from everything else in a home environment, so ***_when_*** it gets hacked, the rest of your systems are not taken over too.  "When" is the correct term, BTW, not "if".

---

### Post by scorp123 on 2021-08-17
> **couzin2000 said:**
> no ping is received back.

Ping is an ICMP protocol and listens on port 7. And firewalls are per default blocking that port which is a good thing.

> **couzin2000 said:**
>  Am I missing anything?

You are testing the wrong port. Ping is on port 7 and blocked per default. You said you opened port 19000? So you need to test port 19000 and "ping" is the wrong tool for that.

To test from **outside** (e.g. from work? via a VPN?) you either need to test with e.g. a port-scanner such as **"nmap"**:

```
nmap -p 19000  your.hostname.no-ip.com
```

A positive scan result should look something like this:

```
Starting Nmap 7.80 ( https://nmap.org ) at 2021-08-18 00:45 CEST
Nmap scan report for your.hostname.no-ip.com
Host is up (0.00034s latency).
PORT   STATE SERVICE
19000/tcp open  unknown
MAC Address: xx:xx:xx:xx:xx:xx (Unknown)
Nmap done: 1 IP address (1 host up) scanned in 0.24 seconds

```

Another tool you could use is e.g. **"nc"**:

```
nc -zv your.hostname.no-ip.com 19000
```

A positive result should look something like this:

```
Connection to your.hostname.no-ip.com 19000 port [tcp/unknown] succeeded!
```

Again: It is very important you test this from OUTSIDE your network, e.g. you can't be sitting at home and test this. Your firewall would detect that the connection is going out and is trying to get back in again and will thus assume that this must be bogus and block this attempt.

Hope this helps?

---

