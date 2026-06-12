---
title: "DNS no longer works after upgrade to 14.04"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by mandevillem on 2014-06-19
Hello,

I took the plunge and recently updated a 12.04 machine to 14.04.  Immediately after, I still had a connection (I can ping both internal and external IPs), but DNS seems to have died on me.  I've attempted to stop/start networking, checked to make sure DHCP is giving all the info it should, but even with network manager insisting I have a valid IP and the correct DNS servers, still nothing.  I tried using 8.8.8.8 and 8.8.4.4 with no luck.  Having verified everything in resolvconf looks kosher, not really sure what else to say.

Thoughts?

---

### Post by steeldriver on 2014-06-19
Hello and welcome to the forums

How exactly is DNS lookup failing? is it failing to find a DNS server, or is it finding a server but not returning any record for the query?

Is dnsmasq running? what does 'dig google.com' or 'dig ubuntuforums.org' say? what about 'dig @8.8.8.8 google.com'?

---

### Post by mandevillem on 2014-06-19
Thanks for the reply,

A simple dig google.com says no servers could be reached, while dig @8.8.8.8 google.com found one server, then gives me all the google addresses in the 'answer' section.

---

### Post by steeldriver on 2014-06-19
Can you post

```

ls -l /etc/resolv.conf

cat /etc/resolv.conf

sudo lsof -i :53

```

---

### Post by mandevillem on 2014-06-20
It appears I have no /etc/resolv.conf.  I do have the resolvconf directory however, with files labled base, head, and original. 

lsof -i :53 shows the following (replaced my machine's name with hostname, obviously)

dnsmasq 2478 nobody    4u  IPv4  16608      0t0  UDP hostname:domain 
dnsmasq 2478 nobody    5u  IPv4  16609      0t0  TCP hostname:domain (LISTEN)

---

### Post by steeldriver on 2014-06-20
Try reconfiguring the resolvconf package

```

sudo dpkg-reconfigure resolvconf

```

It will present you with a question about preparing /etc/resolv.conf for dynamic updates - answer "Yes". It may also present you with another question about temporarily appending your existing config to the dynamic one - I suggest answering "No" to that one.

---

### Post by mandevillem on 2014-06-20
Did it, annnnd it's working again!  Thank you for both the help, as well as the lesson :D

---

