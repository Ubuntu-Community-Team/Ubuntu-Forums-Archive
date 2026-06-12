---
title: "Updates don't work"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by mrmonday on 2007-02-15
Hi everyone,

After entering lots of commands in a terminal, I have managed to get the Internet working,  I had to disable ipv6 in firefox. However I still can't get updates working, the update manager will detect updates, but it can't download them. How do I resolve this? I access the Internet via a wireless router, if this helps. Thanks in advance.

---

### Post by dmizer on 2007-02-15
add:
blacklist ipv6

to the end of this file:
/etc/modprobe.d/blacklist

reboot and see if that helps.

---

### Post by mrmonday on 2007-02-15
Nope.  No luck.  Any other ideas? Thanks.

---

### Post by dmizer on 2007-02-15
yup ... one more:
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=howto+fix+dns](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=howto+fix+dns)

---

### Post by mrmonday on 2007-02-15
how do I find what DNS addresses to use?

---

### Post by dmizer on 2007-02-15
a number of ways.  they're usually posted on you're isp's website.  there's probably some nifty command you can type in terminal to glean them as well, but i don't know it.

but i suggest you try these: [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by mrmonday on 2007-02-15
Thanks for your help, it worked!

---

