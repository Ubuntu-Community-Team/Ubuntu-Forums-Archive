---
title: "Challenge installing packages behind a Proxy Firewall"
date: 2016-07-20
forum: Networking &amp; Wireless
---

### Post by darts2 on 2016-07-20
Hi All,

I am currently trying to install a package (# apt-get install gnome-system-tools) however I am receiving a networking (related error). I am behind a Proxy firewall, but port 80 should be open. Is there another port that Ubuntu typically uses to retrieve packages? Here is a screen shot of part of the error that I am receiving -

[IMG]http://i67.tinypic.com/wl26no.jpg[/IMG]

Any help with overcoming this error will be greatly appreciated.

Kind Regards,

Davo

---

### Post by darts2 on 2016-07-20
Hi All,

Just answered my own question, from the terminal used: # http_proxy=http://[URL]:[Port] apt-get install gnome-system-tools

Kind Regards,

Davo

---

