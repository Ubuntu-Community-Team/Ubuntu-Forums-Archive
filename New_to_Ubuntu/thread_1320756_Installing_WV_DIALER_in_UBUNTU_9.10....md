---
title: "Installing WV DIALER in UBUNTU 9.10..."
date: 2009-11-09
forum: New to Ubuntu
---

### Post by vikaskumargdra on 2009-11-09
Hi! 
Can anybody tell me how to install wvdialer in ubuntu 9.10 karmic & where to get it.I tried to search it on [http://www.packages.ubuntu.com/karmic](http://www.packages.ubuntu.com/karmic) then it shows 'server not found'.What the hell is this.Ple anybody help me.
Thanks!:mad:

---

### Post by LowSky on 2009-11-09
no www

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)


direct link
[http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial)

just download and click on to install, easy as Windows

---

### Post by ranch hand on 2009-11-09
I take it that you have a winmodem.

Get an external HARDWARE modem and remove your winmodem.  MS will have a better connection and you can connect Ubuntu by running;
```

sudo pppconfig

```

---

### Post by vikaskumargdra on 2009-11-09
> **LowSky said:**
> no www

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)


direct link
[http://packages.ubuntu.com/karmic/wvdial](http://packages.ubuntu.com/karmic/wvdial)

just download and click on to install, easy as Windows
Oops! Seems somethin went wrong.
While installing shows 'ERROR: Dependency not satisfiable'
what you think about it?

---

### Post by ranch hand on 2009-11-09
Get the depenency and install it.

---

### Post by t0p on 2009-11-09
> **ranch hand said:**
> I take it that you have a winmodem.

Get an external HARDWARE modem and remove your winmodem.  MS will have a better connection and you can connect Ubuntu by running;
```

sudo pppconfig

```

Why do you assume he has a winmodem?  There are many devices that wvdial is handy for.  eg. some cellphones when used as "modems"; some HSDPA modem-dongles that aren't supported by Network Manager.

Anyway, telling someone to "get rid" of his winmodem and replace it with a hardware modem is not particularly useful advice.  Many users rely on their built-in winmodems because they can't afford to go buy bits of hardware at thr drop of a hat.  Hardware modems are becoming increasingly difficult to locate (at a reasonable price) for various reasons including the seeming ubiquity of broadband.

It's true that hardware modems have better compatibility in Linux.  But if a user can get his winmodem to work, it may work just as well as a hardware modem.  Winmodems certainly deserve junking out of hand, even if they are annoying bits of crap.  Anyway, we don't know that the OP has a winmodem.  So there.  

:p

---

### Post by DustStuff on 2010-03-01
This post does not really refer to most (or all?) of what people have been posting here, but it does have some relevance to the subject of this thread.

If you are using a USB modem and were using wvdial (or possibly another dialer) successfully in Ubuntu 9.04, but it no longer works (with the same settings) in Ubuntu 9.10, then you might want to check out [this post]("http://ubuntuforums.org/showthread.php?p=8899463#post8899463") for a workaround solution.

---

