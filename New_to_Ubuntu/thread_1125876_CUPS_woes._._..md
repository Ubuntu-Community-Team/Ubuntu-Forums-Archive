---
title: "CUPS woes. . ."
date: 2009-04-14
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-14
Hi!  I am having some difficulties with CUPS on my server.  Normally, I would use the web interface and be on my merry way, but I can't seem to get it working.  On the server side, I have the following in the Listen section of /etc/cups/cupsd.conf:

Listen localhost:631
Listen /var/run/cups/cups.sock

What else would I add to allow other machines to connect to the web interface remotely?  It's IP is 192.168.1.107, the router is 192.168.1.1.

I also have this problem:

travis@ubuntu-server:~$ sudo /etc/init.d/cupsys restart
sudo: /etc/init.d/cupsys: command not found


I have the metapackage cupsys. . .  What am I doing wrong?

Thanks in advance!

---

### Post by glennric on 2009-04-14
/etc/init.d/cupsys has been changed to /etc/init.d/cups in recent releases of Ubuntu.

---

### Post by pi.boy.travis on 2009-04-14
> **glennric said:**
> /etc/init.d/cupsys has been changed to /etc/init.d/cups in recent releases of Ubuntu.

Thanks!  I am surprised this hasn't changed in the official documentation. . .

---

### Post by pi.boy.travis on 2009-04-14
OK, now I get this in my web browser:

403 Forbidden

What do I do next?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-14
OK, I have added:

Listen 192.168.1.107:631

to the Listen section, but I still get:

403 Forbidden. . . 

Is there some other field I have to change?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-14
Now, I have commented out the Listen directives, and used a port directive instead:

Port 631

But I still get the:

Forbidden 403. . .

---

