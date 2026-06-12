---
title: "Device manager?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by guthix0009 on 2010-06-14
ok so ive been on ubuntu on and off and now im actually getting into it and im wondering is there a "device manager" like in windows that will tell me what i have in my computer such as processor and video card.

thanks in advance!

---

### Post by Jay Car on 2010-06-15
Enter ```
sudo lshw -html > hardwareprofile.html
``` in a terminal to create an HTML file with all your hardware details. Then look for the file titled "hardwareprofile.html" in your home folder and double-click it to open it in your browser. It's one of the first things I learned when I started using Ubuntu. :)

---

### Post by bigsmitty64 on 2010-06-15
> **Jay Car said:**
> Enter ```
sudo lshw -html > hardwareprofile.html
``` :)
Brilliant! T

---

### Post by guthix0009 on 2010-06-15
Ok thank you so much thats alot of info  haha well thanks again have a good one

---

### Post by Jay Car on 2010-06-15
You're very welcome! :p

---

### Post by qyot27 on 2010-06-15
If you're up to doing a little Terminal work to get it installed, you can also try [PerlMon](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html).  I've used it before under Karmic, and if what you're looking for is a CPU-Z like program, this is the closest I've found.  Laid out in a very digestible way (and if the CPU-Z reference wasn't clear, PerlMon is a GUI that abstracts the system readouts you'd probably be getting with lshw).

---

### Post by HermanAB on 2010-06-15
lspci
lsusb
lsmod

---

