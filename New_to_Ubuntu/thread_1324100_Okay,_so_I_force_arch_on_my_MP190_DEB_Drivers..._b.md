---
title: "Okay, so I force arch on my MP190 DEB Drivers... but..."
date: 2009-11-12
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-12
In hardy, xsane can't detect my scanner portion.

Here are the drivers: [http://software.canon-europe.com/software/0031326.asp?model=](http://software.canon-europe.com/software/0031326.asp?model=)

Is there anything I'm missing here?

---

### Post by coldReactive on 2009-11-12
It can detect the printer, but it can't print, cups exits with this:

There was an error during the CUPS operation: 'client-error-document-format-not-supported'

---

### Post by coldReactive on 2009-11-12
Nevermind then, I'll just upgrade to karmic :|

---

### Post by uhappo on 2009-11-12
I've tried it on karmic, won't work or at least I don't know how to do it. I've read some info on OpenPrinting-site, but I'm still quite stupid with this thing.

Please, let us know if this thing prints/scans properly!

(Well printing works ok for me too)

---

### Post by coldReactive on 2009-11-12
> **uhappo said:**
> I've tried it on karmic, won't work or at least I don't know how to do it. I've read some info on OpenPrinting-site, but I'm still quite stupid with this thing.

Please, let us know if this thing prints/scans properly!

(Well printing works ok for me too)

First, turn off the MP190.

Printing requires (in karmic) this package: [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb)

then, after you install it, remember to do this (if you have amd64 like me)
```
sudo dpkg -i --force-architecture <deb_package>
```
on all four debs from canon-europe. Everything in this installation has to be done from terminal, and you MUST turn off the printer before you install anything so it can detect the printer when you turn it on.

I wish ubuntu would make their own packages since canon-europe provides the packages.

---

### Post by uhappo on 2009-11-13
That link of yours about libcupsys2_1.3.9-17ubuntu3.1_all.deb doesn't work.

I haven't tried your method/solution yet, but if you say it works, then kudos and respect, man! Thanks!

---

### Post by coldReactive on 2009-11-13
> **uhappo said:**
> That link of yours about libcupsys2_1.3.9-17ubuntu3.1_all.deb doesn't work.

I haven't tried your method/solution yet, but if you say it works, then kudos and respect, man! Thanks!

printing on karmic will not work without that deb I gave you. I'm glad I saved it. See attachment.

---

