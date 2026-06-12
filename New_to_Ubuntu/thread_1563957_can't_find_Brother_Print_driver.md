---
title: "can't find Brother Print driver"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by mikeprosceo on 2010-08-29
I am running ubuntu 10.0.4  (64bit) and am trying to install a brother hl-5370dw laser printer.  There are no drivers listed in the add printer box. On the Brother website they list a driver for 64 bit ubuntu but require either la32-libs or lib32stdc++.  How do I find either of these and install them.  I tried sudo apt-get install la32-libs and then lib32stdc++ but both couldn't be found.  I did an update and tried again but still the same.  I am trying to connect wireless but can use a network cable if necessary.  Please help -Mike

---

### Post by Toz on 2010-08-29
You could always try the openprinting drivers - [http://www.openprinting.org/printers](http://www.openprinting.org/printers). They don't have your printer available yet but you could try the 5270 driver. Download the PPD file and select it during the printer install.

/ToZ

---

### Post by Perfect Storm on 2010-08-29
> **mikeprosceo said:**
> I am running ubuntu 10.0.4  (64bit) and am trying to install a brother hl-5370dw laser printer.  There are no drivers listed in the add printer box. On the Brother website they list a driver for 64 bit ubuntu but require either la32-libs or lib32stdc++.  How do I find either of these and install them.  I tried sudo apt-get install la32-libs and then lib32stdc++ but both couldn't be found.  I did an update and tried again but still the same.  I am trying to connect wireless but can use a network cable if necessary.  Please help -Mike

It's 
```
sudo apt-get install ia32-libs lib32stdc++6
```

---

### Post by wojox on 2010-08-29
Do you have a link to that driver? If you running 64 bit and the driver is 64 bit, there is no need to download 32 bit libs.

That's only if you have a 32 bit driver on a 64 bit machine. 

[Like these drivers]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5370DW")

---

### Post by mikeprosceo on 2010-08-29
On the Brother Website they list what they say are 64 bit drivers but also state you must down load the 32 bit libs first.  I downloaded the driver to my desktop but when I try to install the 32 bit libs the terminal message is that they can't be found.  I installed the 32 bit libs on my laptop but can't install the driver from brother.  The message I get is that the cupswrapper package is the wrong architecture (i386) Thats what all the drivers seem to be and for some reason it installed on my desktop.  As you can see I have 2 problems here, laptop and desktop.  Any ideas?

---

### Post by mikeprosceo on 2010-08-29
I guess the question is why does my desktop install the driver (i386) but can't find the 32bit libs and my laptop can find the 32bit libs but won't install the i386) driver?  Both computers are running the same ubuntu and both are AMD 64 bit chips.

---

### Post by Perfect Storm on 2010-08-29
1) Did you install 64-bit version of Ubuntu?
2) DO you have internet connection for it?

It sounds more likely you have installed 32-bit version of Ubuntu on it.

---

### Post by mikeprosceo on 2010-08-30
I thought I downloaded the 64 bit version of ubuntu 10.04 on both machines.  How can I find out?

---

### Post by Soulcage on 2010-08-30
uname -m
If it says x86_64 then you're running 64bit if it just says x86 (I think) then you're running 32bit

---

### Post by mikeprosceo on 2010-08-30
The laptop is running 64 bit but the desktop says i686.  Is that 32 bit?

---

### Post by Riffer on 2010-08-30
Have you enabled "Multiverse" in the repos?  Go to the drop down menu "System > Administration > Software Sources" click on that and enter your root password.  On the first tab (Ubuntu Software) check the boxes for everything except for "source code".  Once you've done that try installing those libraries again.

---

### Post by Perfect Storm on 2010-08-30
> **mikeprosceo said:**
> The laptop is running 64 bit but the desktop says i686.  Is that 32 bit?

Yes. So if you want a 64-bit OS you need to install 64-bit version of Ubuntu.

---

