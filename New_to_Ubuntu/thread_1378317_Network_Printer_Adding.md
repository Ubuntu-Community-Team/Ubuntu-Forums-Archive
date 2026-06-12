---
title: "Network Printer Adding"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-11
Just wanted to know how I would go about adding a printer to my lpoptions if lpoptions doesn't know the printer is there.

I backed up my /etc/cups as per another thread, but copying all of it back over to my current /etc/cups doesn't do anything at all.

Also, how do I start the hplip service? sudo start hplip doesn't do anything.

Also, I'd rather not resort to using a GNOME Application to deal with this, GNOME 3 is coming, and I don't want anything to do with it, so I need to know how to do this myself.

---

### Post by Temposs on 2010-01-11
You know you don't have to upgrade your GNOME when GNOME 3 comes out, if you don't want to...Ubuntu 9.10 will not be upgrading to GNOME 3 at all, in fact.

---

### Post by Psumi on 2010-01-11
> **Temposs said:**
> You know you don't have to upgrade your GNOME when GNOME 3 comes out, if you don't want to...Ubuntu 9.10 will not be upgrading to GNOME 3 at all, in fact.

Of course not, but in 11.04, it will have it. I will be using 10.04 mini.iso once more before that. I don't wish to fall behind in versions either.

---

### Post by Psumi on 2010-01-15
Bump

---

### Post by Psumi on 2010-01-20
Bump

---

### Post by Morbius1 on 2010-01-20
I don't know if this will help you but you could use CUPS itself:

Open your favorite browser and enter: **localhost:631**

Select "adding printers" > Add printer

It's independent of any desktop environment.

---

### Post by Psumi on 2010-01-20
> **Morbius1 said:**
> I don't know if this will help you but you could use CUPS itself:

Open your favorite browser and enter: **localhost:631**

Select "adding printers" > Add printer

It's independent of any desktop environment.

I'll try that next time I'm on xfce.

---

### Post by Psumi on 2010-01-23
Yep, works :3

Now I can print from firefox without having to go through all that gnome jazz.

---

### Post by SimonBishop on 2011-09-20
Nice One, Morbius1!!=D>

---

