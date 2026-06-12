---
title: "mrtg package issue"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by ask123 on 2009-09-26
Hi,
I've istalled ubuntu server, and now want to install mrtg package,
I've done this 'apt-get install snmpd mrtg apache2', two package installe succesfuly (snmpd&apache2) but mrtg package say this "Package mrtg is not available, but referred to by another package....bla-bla-bla Package mrtg has no installation candidate", as I understand it's going to get MRTG package from the url:[http://ru.archive.ubuntu.com/](http://ru.archive.ubuntu.com/), and I suppose it's really missing there, so can you tell me how can I change repositary or some another way to fix me problem. thx in advace

---

### Post by yeats on 2009-09-26
strange... this is available in the [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) repository for jaunty.  What version are you running?

---

### Post by ask123 on 2009-09-26
it's ubuntu-8.10-server-i386, so how can I change repositary to US, is that posible?

---

### Post by ask123 on 2009-09-27
I've already add to sources.list this
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty net universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty net universe

nothing changes, it's stil can't install mrtg

---

### Post by yeats on 2009-09-27
okay - what is the output of 

```
apt-cache search mrtg
```

?

---

### Post by ask123 on 2009-09-27
apt-cache search mrtg --> Nothing in the output
And one more thing, when I installing Ununtu server, it stuck at about 43% when
Configuring the Apt 43% scanning the mirror
After 30 min of waiting I just disable network card (it's on wmware) , after this installation was finished succesfuly. Might be it a reason

---

### Post by benow on 2011-07-22
Yeah, this is an ancient thread, but the issue is that mrtg is in universe.  You need to enable the universe repository via gui or add

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe

(or similar) to /etc/apt/sources.list.

---

### Post by bapoumba on 2011-07-22
Now that the answer has been given, I'll close this (almost 2 years old) thread.

---

