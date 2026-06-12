---
title: "Need to add nomodeset to Grub menu"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by cwmoser on 2011-05-17
I need nomodeset to boot my Ubuntu 11.04.
On each boot up, I have to manually edit the grub menu boot line and append nomodeset and then I am able to start up Ubuntu.

How can I add the switch nomodeset permanently?

Thanks

Carl

---

### Post by wojox on 2011-05-17
```
gksudo gedit /etc/default/grub
```

Look for this line and add it.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Then

```
sudo update-grub
```

---

### Post by drs305 on 2011-05-17
Once you are booted into your system, open /etc/default/grub and look for the line (the kernel options may be different):
```
gksu gedit /etc/default/grub
```
Change:
> **GRUB_CMDLINE_LINUX_DEFAULT=**"quiet splash vt.handoff=7"

Usually you would replace the "quiet splash" and also the "vt.handoff=7" as well if you are having issues with modules/drivers so it would look like:
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Update Grub:
```
sudo update-grub
```

Added: Hopefully this won't be a permanent solution for you. If you can find the correct video driver or less all-encompassing kernel option you may be able to get rid of the 'nomodeset' option.

---

### Post by cwmoser on 2011-05-18
What is the downside with nomodeset?

Should I look for another way to fix the problem I;m having booting Ubuntu 11.04 other than nomodeset?

Carl

---

### Post by wep940 on 2011-05-18
I found this amongst some things on the net.  Basically, I think the kernel is responsible for detecting/setting video output (Kernel Mode Setting - KMS).  I'm not sure if this has something to do with the changes to X or not (where the default xorg.conf disapeared).   Apparently, nomodeset disables this.  I have no clue what this all means right now - I'm still learning!
 
**Working around bugs in the new kernel video architecture**

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets. While this is a major step forward for the graphics architecture in Ubuntu, in some rare cases KMS will prevent your video output from working correctly, or from working at all. If you need to disable KMS, you can do so by booting with the nomodeset option. You can also save this setting so that it's applied at every boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub). ([533784]("https://bugs.launchpad.net/bugs/533784"), [541501]("https://bugs.launchpad.net/bugs/541501"))

---

### Post by Quackers on 2011-05-18
Often installing an available proprietary graphics driver will cancel it out. Have you run Additional Drivers and installed the correct driver (if there is one)?

---

