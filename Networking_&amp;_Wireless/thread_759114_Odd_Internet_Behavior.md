---
title: "Odd Internet Behavior"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by PH James on 2008-04-18
Hello.

I'm running on a home network, and it seems at random times my main box (Ubuntu 7.10), which is hooked up to the router via ethernet, will not load a website. Some websites it will load, others it will not. Sometimes refreshing the page helps. This can go on for anywhere from a few seconds to several minutes.

Another computer on the network (running XUbuntu), while this is happening, can access everything this computer cannot.

Both PCs I have tested in this situation (it only happens on the one as far as I've seen) have static IPs. Their basic /etc/network/interfaces file looks like this:

```
auto eth0
iface eth0 inet static
address 192.168.1.x
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.1.1
broadcast 192.168.1.255

auto lo

iface lo inet loopback
```

The router is a wired/wireless Linksys WRT54G. Restarting it doesn't seem to affect the problem.

I'm running Firefox 2.0.0.3. I have tested this in Opera and even the pages that load in Firefox don't load in Opera, I assume this is related to caching in Firefox.

Sometimes when this happens, I can access, for instance, YouTube, but only the HTML loads and there is no styling. Again, I assume this is related to caching.

Any help is much appreciated.

---

### Post by chili555 on 2008-04-18
When this happens, what kind of ping times do you get from your router:```
ping -c3 192.168.1.1
```and from your ISP:```
ping -c3 my.provider.net
```Let's see if this is an ISP, router or computer issue.

---

### Post by PH James on 2008-04-18
Thank you for replying.

It just happened again, these are the ping times I got:

Comcast.net:
PING comcast.net (204.127.205.8) 56(84) bytes of data.
64 bytes from 204.127.205.8: icmp_seq=1 ttl=48 time=14.3 ms
64 bytes from 204.127.205.8: icmp_seq=2 ttl=48 time=13.4 ms
64 bytes from 204.127.205.8: icmp_seq=3 ttl=48 time=14.7 ms

My router:
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.30 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.00 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.12 ms

Again, while this happened I was able to use my laptop without problem.

---

### Post by djronh on 2008-04-18
Hi, I have had similar problems (Ubuntu 7.10 + Firefox 2.0).
Logging in and out of gmail required refresh.
Softpedia linux page crashed my firefox browser halfway down page.
Many more example...
sun java 6 at fault returning to 5 solved my problems.
This was caused by the more complicated java applets.

---

### Post by chili555 on 2008-04-18
Looks like it's not external; those are great times. Some other things to check would be the DNS servers. Perhaps one is intermittently down. Are the nameservers the same in both machines?```
cat /etc/resolv.conf
```While this is going on, can you ping both nameservers with reasonable times?

You might also look at:```
sudo ethtool eth0
```and, while it's going on:```
sudo cat /varlog/messages | grep eth0
```

---

### Post by superprash2003 on 2008-04-18
it looks like a DNS problem you could change your DNS servers to opendns and then try . this is how you do it  [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by PH James on 2008-04-18
> **chili555 said:**
> Looks like it's not external; those are great times. Some other things to check would be the DNS servers. Perhaps one is intermittently down. Are the nameservers the same in both machines?```
cat /etc/resolv.conf
```While this is going on, can you ping both nameservers with reasonable times?

You might also look at:```
sudo ethtool eth0
```and, while it's going on:```
sudo cat /varlog/messages | grep eth0
```

I checked and the PC with the problem was using my router as the only nameserver while my laptop was using the same ones as defined in my router's setup.

I've changed the main PC's DNS servers to match my laptops' and my routers'. So far it looks good, but if this was the problem could the problem possibly lie within the router?

And yes, before I changed it I could ping both with reasonable times.

---

