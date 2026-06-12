---
title: "Can't access Server Using name"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by travislepp on 2006-11-08
Hi All,

My problem is really quite a simple one, I can connect to my Dapper box (server install) using the IP address, but can't use the name of the machine (laptop).  I'm sure its a very easy solution but after two days of searching forums and trying everything I simply can't get it to work.

I have set it up as a static address etc.

Thanks for reading my problem any suggestions would be a great help.

Cheers,
Travis

---

### Post by lloyd_b on 2006-11-08
Have you added "laptop" to your "/etc/hosts" file?  Adding a line for "laptop" to this file will allow that machine to access it by that name.

Lloyd B.

---

### Post by travislepp on 2006-11-12
Cheers Lloyd_B, 

Actually I think it's something wrong with the DNS in my router...I remember reading it somewhere.  Thanks for your help.

Travis

---

### Post by stream303 on 2006-11-12
Adding your isp's nameservers to your router's setup might help.

You could also add these via the Networking administration tabs or edit /etc/resolv.conf manually, especially if you are running static.  Be sure to check your gateway so that it uses your router's address as the gateway.

---

