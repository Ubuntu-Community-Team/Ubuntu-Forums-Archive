---
title: "DNS errors?"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by nosduha on 2008-04-10
Hi I am a newbie and currently experimenting with Edubuntu on our school network. I have connected a laptop with Edubuntu installed and it picks up DHCP from our Windows 2003 server. My problem is that I can ping the router and external IP addresses but cannot load a page in firefox. I have tried to change the dns settings to an external server but to no avail. Any help would be greatly appreciated.

---

### Post by SpaceTeddy on 2008-04-10
have you tried to manually lookup hostnames ? 
```
nslookup www.google.de
```

you might need to install an extra package for that to work. you can do that with
```
sudo apt-get install dnsutils
```

also, are you sure that there is no proxy inbetween you and the internet, which you might have to configure on the ubuntu box ?

---

### Post by cbobb@alinean.com on 2008-04-10
Verify that you have connectivity to the outside world.  ping this IP which is one of the Root DNS servers 4.2.2.2.  If you cannot ping that IP then you have limited or blocked ip traffic on your network outbound.  Also verify that you have a dns nameserver entry in your /etc/resolv.conf and if you have a server there be sure you can ping it and get a reply also.

Just a few things to try for verification.

---

