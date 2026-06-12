---
title: "Could not open ftp in nautilus"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by shredder12 on 2009-08-20
I jst installed xubuntu 8.04 on an old machine and when I tried to download stuff from my main computer using ftp. It showed that nautilus couldn't handle ftp..

I am able to the same thing in ubuntu. So, why am I getting such  problem in xubuntu..
some help please..

---

### Post by Paddy Landau on 2009-08-20
Xubuntu doesn't use nautilus by default. It uses a different file manager called Thunar.

I don't know whether your problem is a limitation of Thunar, or some other reason.

You can install nautilus from Synaptic Package Manager, if you like, or you can try an FTP manager like Filezilla (also from Synaptic Package Manager).

Unless someone else can tell you how to get Thunar to work with FTP.

---

### Post by shredder12 on 2009-08-20
Ya, I knew about Thunar and that's why I installed nautilus and tried to open the ftp but then a message popped up and said..

```
Couldn't open location ftp://ip/
 Nautilus can't handle ftp locations
```

So, is this some kind of problem with nautilus

---

### Post by oldos2er on 2009-08-20
> **shredder12 said:**
> Ya, I knew about Thunar and that's why I installed nautilus and tried to open the ftp but then a message popped up and said..

```
Couldn't open location ftp://ip/
 Nautilus can't handle ftp locations
```So, is this some kind of problem with nautilus

 Omit the "ftp://" and type in just the name of the site, e.g. ftp.idsoftware.com.

---

### Post by shredder12 on 2009-08-20
i jst used the ip and again nautilus gave error..
saying "please check the spelling and try again"

---

### Post by Paddy Landau on 2009-08-21
Hmm, I've just tested this on nautilus (Ubuntu Hardy).

The first one didn't work (Nautilus cannot handle this type of location), but the second two both worked.
```
213.171.195.64
ftp://213.171.195.64
ftp://213.171.195.64/
```So, sorry, I can't tell you the problem.

---

