---
title: "Removing .local from hostname"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by kdmurray on 2008-07-06
How do I reconfigure my Ubuntu machine (running Hardy Heron) so that I can access my machine by it's hostname.

[FONT="Courier New"]titanium:~ kdmurray$ ping cadmium.local
PING cadmium.local (192.168.1.119): 56 data bytes
64 bytes from 192.168.1.119: icmp_seq=0 ttl=64 time=1.031 ms
64 bytes from 192.168.1.119: icmp_seq=1 ttl=64 time=1.009 ms
64 bytes from 192.168.1.119: icmp_seq=2 ttl=64 time=1.037 ms
64 bytes from 192.168.1.119: icmp_seq=3 ttl=64 time=0.919 ms
--- cadmium.local ping statistics ---
4 packets transmitted, 4 packets received, 0% packet loss
round-trip min/avg/max/stddev = 0.919/0.999/1.037/0.047 ms

titanium:~ kdmurray$ ping cadmium
ping: cannot resolve cadmium: Unknown host[/FONT]

When I connect to the server, the locally registered hostname is just "cadmium".
[FONT="Courier New"]kdmurray@cadmium:~$ hostname
cadmium[/FONT]

How can I remove the requirement to use the ".local" suffix?

---

### Post by quantumstitch on 2008-07-06
On the local machine, hostname.local appears in /etc/hosts and /etc/hostname. So change to just hostname and restart network services.(remember to make a backup). 

In my home, I usually set hostnames in /etc/hosts to bind to a given ip on all machines. My router assigns static 192.x.x.x ips to certain MAC address.

---

### Post by kdmurray on 2008-07-08
Thanks for the speedy reply.  However, upon checking the /etc/hosts file, the hostname assigned is only "cadmium" and not "cadmium.local" as I expected to find.

Any other ideas?

---

### Post by quantumstitch on 2008-07-11
How about this?
add this line to /etc/hosts
```

192.168.x.x cadmium cadmium.local

```
If this is a problem when using ssh from another machine and you are having to use
```

ssh cadmium.local

```
instead of 
```

ssh cadmium

```
That should fix it.
Sorry for the delay.

---

### Post by Endolith on 2008-09-12
This just happened to my desktop, too.  Yesterday it started acting as hostname.local instead of hostname.  Very strange.  I don't know what caused it to change.  My router does not list it as a DHCP client, and I cannot access it at the normal hostname, but I can access it at hostname.local.  If I log into it through my external dynamic IP, it works fine, and lists username@hostname, even though this hostname is not on my network.  What is .local?  Some kind of local cache of the other machine's IP address?  laptophostname and laptophostname.local both go to the same IP, so I'm guessing that's what it is.  If the other machine is not registered on the network under its hostname, my machine guesses based on the past?  If I reboot the desktop, it sometimes has the hostname and sometimes does not.

---

