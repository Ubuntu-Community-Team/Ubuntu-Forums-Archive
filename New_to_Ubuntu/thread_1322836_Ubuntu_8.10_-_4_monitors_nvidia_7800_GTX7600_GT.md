---
title: "Ubuntu 8.10 - 4 monitors: nvidia 7800 GTX/7600 GT"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by ImprisonedPride on 2009-11-11
Sorry if this is in the wrong forum. This is my first time using Ubuntu and I figured that there would be enough info available on Google to help me sort this out, but I just can't seem to get it working correctly.

As the title says, I'm trying to get a quad-monitor setup working in Ubuntu 8.10. This is running persistently from a Kingston 4GB thumb drive. Here's what I've been able to do:

[LIST]
[*]Install Ubuntu to the USB.
[*]Resize casper-rw to soak up the extra space after the install.
[*]Launch Ubuntu in a single-monitor view.
[*]Change themes, play games, and basically muck things up time and time again...
[/LIST]

I've been at this for just over 9 hours now and I've formatted and reinstalled it on the USB drive about 6 times now because if I make any small mistake, my BIOS passes right by it and loads Windows 7 instead, even when I manually select it.

I've been following [this tutorial]("http://jayant7k.blogspot.com/2009/02/upgrade-nvidia-drivers-on-ubuntu-810.html"), and it works... sort of. envyng -t fails to launch again and again. It displays "TypeError: list indices must be integers" as the error in the terminal. So I went with the second approach that page offers: manually updating the nvidia drivers myself. After the fourth consecutive fail/format/install I actually did manage to get NVIDIA-Linux-x86-180.51-pkg1.run to finish installing. When I went to reboot, the screen just hung at a black screen for 30 seconds to a minute before spewing 20-25 "Bad Sector" errors and rebooting. However, when I went to boot into Ubuntu it was the same case as before: Somethings wrong with the install because now Windows 7 boots instead and the USB drive gets passed over.

So I'll restate myself. I'm completely and totally new at Ubuntu but I just had this 4GB USB lying around and wanted to try it out but it's not worth it if I can't use 4 monitors. I'm sure everyone can post me links, but can someone please just **walk me through the steps?** I'm down to my last fistful of hair here.

Thanks.

---

### Post by ImprisonedPride on 2009-11-11
Bump from page 4.

---

### Post by ImprisonedPride on 2009-11-11
Bump from page 8.

---

### Post by ImprisonedPride on 2009-11-12
Bump from page 5... last bump.

---

### Post by Temposs on 2009-11-12
1) Not many people are trying to set up quad monitor.

2) Ubuntu 8.10 is a little old, and not many people are using it still(though it is still supported, of course). Most people now are on 8.04, 9.04, or 9.10.

These are reasons you're likely not getting a response to your question.

---

### Post by ImprisonedPride on 2009-11-12
Fine, fine. I was only using 8.10 because it was suggested to me. Is it any easier in 9.10?

---

### Post by JBAlaska on 2009-11-12
Do try 9.10, also you should not use envyng, just install the recomended Nvidia driver from System, Administration, Hardware Drivers.

Can't help on the quad monitor thing though, hopefully someone else can. Are you trying to use 4 monitors as one big display? if so check out Xinerama and TwinView

---

### Post by ImprisonedPride on 2009-11-12
Tried 9.10. Shows me the typical Ubuntu option screen and when I press Run it goes to the normal casper....... screen and then to a black screen for eternity.

Not really sure what you mean by "one big display". In Windows 7, all of my monitors act like separate screens. Two run on the 7600GT and two run on the 7800GTX.

---

