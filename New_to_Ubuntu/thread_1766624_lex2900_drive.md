---
title: "lex2900 drive"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by baba88 on 2011-05-24
Hi,

I try to install lex2900 drive by using the file  I downloaded from [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters). However, I do not know how to canonLBP_install.sh. 
Thanks for your help.

---

### Post by yeats on 2011-05-24
This may help you:

[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)

---

### Post by baba88 on 2011-05-31
I have read the document, but I do not know where to write sudo ./canonLBP_install.sh PRINTER_MODEL.

---

### Post by baba88 on 2011-06-02
anyone can help me?

---

### Post by yeats on 2011-06-03
Okay, take these steps:

1) Open a terminal window (Applications -> Accessories -> Terminal).

2) type in the following code (hit enter after every line):

```
wget http://codebin.cotescu.com/canon/lbp_driver/CanonCAPTdriver.tar.gz
tar xzf CanonCAPTdriver.tar.gz
cd raducotescu-CanonCAPTdriver-c8ea9f9/
sudo ./canonLBP_install.sh LBP2900
```

Post back if you hit any more issues.

---

