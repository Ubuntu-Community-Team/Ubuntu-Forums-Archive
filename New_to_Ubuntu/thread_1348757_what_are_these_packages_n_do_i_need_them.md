---
title: "what are these packages n do i need them??"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-07
the following packages have been kept back:
 [B] bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50
  liblwres50[/B]
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by nothingspecial on 2009-12-07
Depends on weather you`ve got anything installed that depends on them.

---

### Post by JamesParnell on 2009-12-07
can i find out what uses them, if anything.

---

### Post by nothingspecial on 2009-12-07
Very easy answer.

Are you seeing this message after using apt-get?

Have you ever used dpkg or compiled from source?

If the answer to the first question is yes and the second is no....


..... then you can remove them.

---

### Post by JamesParnell on 2009-12-07
> **nothingspecial said:**
> Have you ever used dpkg or compiled from source?

HA, like i know how to do that. i guess i can remove them then, thanks for the help

---

### Post by SuperSonic4 on 2009-12-07
> **JamesParnell said:**
> HA, like i know how to do that. i guess i can remove them then, thanks for the help

If you used aptitude, synaptic or software centre then you used dpkg

if not you installed from source

Of course it's rarely *that* simple but it's a good rule of thumb

---

### Post by nothingspecial on 2009-12-07
> **JamesParnell said:**
> HA, like i know how to do that. i guess i can remove them then, thanks for the help

Yes you can. That`s part of the point of a package manager. If it`s telling you that you don`t need the packages then you don`t.

Of course, if you have a lot of free space, and leave them there, then you won`t need to download them next time you install an app that depends on them. My way of doing things is to leave them there. 

But then this is linux, do what you will;)

---

