---
title: "can live cd willl do the foll.?"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-14
<p>
hii...
can i set up my dial up internet connection (edit auto etho) through live cd of ubuntu and ll i able to save it or it will just disappear after removing cd </p>

---

### Post by hamstermoon on 2011-04-14
> **naved ..... said:**
> <p>will just disappear after removing cd </p>

Unfortunately, yes it will. What you could do is set up a persistent USB (using unetbootin and the disk image you used for the CD) using the guidelines in this article:

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by seawolf167 on 2011-04-14
Just as the previous poster said, the LiveCD won't save any changes - the workaround is to make a USB persistent writable boot system (USB because you won't be able to write to a finished cd) with [Unetbootin]("http://unetbootin.sourceforge.net/"). Make sure you turn on USB booting in BIOS, and if you don't want to prioritize it above CD/HDDs, you can usually hit [F12] to display a boot menu during POST

---

### Post by bodhi.zazen on 2011-04-14
Real geeks would simply customize the iso =)

---

### Post by deconstrained on 2011-04-14
> **naved ..... said:**
> <p>
hii...
can i set up my dial up internet connection (edit auto etho) through live cd of ubuntu and ll i able to save it or it will just disappear after removing cd </p>
I'm not even sure what the question is. What exactly is it you're trying to save?

---

