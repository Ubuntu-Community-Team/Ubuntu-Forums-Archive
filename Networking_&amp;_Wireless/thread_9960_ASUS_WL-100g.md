---
title: "ASUS WL-100g"
date: 2005-01-03
forum: Networking &amp; Wireless
---

### Post by rick2910 on 2005-01-03
Hello,

I have installed and used Ubuntu, and I have to say I was quite stunned by it's appearance and good functionality. But one thing (and that was the only one) that did not work was my wireless card.

It is the ASUS WL-100g PCMCIA card. It will not start up (the link light does not turn on). 

So my question is if it is possible to add this broadcom chipset into a next version of Ubuntu, so I do not have to fool around with all kinds of work-arounds.... I have to say that it is one PCMCIA card which (at the moment) is very widespread in use. So support for this card would not only benefit me (I know several other people with the same problem).

Furthermore, keep up the good work!

Yours faithfully,

Rick; The Netherlands.

---

### Post by guzzi333 on 2005-04-11
I think the linux kernel does not support your card yet.

Take a look at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
This a module for the linux kernel that can load your driver for windows.
I guess that you also just can apt-get ndiswrapper

---

