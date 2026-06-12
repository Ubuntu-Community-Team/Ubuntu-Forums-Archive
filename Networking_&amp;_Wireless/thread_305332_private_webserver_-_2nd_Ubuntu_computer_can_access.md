---
title: "private webserver - 2nd Ubuntu computer can access localhost"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by craig.brisbane on 2006-11-23
I'm new to linux. I have a small network consisting of 2 windows 2000 computers and 2 computers running ubuntu. I have set one ubuntu computer up as a webserver. I have samba running on across the network to share files, which is working. 

The windows computers can access the computer acting as the server when I enter 'localhost' in the browser, the 2nd computer running ubuntu can't. When I enter the ip address of the computer acting as the server in the 2nd ubuntu computer it can access the server, but when I enter locahost - no luck.

Any suggestions how I can get the computer running ubuntu to access the server when I enter localhost?

Thanks 
craig

---

### Post by Jimmey on 2006-11-23
You could try doing it by hostname. 
If you enter your server's hostname under "Hosts" in System>Administration>Networking on the second Ubuntu machine, you could connect to the server by it's hostname.

If not, you could try the socket address - "localhost:80".

---

### Post by craig.brisbane on 2006-11-23
Tks Jimmey your first suggestion appeared to fix the problem - now the second ubuntu computer can access the server via the browser.

Regards
Craig

---

### Post by scxtt on 2006-11-23
you can't use "localhost" to connect to your server if the box isn't the webserver ... "localhost" is an alias for 127.0.0.1 which is ALWAYS the loopback device which is ALWAYS the box you're typing [http://localhost](http://localhost) into ... so Jimmey's suggestion is the ONLY way you can do it ...

---

