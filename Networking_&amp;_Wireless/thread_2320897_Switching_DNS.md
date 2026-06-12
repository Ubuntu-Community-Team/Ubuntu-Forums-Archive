---
title: "Switching DNS"
date: 2016-04-18
forum: Networking &amp; Wireless
---

### Post by jim_deadlock on 2016-04-18
I want to be able to easily switch between 2 DNS servers. Each of the DNS servers works fine if I only have one network connection, but if I try to set up 2 network connections with the only difference being the DNS, switching between them doesn't work, it gets stuck on one or the other. I think /etc/resolv.conf seems to override everything but I'm not sure. What's the best way to achieve this?

---

### Post by T.J. on 2016-04-19
> **jim_deadlock said:**
> I want to be able to easily switch between 2 DNS servers.

Most unusual.  Standard users do not typically have access to change the DNS, because it would be a security hole.


>  Each of the DNS servers works fine if I only have one network connection, but if I try to set up 2 network connections with the only difference being the DNS, switching between them doesn't work, it gets stuck on one or the other. 

Yes. On TCP/IP, one card/connection is chosen,  because it has priority over the other.  I'd need more information about what you are trying to achieve before I can help you configure it for your needs. Why do you want to do this?     You can have a list of DNS servers. If one fails, it moves to the next.

> I think /etc/resolv.conf seems to override everything but I'm not sure. 

Yes, it will.  The resolv.conf file specifies the nameserver order of precedence.

---

### Post by jim_deadlock on 2016-04-19
OK, well one is my normal auto-DNS and the other is for unlocator.com

---

### Post by SeijiSensei on 2016-04-19
This is not easy to do with Ubuntu since it creates resolv.conf each time it boots using the resolvconf package. You could create a secondary resolv.conf and a script that overwrites the existing resolv.conf with the one you wrote.  You'll need to run this with sudo since it would need to run with root privileges.
```

#!/bin/bash

# copy secondary resolv.conf to /etc
cp /home/me/myresolv.conf /etc/resolv.conf

```

---

### Post by T.J. on 2016-04-19
> **SeijiSensei said:**
> This is not easy to do with Ubuntu since it creates resolv.conf each time it boots using the resolvconf package. You could create a secondary resolv.conf and a script that overwrites the existing resolv.conf with the one you wrote.  You'll need to run this with sudo since it would need to run with root privileges.
```

#!/bin/bash

# copy secondary resolv.conf to /etc
cp /home/me/myresolv.conf /etc/resolv.conf

```

I don't think that achieves what he/she is looking for. 

But for the sake of discussion, on Debian, (and I assume Ubuntu as well, since Ubuntu is essentially a copy of Debian)  it is not resolvconf, but in fact network-manager and dhcpd that overwrite resolv.conf by default.  A script like this wouldn't work because they would just overwrite it again as soon as either releases an IP and requests a new one via dhcpd.  That can happen at any time.  A better solution would be to use  the "prepend domain-name-servers" option in your /etc/dhcp/dhclient.conf file, so that when a lease is requested, the appropriate nameservers are always added.  It also eliminates the need for an additional script or adding it to systemctl for startup.

If he/she is using a static IP, then resolv.conf probably remains unchanged, in which case, both ideas are redundant.

---

### Post by T.J. on 2016-04-19
> **jim_deadlock said:**
> OK, well one is my normal auto-DNS and the other is for unlocator.com

Good morning! :D

I'm still not quite 100% certain of what you need.  Are you trying to add a backup DNS or backup connection in case one or the other fails?  Are you trying to use two at once for some reason? 

Your auto-DNS is always added.  In order to help you add unlocator, I needed to find the IP address for you to add the nameserver, because you have to use an IP number. URLs are not allowed.  unilocator.com does not appear to serve DNS.  They get theirs from cloudflare.com, and don't have a nameserver for their specific domain or even an alias.  Normally that disqualifies them entirely, implying that they do not serve DNS to outside parties. They might still allow it, but I wouldn't recommend relying on their good graces unless you are a cloudflare or unlocator customer.  If you are, you should get the IPs for their public nameservers from them.


 I'm posting this so that you don't have to just take my word for it.


```

tj@Workstation:~$ dig unlocator.com ns


; <<>> DiG 9.9.5-9+deb8u6-Debian <<>> unlocator.com ns
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62545
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 5


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;unlocator.com.            IN    NS


;; ANSWER SECTION:
unlocator.com.        86400    IN    NS    pete.ns.cloudflare.com.
unlocator.com.        86400    IN    NS    lorna.ns.cloudflare.com.


;; ADDITIONAL SECTION:
pete.ns.cloudflare.com.    172769    IN    A    173.245.59.136
pete.ns.cloudflare.com.    172769    IN    AAAA    2400:cb00:2049:1::adf5:3b88
lorna.ns.cloudflare.com. 172769    IN    A    173.245.58.190
lorna.ns.cloudflare.com. 172769    IN    AAAA    2400:cb00:2049:1::adf5:3abe


;; Query time: 35 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Apr 19 10:15:20 CDT 2016
;; MSG SIZE  rcvd: 183
]
```

A working DNS server would show up as an NS record in the answer section under their own name. As an example:

```

tj@Workstation:~$ dig google.com ns


; <<>> DiG 9.9.5-9+deb8u6-Debian <<>> google.com ns
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 13275
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 5


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.            IN    NS


;; ANSWER SECTION:
google.com.        170555    IN    NS    ns3.google.com.
google.com.        170555    IN    NS    ns2.google.com.
google.com.        170555    IN    NS    ns4.google.com.
google.com.        170555    IN    NS    ns1.google.com.


;; ADDITIONAL SECTION:
ns1.google.com.        170555    IN    A    216.239.32.10
ns2.google.com.        170555    IN    A    216.239.34.10
ns3.google.com.        170555    IN    A    216.239.36.10
ns4.google.com.        170555    IN    A    216.239.38.10


;; Query time: 130 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Apr 19 10:20:40 CDT 2016
;; MSG SIZE  rcvd: 175



```

If you are trying to get both cards operational in case one fails and then it rolls over to the next on the same network, that is called "bonding" and can easily be done.  I just want to make certain of what you want before I make too many suggestions that confuse the issue.

---

### Post by jim_deadlock on 2016-04-19
unlocator.com is a service which you sign up for that changes the region/location of your IP address so that you can access various online services for different regions, so you're not tied to your own region. It has the same effect as a proxy but it does it via DNS rather than tunnelling traffic like a proxy would. To do this, you use their special nameserver (209.177.145.30) on your internet connection and set your region via your account on their website. It's better than a proxy because there's no traffic forwarding involved so no slowdown.

I have no trouble using my own DNS or their DNS as long as I do it manually by changing resolv.conf etc but I would prefer to set up 2 network connections each with a different DNS server which would make it easier to switch back and forth between the two. Because I'm lazy. From what you guys are saying it seems like this is not really possible and I'll have to spend the full 60 seconds to change it manually. No biggie, thanks for your help anyway.

---

### Post by him610 on 2016-04-19
Did you consider manually setting the desired DNS servers in your router?

---

### Post by jim_deadlock on 2016-04-19
Yes but that's still a manual job. I'm spoiled you see, because before Unlocator I used to use proxies and those are easy to switch between with 2 mouse clicks via my Gnome Shell network indicator. I'm trying to have the best of both worlds - a DNS easy-switcher.

---

### Post by T.J. on 2016-04-19
Ah I see! Thank you for explaining.  

The easiest way to integrate it to your Gnome Desktop - which usually requires network-manager - would be to use it to create two profiles and then switch between them - which is probably what you meant you were doing in the first place.  I assumed you were playing with core networking.  When you were talking about two connections, I assumed two cards and some elaborate setup!

 Totally my bad!  The more I overthink, the more murky things get.  I'm afraid it is an occupational hazard from when I used to build servers.  I humbly ask your pardon for confusion.
 
Let me run some tests!  I shall return.

---

### Post by jim_deadlock on 2016-04-19
Yes switching between 2 profiles is what I tried in the first place but it doesn't seem to work properly, it just gets stuck on one or the other - resolv.conf seems to be in charge and prevent the switching.

---

### Post by T.J. on 2016-04-24
Sorry for the delay.  Programming Microsoft at work is driving me batty. I'll try to get back to you before the weekend ends.

---

### Post by jim_deadlock on 2016-04-24
I've written a small perl script which changes the nameserver in resolv.conf then switches networking off and on again. Does the trick but it has to run under sudo from the terminal and I can't figure out a way to make a .desktop launcher run it under sudo. I tried:

```
Exec=sudo /path/to/script
```

...but no dice.

---

