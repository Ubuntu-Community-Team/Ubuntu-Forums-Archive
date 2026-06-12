---
title: "Guest additions ???"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-27
should this be considered ???

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

input ???

thanks...

---

### Post by nandemonai on 2009-07-27
It certainly helps. There are problems in Jaunty though.

[http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html](http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html)

---

### Post by NOTAGEEK on 2009-07-27
> **nandemonai said:**
> It certainly helps. There are problems in Jaunty though.

[http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html](http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html)

and mint 7 and karmic have less "problems" than jaunty ???

---

### Post by muteXe on 2009-07-27
Works fine in hardy.

---

### Post by RJ12 on 2009-07-27
> **NOTAGEEK said:**
> and mint 7 and karmic have less "problems" than jaunty ???
I agree I tried Karmic under virtualbox ans\d its a pain without guest additions

---

### Post by nmaster on 2009-07-27
> **nandemonai said:**
> It certainly helps. There are problems in Jaunty though.
[]("http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html")

i didn't have any problems with guest additions in jaunty.  try these pages. it worked for me.

[http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox](http://lifehacker.com/5204434/the-beginners-guide-to-creating-virtual-machines-with-virtualbox)
[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by nandemonai on 2009-07-27
> **NOTAGEEK said:**
> and mint 7 and karmic have less "problems" than jaunty ???

Mint 7 is essentially Ubuntu Jaunty, at least as a base. Karmic not too sure, I haven't tried vbox on my testing VM cause it in itself is a virtual machine ;)

As for the issues in Jaunty, version 2.2.4 of the VirtualBox additions needs a simple edit in order to install the video  driver as it doesn't detect the version of X running properly. This may have been fixed in version 3. Not too sure.

---

