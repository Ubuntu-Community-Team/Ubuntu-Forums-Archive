---
title: "Printer driver problem [Brother DCP]"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by leem018 on 2010-12-10
Hi,

Another Linux newbie here.  I've just migrated from a Windows OS and am still very much finding my feet with Ubuntu 10.4.

The first problem I've encountered is with the installation of my printer drivers.  Well, not the installation, which went fine, but the actual use. 

I installed the Linux drivers from the Brother site [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-163C") for my DCP163C - both the LPR and cupswrapper DEB files.  The drivers are installed and the computer appears to recognise my printer at the /admin/printer application.

When at this page, I try to print a test page.  The command appears to go through but never gets past the 'processing' part.  I also attempted to print from the Text Ed app without success, although my printer was listed as an option.

It seems to me like my computer has a profile for the printer ready to go, but that the two aren't communicating.

Any advice or areas to consider would be very much appreciated.

Many thanks.

Lee

---

### Post by cariboo on 2010-12-10
Did it print a test page when you originally installed the printer? I have a brother printer, HL-5250DN, an it automagically installed the drivers without any intervention from me.

---

### Post by Daveth on 2010-12-10
does it show up as a usb device i wonder. Type

```
lsusb
```

in a terminal and see if it names the printer. Terminal from Applications/Accessories.

---

### Post by charlie_b on 2010-12-10
I had a similar problem with my Brother printer. If you open up Synaptic package manager and search for brother printer, you'll find a bunch of driver packages there. My problem was fixed by using one of these packages, rather than the download from the brother website.

---

