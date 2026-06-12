---
title: "Package/Update Install error"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by snowbalance on 2009-01-20
I installed 8.10 and am trying to run the updates.  It went fine until the end, when it gave me an error message:
```
E: libpam-runtime: subprocess post-installation script returned error exit status 1
```

When I try to install VLC via Synaptic, it seems to run fine until the last item, when it gives me the same error message.

I can't install any updates now at all.  Ahhh...help? :(

here's the screen I'm getting at the end of the Update install: [http://i42.tinypic.com/35i3xwy.png](http://i42.tinypic.com/35i3xwy.png)

---

### Post by Kobalt on 2009-01-20
A process is using the file "config.dat" which apt needs to access. To find out which process is using it, and eventually end it, use this command line: ```
fuser -v /var/cahce/debconf/config.dat
```

---

### Post by snowbalance on 2009-01-20
> **Kobalt said:**
> A process is using the file "config.dat" which apt needs to access. To find out which process is using it, and eventually end it, use this command line: ```
fuser -v /var/cahce/debconf/config.dat
```
Oh that's a useful command!  Here's what I get (I'm not entirely sure how to read the output):
```
jillian@LILITH4:~$ sudo fuser -v /var/cache/debconf/config.dat
                     USER        PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       6746 f.... dpkg-reconfigur

```
I looked for process 6746 in System Moniter, but I can't find it.  How would I kill this via Terminal?

---

