---
title: "gksu nautilus error message"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by zazlox on 2010-12-14
hi everybody

when i use " gksu nautilus"

i get this message on terminal

```
Initializing nautilus-gdu extension
Initializing nautilus-image-converter extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10290): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files



```well , i'm using only ubuntu , i'm not using samba , i don't need it , so it means that i'm not sharing any folders.

please, how can I fix this without installing samba or net usershare.

I really appreciate any help

---

### Post by mr clark25 on 2010-12-14
> **zazlox said:**
> hi everybody
```
Initializing nautilus-gdu extension
Initializing nautilus-image-converter extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10290): **WARNING** **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files



```

that is just a warning, and it is nothing to worry about.

---

### Post by rburkartjo on 2010-12-15
zaz this might help

[http://art.ubuntuforums.org/showthread.php?t=566572](http://art.ubuntuforums.org/showthread.php?t=566572)

---

### Post by zazlox on 2010-12-15
Thanks a lot, but why shall I install samba , if i'm not going to use it or need it

because as I said , i'm not using any other OS . to share folder with.

---

### Post by MooPi on 2010-12-15
Samba is installed by default with nautilus I believe. I don't use nautilus and samba is not installed on my system.

---

### Post by zazlox on 2010-12-15
> **MooPi said:**
> Samba is installed by default with nautilus I believe. I don't use nautilus and samba is not installed on my system.

how can I remove samba from my system , i'm using lucid

---

### Post by mc4man on 2010-12-15
> how can I remove samba from my system , i'm using lucid 
open up synaptic, search samba and remove 'samba', you could also remove nautilus-share if inclined (will show up in samba search. 
I'd leave samba-common
But as mentioned, if gksudo nautilus is working, (a root file browser opens), then what you see in the terminal doesn't matter.

When I used to use gksudo nautilus I'd open from the run dialog instead of in a terminal - 
Alt+F2, type in gksudo nautilus, click run (see screen

What you may like instead is to install  is nautilus-gksu, this will give you a right click - "Open as administrator" on files and folders

---

### Post by zazlox on 2010-12-15
> **mc4man said:**
> open up synaptic, search samba and remove 'samba', you could also remove nautilus-share if inclined (will show up in samba search. 
I'd leave samba-common
But as mentioned, if gksudo nautilus is working, (a root file browser opens), then what you see in the terminal doesn't matter.

When I used to use gksudo nautilus I'd open from the run dialog instead of in a terminal - 
Alt+F2, type in gksudo nautilus, click run (see screen

What you may like instead is to install  is nautilus-gksu, this will give you a right click - "Open as administrator" on files and folders

thanks a lot , it worked :D

---

