---
title: "Cant print large pdf in document viewer"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by oilit on 2009-02-10
Intrepid Ibex : I can print single pages in evince document viewer v 2.24.1 but I am trying to print a larger (~50 pages) and the print box comes up, i can press print, but nothing joins the queue and the printer just sits their waiting for a job!:(

Any suggestions?

Thanks

---

### Post by kaibob on 2009-02-10
A lot of people have trouble printing pdf documents with evince. A workaround is to use lpr. Open a terminal window and enter:

```
lpr filename.pdf
```

---

### Post by sdowney717 on 2009-02-10
use adobe acrobat for linux. There is a deb file on the site for download.
Set your printer to be the system default

---

### Post by philinux on 2009-02-10
> **oilit said:**
> Intrepid Ibex : I can print single pages in evince document viewer v 2.24.1 but I am trying to print a larger (~50 pages) and the print box comes up, i can press print, but nothing joins the queue and the printer just sits their waiting for a job!:(

Any suggestions?

Thanks

Click the medibuntu link below and follow the instructions. Acroread will then be available via synaptic. Evince is really only good for simple pdf's.

---

### Post by marcgh on 2009-02-10
I am using the acrobat for linux and I print sometimes manual of 240+ pages with pictures without problem.

---

### Post by oilit on 2009-02-10
thanks - lpr has fixed me short term - but when I tried to download the .deb from adobe it came up with following problem:- /tmp/AdobeReader_enu-8.1.3-1.i386-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences (I was using gdebi)

I am going to try the medibuntu route as soon as my 50 pages have printed off which I needed about 3 hours ago !! THANKS EVERYBODY - Will report back my findings!!

---

### Post by roshanjose on 2009-02-10
hey use kpdf...thats the best you can use...got good features...and no problem with printing

---

### Post by oilit on 2009-02-11
> **philinux said:**
> Click the medibuntu link below and follow the instructions. Acroread will then be available via synaptic. Evince is really only good for simple pdf's.

thanks - got it working !!!

---

