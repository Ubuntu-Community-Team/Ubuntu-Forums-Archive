---
title: "Conky Questions"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Doman on 2009-07-02
I've a pretty decent conky script going (and I'll probably post a screenshot when I'm done) but I've two things I really want that I can't seem to find.

ibm_temps in °F, not °C.

and the ability to break network usage down to processes. Something like:
```
${top_downspeed eth1 name 1}@${top_downspeed eth1 downspeedf 1}
${top_upspeed eth1 name 1}@${top_upspeed eth1 upspeedf 1}
```
If it should exist.

Anyone?

Thanks,
Doman

---

### Post by sailthesea on 2009-07-02
Did you look through the conky screenshots sticky here?
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)
you can find and cherrypick pretty much anything out these
Just fired up conky and its a great source of info its a large thread though check dates distros and hardware for your needs
Good luck!

---

### Post by Doman on 2009-07-02
I've been going through there and there are hundreds of pages.  Any more specific help?

---

### Post by spillin_dylan on 2009-07-02
One thing I can think of off the top of my head is a small Perl or Python script to actually calculate the values from the deg C to deg F using (5/9) + 32 (or something super close to that...) 

There might be an option in Conky to do this, but IIRC it is just getting the values from a /etc/acpi/...  file or something along those lines, and I'm pretty sure those are in celsius to begin with..

---

### Post by Doman on 2009-07-03
Discarded the former.  Anyone for the latter?

---

