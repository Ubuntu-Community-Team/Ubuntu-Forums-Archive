---
title: "Verbose lsusb output for a single device"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-05-01
Is there a way I can get a verbose out from lsusb command for a single USB item? The issue I am having is when I run just lsusb -v there is too much output and devices I need information about get cut off... Is there a way I can either A. get the output for just a single device, or B. dump the output to a .txt file somehow?

Thanks,
~Jeff

---

### Post by nandemonai on 2009-05-01
```
lsusb --help
```

---

### Post by beastrace91 on 2009-05-01
Yes I'm aware of this... I've spent at least a half hour looking this over and another half hour crawling google. How can I make it display for just a single device?... If you understand it from the help out then please share :)

~Jeff

---

### Post by anewguy on 2009-05-01
This is a 2-step process:

(1) do a normal lsusb.  After the ID: will be a string such as 1234:5678.  This is the unique vendor id (before the : ) and product id (after the : ).

(2) do:

lsusb -v -dxxxx:yyyy where the xxxx:yyyy is the vendor and product id from a normal lsusb.

Dave :)

BTW:  A better resource in this case than lsusb --help is man lsusb. :)

---

