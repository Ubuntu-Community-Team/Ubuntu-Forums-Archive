---
title: "Samba Homedir Question."
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by voide on 2007-09-25
Hello Everyone!
I'm running Linux Ubuntu, i've managed to configure and i'm able to log in to my active directory created accounts, my only problem is that i want that my user HOME directory is saved into my server, let's say smb://master01/%u so that all the user account documents can be saved there, because right now the user's home are /home/domainname/%U.
So i've tried to change smb.conf to both::

```
logon path = smb://master01/%U
```

and also

```
template homedir = smb://master01/%U
```


Since i'm not sure to which one to use.

What i'm i doing wrong? Or isn't it possible?

Thank you for your time.

---

### Post by helgman on 2007-09-25
> **voide said:**
> 
So i've tried to change smb.conf to both::

```
logon path = smb://master01/%U
```

and also

```
template homedir = smb://master01/%U
```

Have you tried:

```
logon path = \\master01\%U
```

I'm not sure if samba swings both ways ... and I don't have enough machines running at the moment to test.

For more information about samba try *[Using Samba, 2nd Edition](http://www.faqs.org/docs/samba/toc.html)* by Jay Ts, Robert Eckstein, and David Collier-Brown.

Regards,
Helgman

---

