---
title: "Telnet or ssh on by default?"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by johnnyphive on 2007-05-07
Just got to work today and need access to some stuff at home.  I haven't had a chance to get everything setup right, but i should be able to do what i need through a telnet or ssh session.  Are either of these on and enabled  by default in 7.04?

Also, what are the default ports for either of these?

---

### Post by dbott67 on 2007-05-07
Neither one is enabled by default.  As a security precaution, most services are disabled by default on Ubuntu.

Telnet should never be used, as it is very insecure (it uses port 23).

SSH is the best option (it uses port 22).
```
sudo apt-get install openssh-server
```

If you have a home-based router/NAT firewall, you will need to forward port 22 to the Ubuntu computer (or some other arbitrary port, like 9922).

-Dave

---

