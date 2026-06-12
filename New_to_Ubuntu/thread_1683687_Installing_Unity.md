---
title: "Installing Unity"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by joenewtzie on 2011-02-07
I am running the Netbook Edition of Ubuntu 10.04 (lucid)
In terminal I ran:

sudo add-apt-repository ppa:canonical-dx-team/une

sudo apt-get update

sudo apt-get install unity

At sudo apt-get Install unity I get in return:
"E: Couldn't find package unity"

Any ideas what I might be doing wrong?

---

### Post by wojox on 2011-02-07
Here:

```
sudo apt-get install ubuntu-netbook-unity-default-settings
```

---

### Post by joenewtzie on 2011-02-07
> **wojox said:**
> Here:

```
sudo apt-get install ubuntu-netbook-unity-default-settings
```

I get this after I put that in terminal:


E: Couldn't find package ubuntu-netbook-unity-default-settings

---

### Post by beyboo on 2011-02-08
> **joenewtzie said:**
> I get this after I put that in terminal:


E: Couldn't find package ubuntu-netbook-unity-default-settings

sudo apt-get install ubuntu-netbook

---

### Post by joenewtzie on 2011-02-08
> **beyboo said:**
> sudo apt-get install ubuntu-netbook

After that I get this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-netbook is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by P4man on 2011-02-08
I think unity is for 10.10 only?
Either way, to get the netbook interface, just log out, and in the login screen at the bottom in "session" select netbook interface.

---

### Post by joenewtzie on 2011-02-08
> **P4man said:**
> I think unity is for 10.10 only?
Either way, to get the netbook interface, just log out, and in the login screen at the bottom in "session" select netbook interface.

Oh shoot I think you are right.
Isn't there a command I can run in the update manager to upgrade from 10.04 netbook to 10.10?

---

### Post by joenewtzie on 2011-02-08
> **joenewtzie said:**
> Oh shoot I think you are right.
Isn't there a command I can run in the update manager to upgrade from 10.04 netbook to 10.10?

Because of I do Alt+F2 and type in "update-manager -d" then it goes "new ubuntu release 10.10 is available" but won't that install the desktop version of 10.10 and I just want the netbook edition of 10.10 like I have now.  Or do I just have my information screwed up?

---

### Post by P4man on 2011-02-08
there is no real difference between netbook and regular version, except for the interface/unity. I suspect upgrading the netbook interface to 10.10 will give you unity, but even if not, its just a simple command to add it.

be adviced, Ive found unity to be completely unworkable with ATI cards, and generally, not ready for daily use even on my intel machine, but YMMV. Id suggest trying the livecd first and see if you like it before doing an upgrade, since its irreversible.

---

### Post by joenewtzie on 2011-02-08
Yeah, I have been doing some more research and i've been hearing bad things about Unity now.  Good idea with the live CD I might just try that and compare differences.

---

