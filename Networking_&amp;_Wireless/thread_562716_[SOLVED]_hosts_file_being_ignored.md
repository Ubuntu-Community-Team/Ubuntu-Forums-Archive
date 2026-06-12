---
title: "[SOLVED] hosts file being ignored"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by trinsan on 2007-09-29
What should be very simple, seems to be giving me some headache.

I've modified my hosts file to:

> 
127.0.1.1 LAMP1
127.0.0.1  localhost [www.traving.dk](www.traving.dk) [www.pckonsulent.dk](www.pckonsulent.dk) [www.traving.net](www.traving.net) [www.cyclingsage.com](www.cyclingsage.com) LAMP1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


In order to send requests for [www.traving](www.traving), [www.pckonsulent.dk](www.pckonsulent.dk), [www.traving.net](www.traving.net) and [www.cyclingsage.com](www.cyclingsage.com) to my local machine rather than the public IP.

But, whatever I seem to do, I always get forwarded to the public IP.

I've browsed several posts, and this should do the trick... but it doesn't.

Thanks for your help,

Trin

~

---

### Post by dcstar on 2007-09-29
> **trinsan said:**
> What should be very simple, seems to be giving me some headache.

I've modified my hosts file to:



In order to send requests for [www.traving](www.traving), [www.pckonsulent.dk](www.pckonsulent.dk), [www.traving.net](www.traving.net) and [www.cyclingsage.com](www.cyclingsage.com) to my local machine rather than the public IP.

But, whatever I seem to do, I always get forwarded to the public IP.

I've browsed several posts, and this should do the trick... but it doesn't.

Thanks for your help,

Trin

~

Is your browser caching previous DNS lookups?

Do a **traceroute** to each of them and see what resolves, and the **nslookup** tool is useful as well.

---

### Post by trinsan on 2007-09-29
Both traceroute and nslookup resolve the public IP, not the ones in the hosts file.

I've tried reinitializing the network too, no luck.

Cheers, Trin

---

### Post by helgman on 2007-09-29
Make sure that /etc/host.conf reads:
```
order hosts,bind
```

This tells the computer to first search the hosts file and then go fish the DNS-server.

Regards,
Helgman

---

### Post by noob12 on 2007-09-29
I think that most code that is not statically linked to old libc versions should be using /etc/nsswitch.conf now.

nslookup will always go to DNS.  It calls DNS directly and not through libc/gethostbyname(), so it will never look at /etc/hosts.

I think that traceroute will use libc for forward lookups but not for the reverse lookups that are shown for the points it is hitting.

Another way to get what you want may be to set a host route for that specific public address back to your loopback.

---

### Post by trinsan on 2007-09-29
After taking a more or less voluntary 3 hour nap, I noticed something interesting.

Under Xfce (4.3.90.2) it ignores the hosts file.

But if I log off X and just run the terminal, it reads the hosts file. So its apparently X related.

Hope this makes more sense to you pro's :-)

Cheers, Trin

---

### Post by trinsan on 2007-09-29
Solves the issue. The error path for the sites in apache had an "s" in logs, and so the sites never went online on the localhost adresse.

While a terminal based resolve kept pointing at the locahost addy, firefox went for the public address when the local adresse didn't respond.

Cheers, Trin

---

