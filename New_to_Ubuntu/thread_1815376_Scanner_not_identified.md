---
title: "Scanner not identified"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by expatCM on 2011-07-31
I would like to scan using xsane but I get an error of No Devices Available.    The scanner (Epson V33) used to work with 10.10 but not now ... 

sane-find-scanner shows 'found USB scanner (vendor=0x04b8, product=0x0142) at libusb:002:010'

lsusb includes 'Bus 002 Device 010: ID 04b8:0142 Seiko Epson Corp.' and I know this is the scanner since if I power off the scanner and repeat the command the line disappears.

scanimage -L says 'No Scanners Were Identified'

I have looked at the file /etc/sane.d/dll.conf and both epson and epson2 do not have a # at the beginning of the line so they should be fine.


What should I look at next?

---

### Post by expatCM on 2011-07-31
I have managed to solve this which is kind of amazing..

It seems that Epson need three extra packages to be installed so that a program called Image Scan! will run and that acts as a front end for the scanner.

The packages are offered by avasys.jp and there are different versions according to your architecture and scanner.

I found that the install was nearly a pain since avasys have not updated their software for Ubuntu 11.04 and Image Scan! depends on an older library which also needs downloading and installing (found in the old repositories).

With that done ...  it simply works.

---

### Post by boban_bt on 2011-08-03
[B]HOW TO Install plustek opticpro st24 on ubuntu 10.04 LTS
HELP
HELP:popcorn:
[/B]

---

### Post by demonipuch on 2011-08-04
> **boban_bt said:**
> [B]HOW TO Install plustek opticpro st24 on ubuntu 10.04 LTS
HELP
HELP:popcorn:
[/B]

Hello

Unfortunately, it seems that your scanner is currently not supported by the Sane library : [http://www.sane-project.org/unsupported/plustek-opticpro-st24.html](http://www.sane-project.org/unsupported/plustek-opticpro-st24.html)

---

