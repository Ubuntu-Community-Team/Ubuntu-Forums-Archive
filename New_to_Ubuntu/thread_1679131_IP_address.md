---
title: "IP address"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by techningeer on 2011-01-31
I need to know what my IP address is on an Ubuntu 10.04 server. I use DHCP, so to use the server I have to use the IP address. Is there any command to tell me?
Thanks!
--techningeer

---

### Post by CharlesA on 2011-01-31
Run this from the console:

```
ifconfig
```

If you are using DHCP, you can get a reservation, so that it gets the same IP address each time.

---

### Post by techningeer on 2011-01-31
How do I reserve an IP address?

---

### Post by CharlesA on 2011-01-31
It depends on what type of DHCP server you have running. It might be called a "static lease" that is based on the MAC of the network card.

---

### Post by techningeer on 2011-01-31
I am using the Internet System Consortium DHCP client version 3.1.3. How do I reserve an IP address?

---

### Post by CharlesA on 2011-01-31
You'd need to do it on the DHCP server, not the client. If you are using a router to do DHCP, it should be somewhere.

---

### Post by lisati on 2011-01-31
There are options, e.g.
```
wget http://lisati.homelinux.com/myip && cat myip
```

(/me scurries off to look up the option for wget to overwrite the downloaded file.....)

---

