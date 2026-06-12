---
title: "SSH issues over the internet"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2014-03-22
Hello, I'm trying to access my servers over the internet, I have configured all servers to run off port 39352 and on the lan ssh works fine.

Both of my servers one Ubuntu 13.10 the other Debian Wheezy show these ports as open when I run locally;

```
rhys@cherry:~$ nmap -p 39352 192.168.1.36

Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-22 12:59 GMT
Nmap scan report for tomato.default (192.168.1.36)
Host is up (0.0041s latency).
PORT      STATE SERVICE
39352/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.21 seconds
```

I have an EE router, which has public port 39036 forwarded to private port 39352 on private IP 192.168.1.36 and public port 39030 forwarded to private port 39352 on private IP 192.168.1.30 

[http://www.canyouseeme.org/](http://www.canyouseeme.org/) says

```
 Success: I can see your service on 1.22.333.444 on port (39036)
Your ISP is not blocking port 39036
```

However SSH doesn't work

```
rhys@cherry:~$ ssh -p 39036 rhys@1.22.333.444
ssh: connect to host 1.22.333.444 port 39036: Connection refused
rhys@cherry:~$ nmap -p 39036 1.22.333.444

Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-22 13:04 GMT
Nmap scan report for 1.22.333.444
Host is up (0.0021s latency).
PORT      STATE  SERVICE
39036/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.19 seconds
```

I've tried disabling all firewalls on both the router and server, but nothing works. I've also tried connecting via putty on a physically different network, which comes back with a similar error.

---

### Post by Lars Noodén on 2014-03-22
In your description you have port 39030 and in your sample you have 39036.  Is that a typo?

---

### Post by AmbiguousOutlier on 2014-03-22
> **Lars Noodén said:**
> In your description you have port 39030 and in your sample you have 39036.  Is that a typo?

I have two servers, one I have forwarded from public port 39030 and the other from 39036 both to their private IP's on local port 39352.

---

### Post by ian-weisser on 2014-03-22
Methodically eliminate possibilities.

Can you ssh between the two systems inside their lan?
```
rhys@debian:~$ ssh -p 39352 rhys@ubuntu

rhys@ubuntu:~$ ssh -p 39352 rhys@debian
```
If ssh works locally between the servers, then it's not an ssh or local firewall issue.
Then (and only then) is it time to start testing your router firewall and forwarding rules.

---

### Post by untrustytahr on 2014-03-22
[FONT=century gothic][SIZE=2]Verifying that ssh is properly configured for 39352 as ian-weisser says is a good start.   
[/SIZE][/FONT]
[FONT=century gothic][SIZE=2] [/SIZE][/FONT][FONT=century gothic][SIZE=2]
[/SIZE][/FONT]
[FONT=century gothic][SIZE=2] [/SIZE][/FONT][FONT=century gothic][SIZE=2]If I understand your description, you can't access your servers that are behind a NAT firewall by their public IP while you too are behind that same firewall, correct?  If so, that's because you need a router capable or hairpinning (reflection).  I'm not familiar with EE, but you may also want to verify that.  You said you tried from a different network, but it wasn't clear if you were on the other side of the NAT.[/SIZE][/FONT]

---

### Post by AmbiguousOutlier on 2014-03-22
Yes, I can access both servers from any client on the LAN, via port 39352.

Yes, I am trying this from behind the same firewall. Although I have tried accessing from another Windows machine in a different location behind a different router and NAT using Putty and this still fails.

---

### Post by ian-weisser on 2014-03-22
Then it seems time to ignore the servers, and focus on your router's settings.

---

### Post by steeldriver on 2014-03-22
The failure to connect from **inside** the LAN may be due to your router not supporting [NAT loopback]("http://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback") - the failure via PuTTY from **outside** the LAN may be unrelated... ?

---

