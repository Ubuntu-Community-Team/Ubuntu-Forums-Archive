---
title: "PC Line ethernet card"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by km2008 on 2008-01-17
I've just bought the PC Line "Gigabit network card bus", which comes with a Linux driver, but I can't get the driver to work.  The CD has a Linux directory, with file "Makefile", "readme" and a directory called source.  The readme says to 

Unpack the tarball :
	unzip rtl8169_8110S_linuxdrv_vxx.zip

but this file rtl... doesn't seem to be on the CD.

Any thoughts?  Can I get a driver online or do it without a driver?

---

### Post by ugm6hr on 2008-01-17
Plug the card in and turn your computer on.

Once booted - it may just work automatically.

If not, post the output from:
```
lspci
lshw -C network
ifconfig
```

---

