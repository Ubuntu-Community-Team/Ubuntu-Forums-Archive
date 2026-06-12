---
title: "About installing ndiswrapper"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Tahir on 2007-02-17
Hello all,

I have installed Ubuntu 6.10 (Edgy Eft) the desktop CD on my computer and I was confused when I had to install ndiswrapper.  I selected all the ndiswrappers there were:

ndiswrapper-common
ndiswrapper-utils
ndiswrapper-utils-1.1
ndiswrapper-utils-1.8

Would this have anything to do with me getting no results when I types "iwlist scan"?

So which ndiswrappers do I install then?

-T

---

### Post by teaker1s on 2007-02-17
in terminal  and post results first lets find your chipset
[COLOR="Red"]lsusb
lspci[/COLOR]

---

### Post by Tahir on 2007-02-18
> **teaker1s said:**
> in terminal  and post results first lets find your chipset
[COLOR="Red"]lsusb
lspci[/COLOR]

Thanks but I have got it to work!!!

It doesnt matter if you install all the ndiswrapper packages!!!

Thanks again
-Taz

---

### Post by teaker1s on 2007-02-18
on your hardware maybe, but on mine without utils=no wireless. glad your sorted

---

### Post by Tahir on 2007-02-18
> **teaker1s said:**
> on your hardware maybe, but on mine without utils=no wireless. glad your sorted

Actually I installed all the utils meaning:

ndiswrapper-utils
ndiswrapper-utils-1.1
ndiswrapper-utils-1.8

all of them!

---

