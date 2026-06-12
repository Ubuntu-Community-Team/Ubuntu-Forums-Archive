---
title: "Poor wifi performance on ubuntu"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Nastareger on 2008-12-01
I've got a dual boot (vista & hardy) on my dell inspiron 1525 (built-in wifi support, of course), but I encounter some strange problems with that very wifi support... It seems like my network card is performing better when running Windows. Reception is higher, increased speed, sometimes even detects more networks... Why would this be? In Vista, I also have the possibility to 'set the performance' of the card, in the power saving options. Ubuntu does not support this, as the driver is a third-party one and I cannot do any configuration on it. Might it be that the default is set to be a lower performance than it is capable of? I hope one of you can shed some light on this, as I now have to use Vista when the signal is not very strong, which I have started hating. Thanks in advance!

---

### Post by superprash2003 on 2008-12-01
which driver have you used?? the one under sytem->admin->hardware drivers??

---

### Post by Nastareger on 2008-12-01
I can hardly say I remember exactly.. I do remember I had to do something slightly 'out of the ordinary' to make it work. Anyway, under that menu it now lists two drivers (only one in use):
Broadcom B43 wireless driver (this one in use)
Broadcom STA wireless driver (this one not in use)

---

### Post by CSandman on 2008-12-01
It sounds like the Wireless Card that you have is fairly new.  If nothing is in the hardware drivers supported by the Ubuntu Community (as per superprash's post) then it may just be that support for that card is not very complete yet.  It was the same with my Atheros card when I first got it.

I have actually found that on supported hardware (Usually a little bit older) linux in general performs much better.  I've actually resurected really old hardware that was useless on windows by installing ubuntu.

---

### Post by Nastareger on 2008-12-01
So... best thing I can do would be to wait and see whether it's going to receive community support somewhere in the future? 

Stupid question: what is the easiest way of finding out which card I have exactly, and consequently check whether community support already exists? I guess Ubuntu won't automatically notify me when it starts fully supporting my card... or can I do some kind of recheck?

---

### Post by Hyper Tails on 2008-12-01
I have the same problem too with my laptop that runs Intrepid

laptop:acer aspire 5715Z

---

### Post by superprash2003 on 2008-12-02
use STA you should get better performance with that

---

