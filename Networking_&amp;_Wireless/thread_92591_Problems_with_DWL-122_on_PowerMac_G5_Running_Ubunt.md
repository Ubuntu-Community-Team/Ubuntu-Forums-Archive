---
title: "Problems with DWL-122 on PowerMac G5 Running Ubuntu 5.10"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by yangdh@cableplus.com.cn on 2005-11-19
I installed Ubuntu 5.10 on my G5 successfully and it ran well too. Now the problem is of DWL-122 wireless card. I followed the HOWTO [http://ubuntuforums.org/showthread.php?t=25676](http://ubuntuforums.org/showthread.php?t=25676), and installed linux-wlan-ng package and configured accordingly. But I got the error:
     wlanctl-ng: Function not implementd
when I executed "sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable". I looked dmesg messages and p80211 and prism2_usb modules were listed, the card was also listed in Device Manager.
The system kernel installed is 2.6.12-powerpc64-smp, the hardware is G5 DP 2.0GHz.
Any ideas? Thank you.

---

### Post by elmerhomero on 2005-11-23
Hello yangdh, I just wanted to ask you if you would mind posting in detail how you got your G5 to run Ubuntu. I and apparently a bunch of other people can not get it to run in our G5's  :confused: ; after booting the mouse and keyborard freeze in the login screen. Did you have the same problem? How did you solve it?

---

### Post by mips on 2005-11-24
[http://ubuntuforums.org/showthread.php?t=84802](http://ubuntuforums.org/showthread.php?t=84802)
[http://lists.linux-wlan.com/pipermail/linux-wlan-devel/2004-February.txt.gz](http://lists.linux-wlan.com/pipermail/linux-wlan-devel/2004-February.txt.gz)

---

### Post by yangdh@cableplus.com.cn on 2005-12-02
[QUOTE=elmerhomero]Hello yangdh, I just wanted to ask you if you would mind posting in detail how you got your G5 to run Ubuntu. I and apparently a bunch of other people can not get it to run in our G5's  :confused: ; after booting the mouse and keyborard freeze in the login screen. Did you have the same problem? How did you solve it?[/QUOTE]
Nothing special with the installation, just used the installation disk to boot and followed the instructions of the installer. The big problem for me was yaboot didn't work, so I had to configure it by hand. I selected the ppc64-smp kernel, and didn't come into the freeze of keyboard and mouse, everything seemed running smoothly.
BTW: My G5 is an old model 7,2. Don't know if yours is a new one.

---

