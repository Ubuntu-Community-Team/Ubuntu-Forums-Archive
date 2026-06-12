---
title: "ubuntu 10.10 antivirus"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Karlof on 2010-12-14
Hi forum

klam av will not scan system files  access denied

Why/ please 

Thanks

---

### Post by Ligerzero_942 on 2010-12-14
Make sure you are using KDE and not Gnome.

---

### Post by cipherboy_loc on 2010-12-14
Make sure you run it with kdesudo. AKA:

```
kdesudo klamav
```

or while you in the terminal, you might as well use sudo:

```
sudo klamav
```

This assumes you are using KDE. If you use GNOME, then replace kdesudo with gksudo. sudo will work anywhere.



Cipherboy

---

### Post by Karlof on 2010-12-15
Hi guys 

Thanks for the info, I will let you know how I get on


Cheers Karlof

---

### Post by Karlof on 2010-12-20
Hi guys

Thanks for your help I downloaded KDE desktop  and can now use the virus scanner

Also I have managed to activate a fire wall

Cheers and seasons greetings


Karlof

---

### Post by AngusH on 2010-12-20
> **cipherboy_loc said:**
> Make sure you run it with kdesudo. AKA:

```
kdesudo klamav
```

or while you in the terminal, you might as well use sudo:

```
sudo klamav
```

This assumes you are using KDE. If you use GNOME, then replace kdesudo with gksudo. sudo will work anywhere.



Cipherboy

For the record, since klamav is a graphical app, it should always be kdesudo, whether you are launching from a terminal or an ALT-F2 prompt.

Angus

---

