---
title: "Ubuntu Server Setup"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-10-13
Hi,

It's my first time using Ubuntu Server, I've successfully installed the OS and started installing the software I need. I've installed bind9, POSTFIX with SMTP-AUTH and TLS and I've also got SSH configured so I can connect to the server within my local network (I also had LAMP installed on installation of the server). 

My intentions for the server are for some small time webhosting (I want to gain experience in hosting/running a website from my own server), it's only going to be a small website with a tiny audience but it's experience nonetheless. I was also planning on using the server for some IRC related stuff, maybe some BNC hosting or whatever. 

So anyway, I've installed the software I wanted and now I'm looking into how to configure a domain with my server and start hosting some simple HTML pages with a domain, however I've come across a problem. From what I can gather, all of the guides I've read use a static IP, I have a router with a broadband connection (in the U.K) thus my IP is dynamic and will be changing. 

I'd much appreciate anyone that can guide me in the right direction for configuring my domain and getting some files up and running, along with any information on the static/dynamic IP issue. The last thing I'd like to add is that I can only access the server through SSH if I'm on my own network, I have no way of gaining SSH access over the internet outside my network, once again any info on resolving this is much appreciated!

- Aaron.

---

### Post by az on 2009-10-13
> **Letterbomb05 said:**
> Hi,



I'd much appreciate anyone that can guide me in the right direction for configuring my domain and getting some files up and running, along with any information on the static/dynamic IP issue. The last thing I'd like to add is that I can only access the server through SSH if I'm on my own network, I have no way of gaining SSH access over the internet outside my network, once again any info on resolving this is much appreciated!

- Aaron.

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by rampageoberon on 2009-10-13
> **Letterbomb05 said:**
> So anyway, I've installed the software I wanted and now I'm looking into how to configure a domain with my server and start hosting some simple HTML pages with a domain, however I've come across a problem. From what I can gather, all of the guides I've read use a static IP, I have a router with a broadband connection (in the U.K) thus my IP is dynamic and will be changing. 

I'd much appreciate anyone that can guide me in the right direction for configuring my domain and getting some files up and running, along with any information on the static/dynamic IP issue. The last thing I'd like to add is that I can only access the server through SSH if I'm on my own network, I have no way of gaining SSH access over the internet outside my network, once again any info on resolving this is much appreciated!

- Aaron.

Hi there,

Not a problem for a small personal site though using dynamic IP's is not ideal.

You want to consider a dynamic dns solution (DynDns.com or no-ip.com) where you can point a domain to your dynamic ip and have it update the ip at regular intervals.

For the SSH you can do this with Iptables. I assume the internal network has IP 192.168.1.x
```
sudo iptables -t filter -A INPUT -p tcp -m multiport --dports 22 -m iprange ! --src-range 192.168.1.0-192.168.1.255 -m iprange ! --src-range 127.0.0.1 -j DROP

```

You can also have it listening on on the internal IP.

Hope this helps

---

### Post by Letterbomb05 on 2009-10-13
Hi,

thanks both of you for your replies, I'm reading into it now, very useful information :)

- Aaron.

---

