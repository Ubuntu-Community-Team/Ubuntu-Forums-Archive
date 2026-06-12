---
title: "What is a Kernel? and why is it that i still have the 9.04 kernel and not 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by psidrum on 2009-11-02
after i have upgraded?

i checked the kernels in Boot section and i only saw 9.04 kernels?

but yet the OS is looking at my system as Karmic

im confused!

---

### Post by Cypher on 2009-11-02
The Kernel is the heart of ANY OS. Ubuntu is a distribution that packages up the Kernel and a bunch of other applications (X-WIndows & Gnome for desktop for example) so that you can use the system.

Open up a Terminal and type
```

uname -a

```
This will tell you the version of the Kernel you are running.

On my Karmic installation, I have:
> 
Linux Dante 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


I believe Jaunty was at 2.6.29..The Kernel are housed at [http://www.kernel.org](http://www.kernel.org) and are relased by the "father" for Linux Linus Torvalds..

Regards

---

