---
title: "Can I use an Epson Stylus DX7450 All-in-One device with Ubuntu 9.10?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by AndrewS on 2009-11-10
Hi

I have Ubuntu 9.10 installed on my PC, and I want to use the scanner facility of my Epson Stylus DX7450.  I've tried xsane, but it just says it can't find a scanner.  Am I missing something, or isn't this device supported?

TIA

Andrew

---

### Post by philinux on 2009-11-10
[http://translate.google.co.uk/translate?hl=en&sl=pl&u=http://forum.ubuntu.pl/showthread.php%3Ft%3D55950&ei=2IL5SvbOFonG4Qbn9-W2Cw&sa=X&oi=translate&ct=result&resnum=1&ved=0CAwQ7gEwAA&prev=/search%3Fq%3Dlinux%2Bxsane%2BEpson%2BStylus%2BDX7450%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DbXD%26sa%3DG](http://translate.google.co.uk/translate?hl=en&sl=pl&u=http://forum.ubuntu.pl/showthread.php%3Ft%3D55950&ei=2IL5SvbOFonG4Qbn9-W2Cw&sa=X&oi=translate&ct=result&resnum=1&ved=0CAwQ7gEwAA&prev=/search%3Fq%3Dlinux%2Bxsane%2BEpson%2BStylus%2BDX7450%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DbXD%26sa%3DG)

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7450](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7450)

Use 

```
lsusb
``` to get the device code.

Or go to the source for a driver.

[http://translate.googleusercontent.com/translate_c?hl=en&sl=pl&u=http://esupport.epson-europe.com/ProductHome.aspx%3Flng%3Dpl-PL%26data%3DlkuCfcvA9cxilOO9%2Bu8vw8Lv3Uf92LwP4YHYMiH4UYEU003D%26tc%3D6&prev=/search%3Fq%3Dlinux%2Bxsane%2BEpson%2BStylus%2BDX7450%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DbXD%26sa%3DG&rurl=translate.google.co.uk&usg=ALkJrhiZTHw1JDaD8a5fp7UyaWJRc57AqQ](http://translate.googleusercontent.com/translate_c?hl=en&sl=pl&u=http://esupport.epson-europe.com/ProductHome.aspx%3Flng%3Dpl-PL%26data%3DlkuCfcvA9cxilOO9%2Bu8vw8Lv3Uf92LwP4YHYMiH4UYEU003D%26tc%3D6&prev=/search%3Fq%3Dlinux%2Bxsane%2BEpson%2BStylus%2BDX7450%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-GB:official%26hs%3DbXD%26sa%3DG&rurl=translate.google.co.uk&usg=ALkJrhiZTHw1JDaD8a5fp7UyaWJRc57AqQ)

---

