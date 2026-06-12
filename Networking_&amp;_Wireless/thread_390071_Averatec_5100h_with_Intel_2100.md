---
title: "Averatec 5100h with Intel 2100"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by cab7104 on 2007-03-21
I believe that I am having an issue enabling the wireless card in my Averatec 5100h. This is my first install of Ubuntu, I have tried with the auto recognizing drivers, and with ndiswrapper- no luck. Anyone have a work-around? Thanks in advance - 

Craig

---

### Post by gradedcheese on 2007-03-21
Don't use ndiswrapper for Intel drivers, they are supported by a real driver:

[http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

I would just download the driver source from above and follow the installation instructions.  You will need two packages:

```

sudo apt-get install linux-headers-`uname -r` build-essential

```

---

### Post by zip22 on 2007-03-24
i am looking for similar assistance with ipw2100 wireless.   i may be missing something, but the installation instructions that i am looking at for the driver aren't exactly straightforward. is there a walkthrough or an easier way?

---

