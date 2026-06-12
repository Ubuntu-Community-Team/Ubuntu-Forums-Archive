---
title: "Ubuntu Software Center? Am a bit confused....."
date: 2009-12-06
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-06
Hi I am trying to follow a tutorial and am 90% finished in dual booting windows 7 and Ubuntu 9.04 with shared document data storage.

One of the final things I am supposed to do is "Head to the Applications menu and pick the Ubuntu Software Center. In there, search for "ntfs-config," and double-click on the NTFS Configuration Tool that's the first result. Install it, then close the Software Center."

*> I have looked everywhere and cant find this Ubuntu Software Center - is it because I downloaded ubtunu 9.04? and should have downloaded 9.10?*

Thanks ;)

These forums are the best!

---

### Post by cenzorrll on 2009-12-06
short answer, yes the software center is in 9.10 not 9.04.

i've never used any of the "software centers" found on other *nix's.  it's just a different way of laying out your packages.  if you know what program you want then it's easiest to use the command line or synaptics.  if you don't now what you want, but know the genre its in, then yeah use the software center

type in a terminal:

```
sudo apt-get install ntfs-config
```

or in the menu: system>administration>synaptic package manager

then after your password, search for "ntfs-config", select the package to install, then apply.

---

### Post by Elfy on 2009-12-06
9.04 has Add/Remove ans synaptic as GUI options or do as above and do it though a terminal

---

