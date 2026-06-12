---
title: "xampp, swat and accessing using localhost:901"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by ubuntumaybe on 2009-05-18
Hi,

I have installed xampp and swat for samba. When I enter localhost at the url I get the xampp setup. When I enter localhost:901 which is suggested for swat I get an error. How do I get into swat using xampp? Thanks.

---

### Post by cariboo on 2009-05-19
You have to start firefox as root, then enter:

```
http://localhost:901
```

in the address bar. To start Firefox as root, make sure it isn't running, then press Alt-F2 and type:

```
gksu firefox
```

Once you have used swat to set up your shares, please disable swat, as I feel it is a security problem.

---

### Post by ubuntumaybe on 2009-05-20
Hi,

I found a page about update inetd and it worked ok. Thanks.

---

