---
title: "Accessing other computers shared files"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by kohlerbn on 2006-12-26
Hello all, I am rather new networking in ubuntu. I want to know if there is good software out there or how I should go about accessing my Windows computers files that are shared on the same network that I am on. Thanks for your help.

---

### Post by kidders on 2006-12-26
Samba is the usual. Afaik client-side samba support is built into Ubuntu, so all you need to do is mount your shares. If it's not installed, "apt-get install samba" should do the trick :-)

You might want to add some shares to your /etc/fstab to make your life easier. I would suggest using the "noauto" mount option though, since your Windows box might not always be on.

---

### Post by scrooge_74 on 2006-12-26
> **kidders said:**
> Samba is the usual. Afaik client-side samba support is built into Ubuntu, so all you need to do is mount your shares. If it's not installed, "apt-get install samba" should do the trick :-)

With that you will installing the server side so your win machine can see your files on the linbox

---

### Post by kidders on 2006-12-26
Oops... I don't suppose kohlerbn needs to do that. Are smbtree, etc. installed by default? (I can't remember!) It occurred to me that they *might* be in the samba package (or a dependency), but perhaps not.

---

### Post by scrooge_74 on 2006-12-26
> **kidders said:**
> Oops... I don't suppose kohlerbn needs to do that. Are smbtree, etc. installed by default? (I can't remember!) It occurred to me that they *might* be in the samba package (or a dependency), but perhaps not.

i think samba tree comes with the server side of samba.  Anyway it is a good learning tool, after you pass the frustration of your win Pc not loggin correctly :D

I learn samba the hard way, did not know of the ubuntu forums so I had to relay on the documentation at [http://www.samba.org](http://www.samba.org)

kohlerbn you should also try to setup your lijnbox so the Winbox can see files and things like that.

Have fun! i know I did in the end :D

---

### Post by kohlerbn on 2006-12-26
thanks guys!

---

