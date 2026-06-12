---
title: "Need Help ASAP: setting up a network scanner Canon imageRUNNER C3200"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by StutteringJohnSmith on 2011-02-09
I few weeks ago I got sick of windows and I installed ubuntu 10.4 on my netbook without thinking about all the stuff I do. A big park of my job is scanning documents into PDFs and emailing them out.  I need help setting up a network scanner Canon imageRUNNER C3200.

Please help me out in anyway

---

### Post by davidmohammed on 2011-02-09
if you plug it directly into your netbook (assuming it has a usb cable) and run xsane or simple scan, does it recognise your scanner?

---

### Post by StutteringJohnSmith on 2011-02-09
no its pluged into the network with a network cable the Canon imageRUNNER C3200 is a very big unit!

---

### Post by davidmohammed on 2011-02-09
sane supports [these]("http://www.sane-project.org/sane-mfgs.html#Z-CANON") canon scanners - yours isnt on the list.

Looks like the best way to achieve this is to keep windows - either in a dual boot configuration - or installing a slimline windows install into virtualbox.

---

### Post by StutteringJohnSmith on 2011-02-09
it does not look like any network onces work :(, can you please tell me more about running windows install a win

---

### Post by davidmohammed on 2011-02-09
there are various how-to's on the web.

[This one]("http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02") is slightly old - but the process is similar.

You can download the latest virtualbox deb from [here]("http://www.virtualbox.org/wiki/Linux_Downloads")

...

I just noticed you are using a netbook - unless you are using one of the newer multicore netbooks I wouldnt recommend using virtualbox due to the relative lack of performance on most netbooks - I would stick to dual booting between ubuntu and windows.

---

