---
title: "update killed modem connection"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2007-02-26
After I updated my soft ware last night and then shut down the computer.  This moring I tried to get on the internet and got a can't open modem with gnome.  I then tried with wvdial and got a CANNOT OPEN /DEV/MODEM. I then checked to see it the modem directory was in the dev directory and it was not there. 

I don't know how to get my modem (dial up ) working again or get the modem directory back so it will work. I don't know what else could have changed it. I know I had to be on line to get the updates. 

Can anyone help.

---

### Post by VitaminG on 2007-02-26
Did you update the kernel? If you did, you will probably have to recompile and reinstall the modem drivers with the new kernel. Before you do this, confirm by booting into the old kernel and trying to dial out. If you didn't update the kernel, I'm not sure what the problem is. I've had this problem, though, when upgrading the kernel.

---

### Post by ronbrooks on 2007-02-27
Here is the answer the update did change my Kernel so the driver would not work.  I went back to Linuxant and down loaded the right driver for that Kernel.  I uninstalled the old driver and installed the new one and now everything is working ok.

---

