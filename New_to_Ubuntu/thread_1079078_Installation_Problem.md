---
title: "Installation Problem"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Morphaeus on 2009-02-24
I have been trying to install Banshee from Add/Remove, however, when I try to, I get the following error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

How do I remedy this?

Thank you in advance

---

### Post by balaknair on 2009-02-24
Open a terminal(Applications menu> Accessories> Terminal) and enter the following command
*sudo dpkg --configure -a*

Type in your password when prompted(when entering the password you will not see any *** appear, that's normal, just type it in and press enter).

---

### Post by Morphaeus on 2009-02-24
I did as you suggested but I got an error at the Terminal:

```
dpkg: requested operation requires superuser privilege
```

I am quite new to Ubuntu, and I don't understand what that means. How do I get 'superuser' priviledges?

---

### Post by snova on 2009-02-24
> **Morphaeus said:**
> I did as you suggested but I got an error at the Terminal:

```
dpkg: requested operation requires superuser privilege
```

I am quite new to Ubuntu, and I don't understand what that means. How do I get 'superuser' priviledges?

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You should only get that if you don't use sudo, as so:

```
sudo dpkg --configure -a
```

---

### Post by Morphaeus on 2009-02-24
I could've sworn I typed it in correctly before but idk. It worked after I tried it again.

Thank You!

---

