---
title: "Epson SX200 printer"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Victor Anderson on 2010-12-06
Hi.
      after loading Ubuntu 10.10 onto a upgraded PC and being highly delighted with it I got the nerve up to install my Epson SX200 printer and was delighted at the speed it installed at and it worked but for the Ink Cartridge Status Page which does not show, I have the software CD so if anyone can advise I would be grateful as I am very new to Linux.

Thank you.
Vic :P

---

### Post by cavh on 2010-12-06
I'm guessing that the software CD you have is a Windows version? If so, you have two options, number 1 being preferable to number 2:

1. Check the Epson website and/or do a Google search to find an updated driver for Linux and which includes the ink cartridge functionality (note - such a driver might not exist)

2. Install the software under WINE - see the Wine forum here [http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

### Post by ellgor on 2010-12-06
Hi,

You can use "mtink" its an Epson utility and its  in the repo's.

Regards, Ellgor.

---

### Post by boirax on 2012-03-05
I installed mtink,

```
$sudo apt-get install mtink
```

and ran it,


```
$sudo mtink
```

It looks like a neat little application.  Unfortunately it didn't detect the printer on /dev/lp0, and gave an error about no paper, no ink, not on.

In the end I took a scale and found the cartridge which weighed 5g less than the other ones! :D

---

