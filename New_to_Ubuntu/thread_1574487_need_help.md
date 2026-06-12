---
title: "need help"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by salvage0989 on 2010-09-14
i just upgraded my 10.04 ubuntu to 10.10 but i cannot get it to start 
 
it came up with 
user 
password 
 
got tue wit that part but i don't know wat to do next

---

### Post by salvage0989 on 2010-09-14
plz help

---

### Post by TonKi on 2010-09-14
Login with your user and password and remove /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf

then reboot and you should run on the generic drivers, proprietary (ati I know) dont work at the moment in 10.10 BETA. So there will be probably no 3D, compiz...

---

### Post by salvage0989 on 2010-09-14
if i were to change my os which is the best u suggest

---

### Post by Jazzy_Jeff on 2010-09-14
I would stick with 10.04. Why did you upgrade to 10.10 when it is a beta? You should only do this if you know what you are doing and want to help test it.

---

### Post by salvage0989 on 2010-09-14
is there a way 2 revert back 2 10.04 easily

---

### Post by Jazzy_Jeff on 2010-09-14
> **salvage0989 said:**
> is there a way 2 revert back 2 10.04 easily

No, you will have to do a clean install. I hope you have all your important files backed up. If not you can do it with the Live CD. Let us know if you need help with this.

---

### Post by coffeecat on 2010-09-14
The only way is to reinstall. If you have files to backup you'll need to do this with the live CD. If you need help, post back.

---

### Post by salvage0989 on 2010-09-14
i got this thanks

---

### Post by coffeecat on 2010-09-14
> **salvage0989 said:**
> i got this thanks

Eh?

If you're referring to Jazzy_Jeff and I saying more or less the same thing, we posted within seconds of each other.

---

### Post by TonKi on 2010-09-14
If you installed / and /home on different partitions, you could reinstall and keep the /home partition (no format), so you would keep your user data, settings etc..

Also recommended for a new install

---

### Post by jtarin on 2010-09-14
[

---

### Post by Jazzy_Jeff on 2010-09-14
> **jtarin said:**
> [

I understood him just fine. Oh, you came in and changed what you said...hehe.

---

### Post by jtarin on 2010-09-14
> **Jazzy_Jeff said:**
> I understood him just fine. Oh, you came in and changed what you said...hehe.

Was there a survey posted?

---

