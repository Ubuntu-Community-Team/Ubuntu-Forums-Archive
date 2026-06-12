---
title: "How To Figure Out Ip"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by l0fls on 2008-07-04
i need to figure out my ip when i say ip i dont mean like actual ip
like 192.168.1.?
so i can open ports for my bit torrent client on my laptop on a windows machine i would do ipconfig
what can i do on a ubuntu machine?

---

### Post by 505 on 2008-07-04
On linux you use ifconfig But if your on a local network, this is only your local IP, not the IP the outside world sees.

---

### Post by Kevbert on 2008-07-04
If you mean primary DNS address right-click on the connection in the top right-hand corner of the desktop and select connection information.

---

### Post by marialice on 2008-07-04
> **505 said:**
> On linux you use ifconfig But if your on a local network, this is only your local IP, not the IP the outside world sees.

For the IP the outside world sees you can browse to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) (works on every OS, and is easy to remember).

---

### Post by l0fls on 2008-07-04
thats exacly what i need ty :)

---

### Post by l0fls on 2008-07-04
i typed ipconfig into terminal didnt work

---

### Post by kevdog on 2008-07-04
Cut and paste this command into the terminal to get your external IP address:

wget -q -O - [http://showmyip.com](http://showmyip.com) | grep -m 1 'IP' | awk '{ print $8 }'

---

### Post by l0fls on 2008-07-04
im looking for internal ip

---

### Post by Rui Pais on 2008-07-04
> **l0fls said:**
> i typed ipconfig into terminal didnt work

> **l0fls said:**
> im looking for internal ip

i**_f_**config

Somethign like:
```
ifconfig eth0 |grep inet
```
(or replace eth0 by your network device)

---

### Post by bluzepher on 2008-07-04
> **marialice said:**
> For the IP the outside world sees you can browse to [http://whatismyipaddress.com/](http://whatismyipaddress.com/) (works on every OS, and is easy to remember).

this is slick,

I have 3 computers connected to my router and they all have the same ip address when I use the link.

---

### Post by Rui Pais on 2008-07-04
> **bluzepher said:**
> this is slick,

I have 3 computers connected to my router and they all have the same ip address when I use the link.

Thats because that link gives the IP that your net provider assigns to you when navigate on internet (through the same router and Internet connection).
Your 3 machines will have 3 different **internal** IPs.

---

