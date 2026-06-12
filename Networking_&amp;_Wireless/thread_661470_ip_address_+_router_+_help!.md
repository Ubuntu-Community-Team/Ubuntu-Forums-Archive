---
title: "ip address + router + help!"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by taehC on 2008-01-07
how do i find my computer's ip address.  i have a router and when i plug the main internet cable into my computer i want to find the ip address of it cant connect to the internet.  Is there any way to find my computer's ip address even though there is a router hooked up?

---

### Post by zipperback on 2008-01-07
> **taehC said:**
> how do i find my computer's ip address.  i have a router and when i plug the main internet cable into my computer i want to find the ip address of it cant connect to the internet.  Is there any way to find my computer's ip address even though there is a router hooked up?


You can find your outside ip address several different ways.
Log into your router and see what ip address it has, or you can point your web browser to [http://whatismyip.com](http://whatismyip.com)

For your locally assigned ip address of your network card you can use.

```

ifconfig
iwconfig

```

-zipperback
:popcorn:

---

### Post by taehC on 2008-01-07
when i type ifconfig it gives me alot of stuff.  which thing is my computer's ip?

---

### Post by taehC on 2008-01-07
is it the 
inet addr:
the
bcast:
or the
mask:
those are the 3 that are the possible choices(the address comes after those words in the real file)
in other words the file says
```

blahblahblahblahblahblahblahblahblahblahblahblahblahblah
inet addr: (some address) bcast: (address) mask: (address)
blahblahblahblahblahblahblahblahblahblahblahblahblahblahblah
blahblahblahblahblahblahblahblahblahblahblahblahv
blahblahblahblahblahblahblahblahblahblahblahblahblahblah
blahblahblahblahblahblahblahblahblahblahblahblahblah

```
which address is my computers ip?

---

### Post by wieman01 on 2008-01-08
> inet addr:
...is your IP address.

---

