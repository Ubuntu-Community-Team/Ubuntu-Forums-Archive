---
title: "Ubuntu 8.04 Hardy, major update turns AMD 64 to rubbish"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-12-05
Hey crew

Last week when we had the major updates I encountered some dramas after completion.  Namely, my number pad doesnt work (I have a laptop, and I use a usb keyboard, and both boards dont work...) and I have lost access to my Virtualbox installation of WinXP.

Can I uninstall the updates (I have no idea which update messed things for me) but I have a rough idea of the date, and I have had one update since.

Has anyone else had any dramas with the updates to Hardy?

Cheers

---

### Post by nakama85 on 2008-12-05
> **SonOfOdin said:**
> Hey crew

Last week when we had the major updates I encountered some dramas after completion.  Namely, my number pad doesnt work (I have a laptop, and I use a usb keyboard, and both boards dont work...) and I have lost access to my Virtualbox installation of WinXP.

Can I uninstall the updates (I have no idea which update messed things for me) but I have a rough idea of the date, and I have had one update since.

Has anyone else had any dramas with the updates to Hardy?

Cheers

You could try rebooting and loading the previous kernel. See if this works. If it does than you computer does not like the new kernel. The downside to this is that the previous kernel has alot of vulnerabilities.

---

### Post by mybunche on 2008-12-05
I have never had any trouble with any Ubuntu updates. I am running on intel 32bit. Hope you get it resolved.

---

### Post by hyper_ch on 2008-12-05
as for vbox, when you start it it will tell you that you don't have compiled the according modules for the kernel and it will tell you the code to do so.

---

### Post by SonOfOdin on 2008-12-05
> **hyper_ch said:**
> as for vbox, when you start it it will tell you that you don't have compiled the according modules for the kernel and it will tell you the code to do so.

"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"

From the console I have done:
$ sudo apt-get install virtualbox-ose-modules-generic

Then I tried uninstalling this package and reinstalling it.. but still getting the above.

---

### Post by SonOfOdin on 2008-12-05
Hey Nakama, how do I reboot the old kernel?

---

### Post by theozzlives on 2008-12-05
[http://www.virtualbox.org]("http://www.virtualbox.org")Download that and install that.

---

### Post by hyper_ch on 2008-12-06
oh, the OSE version... no clue... the other one tells you to command for recompiling.

---

