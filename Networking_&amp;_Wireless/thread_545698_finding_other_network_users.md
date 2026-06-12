---
title: "finding other network users"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by occhiso on 2007-09-07
Hi,

Is there an easy way to find out who is on my home network via the command line, regardless if they're running linux or windows, other than writing a script to ping the whole subnet?

Im still new to linux, but Id like to be able to get ip addresses and/or computer names of all machines connected to my home network, kind of like "net view" in windows.

Thanks,
occhiso

---

### Post by jimrz on 2007-09-08
> **occhiso said:**
> Hi,

Is there an easy way to find out who is on my home network via the command line, regardless if they're running linux or windows, other than writing a script to ping the whole subnet?

Im still new to linux, but Id like to be able to get ip addresses and/or computer names of all machines connected to my home network, kind of like "net view" in windows.

Thanks,
occhiso

you should be able to get that info by accessing your router and looking for something like "attached devices"

---

### Post by jimrz on 2007-09-08
> **occhiso said:**
> Hi,

Is there an easy way to find out who is on my home network via the command line, regardless if they're running linux or windows, other than writing a script to ping the whole subnet?

Im still new to linux, but Id like to be able to get ip addresses and/or computer names of all machines connected to my home network, kind of like "net view" in windows.

Thanks,
occhiso

you should be able to get that info by accessing your router and looking for something like "attached devices", try:
```
http://<your routers IP address>
```

---

### Post by occhiso on 2007-09-08
Yea, thats actually what ive bn doing so far, i use the "dhcp table".
But I would really like to know how to do it using  a unix command promt.

Im trying to become more knowledgable with unix/linux and think this is a good thing to know.

---

### Post by spd106 on 2007-09-08
You can get a list of host IPs using nmap. Install from the universe repo.

This command will ping sweep the local private network
```
:~$ nmap -sP 192.168.0.0/24

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-08 12:27 BST
Host 192.168.0.1 appears to be up.
Host 192.168.0.2 appears to be up.
Host 192.168.0.10 appears to be up.
Nmap finished: 256 IP addresses (3 hosts up) scanned in 1.411 seconds

```
There are loads more advanced options with nmap, it's really a port scanner so it can detect the available services on remote hosts and even the operating system. It can be rather aggressive on network utilisation, so make sure you have the network admins approval before letting it loose. It will also set off most intrusion detection systems (or so I've heard...).

Not all devices will respond to ping, especially if they have a personal firewall. Some other tricks include broadcast ping, though that rarely works anymore. 
```
sudo ping -b 192.168.0.255
```
Also try pinging multicast addresses such as 224.0.0.1 or 224.0.0.251 (mdns).
```
ping 224.0.0.1
ping 224.0.0.251
```
and you can try IPv6 on newer OSs such as Ubuntu. 
```
ping6 -I eth0 ff02::1
```

---

### Post by occhiso on 2007-09-08
Thank you very much!

I didnt know about that program and it sounds like it definitely does what I wanted.
Im going to go try it now :)

Cheers,
occhiso

---

