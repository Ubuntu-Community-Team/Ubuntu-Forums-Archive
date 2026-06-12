---
title: "Lexmark X1170 - printer ok, scanner no"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by akira27 on 2010-08-06
Hello,

I am trying to get my Lexmark X1170 printer/scanner to work on Ubuntu 10.04 Lucid.  Thanks to a helpful how-to guide, I successfully got it to print by installing a driver for Z600, but I still cannot scan.

The problem is the same on both SimpleScan and XSane: the scanner makes a repeated mechanical sound as if it's jammed.  When I look inside, the scanning bar (with light source and optical sensor) is stuck at the beginning position, though it keeps trying to go forward.

It's not a hardware issue, as the scanner works perfectly fine on my laptop running Windows 7.

I believe I need something more than the Z600 driver, because the Lexmark Z600 is only a printer without scanning function.

Could anyone suggest something to get my scanner working?

I just would like to thank and show my appreciation for all those who are active on the Ubuntu forums, for providing community support.  I made the transition from Windows to Ubuntu only a couple months ago, and overall, I'm very satisfied.

---

### Post by LowSky on 2010-08-06
I know this isn't what you want to hear, but your lucky you got that printer to even print. Lexmark doesn't make linux drivers, and doesn't plan to for the most part.

---

### Post by akira27 on 2010-08-06
*sigh*

Thanks for comment, LowSky.  Yes, I've gathered that Lexmark printers are often "paper-weight" when it comes to running on Linux.

However, I read that some Lexmark All-in-One printers can just be plugged in, working without having to install drivers, including the scanner.

I'm hoping that some linux scanner driver/software would work on the X1170 also. I suppose it's too much to expect that the scanner on X1170 uses some "standard" scan interface?

This issue is one of the few things that forces me to keep Windows 7 running on my laptop.  One day, I shall make a complete transition to Ubuntu!

---

### Post by zipizap on 2011-02-09
> **akira27 said:**
> *sigh*

Thanks for comment, LowSky.  Yes, I've gathered that Lexmark printers are often "paper-weight" when it comes to running on Linux.

However, I read that some Lexmark All-in-One printers can just be plugged in, working without having to install drivers, including the scanner.

I'm hoping that some linux scanner driver/software would work on the X1170 also. I suppose it's too much to expect that the scanner on X1170 uses some "standard" scan interface?

This issue is one of the few things that forces me to keep Windows 7 running on my laptop.  One day, I shall make a complete transition to Ubuntu!

Well my friend akira27, maybe now you will have even less reasons for using windows :)

I'm with ubuntu 10.04, and I made my scanner/printer Lexmark X1170 scan documents successfully with ubuntu (colors, grayscale, black and white, in several dpi resolutions :) )

I did not had to install any scanner-driver, I just had to install the scanner program Xsane, and it worked out-of-the-box:
```

sudo apt-get install xsane
#and now launch the program xsane to scan
xsane

```And that was it.

I've found very usefull information about scanners in ubuntu in the following page:
[https://help.ubuntu.com/8.04/printing/C/scanning.html](https://help.ubuntu.com/8.04/printing/C/scanning.html)
(which lead me to [this other]("https://wiki.ubuntu.com/HardwareSupportComponentsScannersLexmark") proving that scanning with Lexmark X1170 and other models is supported in ubuntu)

Hope that helps :)

---

### Post by DrStrom on 2011-04-25
I am using Ubuntu Natty 11.04 and i dont get the Lexmark x1170 working. I find it with sane-find-scanner but not with scanimage -L anyone an idea ?

---

