---
title: "Unable to access ports over internet"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by jakobvjgmail.com on 2016-04-13
Hi
Im new to Ubuntu..
I have a virtual machine with Ubuntu 14.04.
I just can't seem to acces fx port 8080.. Everything i Ping is closed...
But im connecting over rdp and that port is also closed when i ping it..
Here is the result from ufw status

[IMG]http://i67.tinypic.com/16lh6av.png[/IMG]

Hope someone can help.

Regards
jakob

---

### Post by SeijiSensei on 2016-04-13
Is something listening on that port?  If not, it will appear closed.

---

### Post by jakobvjgmail.com on 2016-04-13
If i telnet localhost 80, i get connection refused...

I can ping port 22 and 3389, and they are 0.0.0.0:22, 0.0.0.0:3389, but all the others are 127.0.0.0

---

### Post by jakobvjgmail.com on 2016-04-13
I found the problem...
Had a error in my nginx config.. So the nginx could not be started... So port 80 was closed

---

