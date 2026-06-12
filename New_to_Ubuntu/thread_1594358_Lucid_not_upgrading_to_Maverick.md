---
title: "Lucid not upgrading to Maverick"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-10-12
Well, that kinda says it all really. Lucids not upgrading to Maverick

---

### Post by Ctrl-Alt-F1 on 2010-10-12
> **LunaticHiatus said:**
> Well, that kinda says it all really. Lucids not upgrading to Maverick
I suggest a clean install.

However, here are some basic instructions for upgrading.  If you've already done this, then please let us know.

[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server)

Good luck.

---

### Post by LunaticHiatus on 2010-10-12
> **Ctrl-Alt-F1 said:**
> I suggest a clean install.

However, here are some basic instructions for upgrading.  If you've already done this, then please let us know.

[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server)

Good luck.

yeah, I tried that. Clean install isn't really going to happen. I have like 450 gigs being used and I have no external hard drive.
It updates fine, but its not offering me the "upgrade" tab

---

### Post by LunaticHiatus on 2010-10-12
I am trying

sudo do-release-upgrade

we will see if that works

---

### Post by philinux on 2010-10-12
```
update-manager -d

```
Is the usual way.

---

### Post by LunaticHiatus on 2010-10-12
yeah, seems that that is working. I think one of my other repositories (wine or google maybe) was keeping it from upgrading because it was broken. Apparantly ubuntu disabled it when I did the sudo do-release-upgrade

---

### Post by Nodaki on 2010-10-13
> **Ctrl-Alt-F1 said:**
> I suggest a clean install.

[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.04-lucid-lynx-to-10.10-maverick-meerkat-desktop-and-server)

Good luck.

Thanks for the link.  The settings in update manager must be set to check for Normal Releases or you will receive the following:

**sudo do-release-upgrade** 

[I]Checking for a new ubuntu release
No new release found[/I]

---

### Post by lavinog on 2010-10-13
> **LunaticHiatus said:**
> yeah, I tried that. Clean install isn't really going to happen. I have like 450 gigs being used and I have no external hard drive.
It updates fine, but its not offering me the "upgrade" tab

How is your drive partitioned?

Another option could have been to resize your partition, and create a new partition to do a clean install on.
Depending on what is taking up the space, you can move everything over to the new partition or just leave it on the old.

---

