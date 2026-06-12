---
title: "firewall?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by als123 on 2010-01-08
Hi,

Can someone recommend an easy to manage firewall?  I've used firestarter, but it wasn't for me.  I've just jumped the fence into linux land and may still be carrying some windows paranoia baggage.

Thanks

---

### Post by als123 on 2010-01-08
My big concern is these java problems such as drive by fishing and such.  Does firefox or ubtuntu prevent this by default?

---

### Post by Muttley99 on 2010-01-08
Linux is not blessed with a big choice of firewalls. Firestarter is the front end for iptables. Iptables is very powerfull and can do anything any windows firewall can do. But you need to use the command line. There are one or two other firewalls for linux which I don't use, so I'm not in a position to help. I didn't like firestarter either when I moved from XP but after using it for a while realised its all you may need.

---

### Post by bodhi.zazen on 2010-01-08
> **als123 said:**
> My big concern is these java problems such as drive by fishing and such.  Does firefox or ubtuntu prevent this by default?

Use NoScript =)

[http://noscript.net/](http://noscript.net/)

For a firewall, assuming you need one (what do you want a firewall for exactly ? ), use ufw

```
sudo ufw enable
```

For more information see :

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by als123 on 2010-01-08
I really don't know what I need a firewall for.  I've always had them with windows and they always gave me messages while I was surfing the web that they were stopping intruder attacks, so I guess I need one.

---

### Post by bodhi.zazen on 2010-01-08
> **als123 said:**
> I really don't know what I need a firewall for.  I've always had them with windows and they always gave me messages while I was surfing the web that they were stopping intruder attacks, so I guess I need one.

On Windows, yes, not the same need on Linux though.

---

### Post by Sef on 2010-01-08
>  Iptables is very powerfull and can do anything any windows firewall can do

Iptables is installed by default on Ubuntu.

---

### Post by als123 on 2010-01-27
Thanks for all your responses.  I installed Gufw 9.10.4, which as i understand it, uses pitables.  Anyway, while reading the documentation, it offers the uses of the shieldsup web site.  

I guess that was what i was looking for, confirmation that linux is secure.

---

