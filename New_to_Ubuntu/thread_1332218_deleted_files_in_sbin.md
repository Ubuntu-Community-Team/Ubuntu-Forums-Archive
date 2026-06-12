---
title: "deleted files in /sbin"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by lengjingmao on 2009-11-20
Hi, Guys

I made a silly mistake that I deleted the files in the /sbin fold. Now I cann't log in the system. 

My question is "is there any solution to recover this mistake rather than re-install the system"&#65311; BTW, I am using ubuntu 9.10

thanks a lot

---

### Post by 3rdalbum on 2009-11-20
It's probably theoretically possible by copying over the contents of /sbin from a live CD, but if it doesn't work then reinstalling would be your only option.

You might be interested in this old story:

[http://www.ee.ryerson.ca/~elf/hack/recovery.html]("http://www.ee.ryerson.ca/~elf/hack/recovery.html")

It's from 1986, which definitely pre-dates live CDs :-)

---

### Post by ukripper on 2009-11-20
If you already had backup of sbin folder prior to deletion  then just restore that folder, otherwise your only bet is to re-install as it would create inconsistency in your system's integrity even if you just copy it over from live cd and will create whole lot of mess, many programs won't work.

In my opinion go for re-install if you have no backup.

---

