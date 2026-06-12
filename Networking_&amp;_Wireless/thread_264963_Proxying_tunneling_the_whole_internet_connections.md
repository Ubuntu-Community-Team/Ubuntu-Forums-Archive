---
title: "Proxying/ tunneling the whole internet connections"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by crazy_fox on 2006-09-25
Is it possible to set up an SSH tunnel or a proxy for the whole internet connection? Not just one port ..

---

### Post by DarkAngel88 on 2006-09-25
Wow, I'm looking for the exact same thing.. I guess !

I'm using right now a ssh tunnel and I use a different proxy connection for firefox but I'd like to use it for all the applications that use the internet connection.

I'll be watching this thread closely !

---

### Post by michux on 2006-09-29
> **DarkAngel88 said:**
> Wow, I'm looking for the exact same thing.. I guess !

I'm using right now a ssh tunnel and I use a different proxy connection for firefox but I'd like to use it for all the applications that use the internet connection.

I'll be watching this thread closely !

There is a few ways of achieving it. You can try to use just ssh tunneling+proxy and then set the default proxy settings for your desktop (GNOME and KDE have such options).

Another way would be to use transparent proxy with tsocks, corkscrew or httptunnel...

You can read more about those options in this editorial on [ssh tunneling](http://polishlinux.org/apps/ssh-tunneling-to-bypass-corporate-firewalls/).

Regards,
michuk

---

### Post by begemots on 2006-10-02
and how can i do, that all my programs (and all ubuntu updates and other stuff), connect to internet through my proxy?
it's possible?

ty for answer ;)

---

### Post by saxin on 2007-09-21
I also wanna know how I can do this. The proxy is a Windows 2003 server. Anyone know how I can do this?

---

