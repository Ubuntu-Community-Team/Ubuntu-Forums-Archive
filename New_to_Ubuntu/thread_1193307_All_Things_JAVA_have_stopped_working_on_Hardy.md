---
title: "All Things JAVA have stopped working on Hardy"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by crjackson on 2009-06-21
Okay, I don't know what happened, but JAVA no longer works on anything on my system. I have checked synaptic and reinstalled sun java and ubuntu-restricted-extras to no avail.

Surely someone can tell me how to repair this.

---

### Post by konqueror7 on 2009-06-21
have you tried,
```
sudo update-alternatives --config java
```
?

---

### Post by LewRockwell on 2009-06-21
when exactly might this have occurred?

cold boot?
warm boot?
updating?
setting adjustments?

---

### Post by crjackson on 2009-06-21
> **konqueror7 said:**
> have you tried,
```
sudo update-alternatives --config java
```
?

I didn't think of that. Thanks, it did get my java apps working, but according to java.com, the plugin may not be correct. See the screen shot below

---

### Post by konqueror7 on 2009-06-21
are there any other java versions you've installed? like GCJ or OpenJDK? try to remove them first, then reinstall the plugin, and see if that works.

---

### Post by crjackson on 2009-06-22
> **konqueror7 said:**
> are there any other java versions you've installed? like GCJ or OpenJDK? try to remove them first, then reinstall the plugin, and see if that works.

Okay thanks, I'll give that a shot too...

---

### Post by jordan420 on 2009-06-22
i know thius doesnt have anything to do with the thread.. but i was curious. is that a ferret in your avatar? because that might be the meanest looking ferret i have ever seen.

---

### Post by crjackson on 2009-06-22
> **jordan420 said:**
> i know thius doesnt have anything to do with the thread.. but i was curious. is that a ferret in your avatar? because that might be the meanest looking ferret i have ever seen.

Her name is Roxie ...  Looks can be deceiving.  She was yawning...

---

### Post by kpkeerthi on 2009-06-22
If you are running 64bit ubuntu, you need to install [icedtea6-plugin]("http://packages.ubuntu.com/jaunty/icedtea6-plugin")

---

### Post by crjackson on 2009-06-23
> **kpkeerthi said:**
> If you are running 64bit ubuntu, you need to install [icedtea6-plugin]("http://packages.ubuntu.com/jaunty/icedtea6-plugin")

It's sorted for now. I'm running 32-bit

The Sun website says my java is out of date, but my apps work so I'm not concerned anymore.

---

