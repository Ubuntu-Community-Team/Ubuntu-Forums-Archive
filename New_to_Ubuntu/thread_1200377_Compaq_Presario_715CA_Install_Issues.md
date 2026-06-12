---
title: "Compaq Presario 715CA Install Issues"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by nethriel on 2009-06-29
Thanks in advance for any help/suggestions. I have spent the past 2 hours searching these forums for info on how to get Ubuntu installed on this notebook to no avail. Once I select install the computer starts to work, and ubuntu screen comes up with a bar that fills in, about 90% into this bar the the install halts!
 
I have tried to run the Live CD, and the same thing happens. I am sure it is a simple combination of boot parameters that I am missing...

---

### Post by QIII on 2009-06-30
What are the specifications for your machine, such as installed memory, video card, etc?

---

### Post by nethriel on 2009-06-30
AMD 1.2g Mobile Athlon
20g Hard Drive
256m 133Mhz SyncDram (16m for video memory)
4x AGP with VIA Prosavage KN133 Integrated Graphics
 
Complete specs are at: [Notebook Specs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009649&lc=en&dlc=en&cc=us&lang=en&product=95568")
 
I completed a Memtest, no errors were reported (didn't expect any really).I can provide anything else needed.
 
Thanks

---

### Post by QIII on 2009-06-30
Officially, the LiveCD takes a minimum of 256Mb to run.  If some of that is used by your graphics, you may have too little to run it.

Ubuntu will still run on those specs, but don't expect to burn the tires any more than you would with Windows.  You may want to consider Xubuntu, which uses the lighter-weight Xfce desktop.

In either case, you'll probably have to use the "Alternate Install" disk to install Ubuntu.

---

