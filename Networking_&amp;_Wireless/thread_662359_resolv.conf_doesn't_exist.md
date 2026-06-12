---
title: "resolv.conf doesn't exist"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2008-01-08
Did a reinstallation of Ubuntu, immediately tried to get my networking to work. Installed ndiswrapper, installed the driver I need for my wifi adapter, made sure everything was working, and ran sudo ifup wlan0.

Right away, I got the error:
```
grep: /etc/resolv.conf: No such file or directory
```
and indeed, it's not there. There is a folder resolvconf, but it doesn't contain my file either. What should I do to get ifup working? Thanks.

---

### Post by chimerical_brio on 2008-01-08
Good news! It works. I can ping my router, other computers on my network can ping my computer, I'm very happy.

BUT: I can't get outside of my network, and I have a feeling it's related to resolv.conf. What is resolv.conf? How do I generate one? It seems like it has to do with DNS...thanks.

---

### Post by freymann on 2008-01-08
> **chimerical_brio said:**
> 
I can't get outside of my network, and I have a feeling it's related to resolv.conf. What is resolv.conf? How do I generate one? It seems like it has to do with DNS...thanks.

 /etc/resolv.conf tells your system what servers to use for DNS resolution.

 Mine looks like this:

```

nameserver a.b.c.d
nameserver w.x.y.z
domain you.homeunix.com

```

 You will need to add at least one valid DNS server IP. Two is better.
 The "domain" should be whatever you are calling your computer on the network, but you *may* be able to leave that line out.

 You can easily check to see if you can resolve domain names by trying to ping something by domain name instead of IP number

```

ping interpool.ca

```

 should give you results. If you have no DNS it will fail. Set up your /etc/resolv.conf file and try the ping command again.

---

### Post by chimerical_brio on 2008-01-08
Alright, well, I figured out the problem. I had, when reinstalling, brought over my interfaces file right away, which includes a static IP, so my computer wasn't getting the DNS settings from my router. So I just had to temporarily switch over to using dhcp, automatically got the settings, and changed it back to static.

---

