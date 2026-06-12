---
title: "Problems installing new software"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Pyreth on 2010-12-29
Hi There,

I have big problems on my laptop running ubuntu...

Yesterday is installed netatalk but something went worng i guess because when i try to install new things (on synaptic, terminal or what else) i get the following message:

E:I wasn't able to locate file for the netatalk package. This might mean you need to manually fix this package.:

I already tryed to delete the package, to reinstall, but everytime this message comes forward and its drving me crazy. I hope somebody can help me ouit, because i'm complete new to ubuntu...


Greets, Sander

---

### Post by cariboo on 2010-12-29
Open a terminal and try:

```
udo apt-get -f install
```

to see if any missing dependencies get installed.

If that doesn't work, go to System->Administration->Synaptic Package Manager->Edit->Fix broken packages and remove any packages that show up there.

---

