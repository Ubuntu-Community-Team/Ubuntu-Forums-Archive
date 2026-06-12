---
title: "display hostnames on local network"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by cryptoxic on 2011-01-10
I was wondering if I can display hostnames on my local network.
If I type in a command " sudo arp-scan -l " it will show me the list of IPs and addresses. However, it would be nice to know which **users** they belong to.

---

### Post by blind2314 on 2011-01-10
Do you have any kind of DNS setup on this home network? Through your router maybe?

---

### Post by hintss on 2011-01-10
nmap can do that.

install it with:
sudo apt-get install nmap

then run it like so:
nmap -A 192.168.0-1.*

assuming all the IPs are in that range, of course.

---

### Post by cryptoxic on 2011-01-10
> **hintss said:**
> nmap can do that.

install it with:
sudo apt-get install nmap

then run it like so:
nmap -A 192.168.0-1.*

assuming all the IPs are in that range, of course.

Thanks a lot. It worked for me, I can see the hostnames.

---

