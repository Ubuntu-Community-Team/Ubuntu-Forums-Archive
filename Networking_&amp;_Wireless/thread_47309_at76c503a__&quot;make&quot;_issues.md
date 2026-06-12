---
title: "at76c503a : &quot;make&quot; issues"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by duminas on 2005-07-08
Alrighty, since I didn't find anything about this specific problem, I must ask.

I am trying to install the at76c503a drivers (for my TrendNet TEW-229UB wlan device), and am encountering a problem at the *make* step. I have downloaded the nightly tarball, as the CVS client method is not something I can employ.

Specifically, this happens:
```
root@my_machine:/home/duminas/CVS/at76c503a # sudo make
co Makefile,v Makefile
make: co: Command not found
make: *** [Makefile] Error 127
```

Prior to this, I've followed all instructions to a T on the [berlios](http://at76c503a.berlios.de) pages. I've installed *build-essential*, *linux-headers-2.6.10-5* and the *linux-headers-2.6.10-5-386* packages, as seems to be common for this driver when I searched around.

Does anyone have any idea what the problem is? I've never really used Linux in earnest before, so I'm a mite lost as to what exactly **co** is, and what package gives it.

Thank you for your time.
[size=1](I hope I put this in the right forum...)[/size]

---

### Post by murkin on 2005-10-18
i'm pretty sure that all that was missing here was installing the package needed for "make"...
try doing a search in synaptic for "make". after installing make, the instructions work with no problems.

---

### Post by az on 2005-10-18
Install build-essential and the linux-headers package for your running kernel.  I run one of those myself (right now, actually...)

Works fine.  Breezy has the driver built-in.  You do not have to compile it.

---

