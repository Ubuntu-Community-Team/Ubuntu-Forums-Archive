---
title: "New installation of 16.04 Server, can SSH but can't reach ispConfig"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by Robert_Boutin on 2016-08-11
I just reinstalled Ubuntu 16.04 Server using the instructions at:

[https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/)

The installation seemed to go fine.  I connected to ispConfig to begin setting things up.  However, a short time later, I was unable to reconnect from inside and outside my home network.  Forget port 8080, I now can't even enter the ip to get the Apache2 Ubuntu Default Page.

SSH/port 22 works with no problem but entering my server ip into my browser gives me:

[B]Unable to connect

Firefox can’t establish a connection to the server at XX.XX.XX.XX.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer’s network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.[/B]

I disabled ufw and fail2ban thinking maybe one of those was blocking the connection from my laptop, but no dice.

Any quick thoughts on why I was able to reach ispconfig, and then suddenly I'm being blocked?

Thanks

---

