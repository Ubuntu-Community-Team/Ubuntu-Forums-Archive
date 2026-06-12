---
title: "get a package from 10.04 while using 9.10"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-01
Hello,

I'd like to get the package usb-creator - 0.2.19, which is found in Lucid Lynx. I'm using Ubuntu 9.10. How do I get this new version of usb-creator while using 9.10?

---

### Post by wojox on 2010-05-01
There's a .deb here [https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.19](https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.19) may work for ya.

---

### Post by hanzj on 2010-05-02
thanks. 2.19 has been superseded. I got [https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.22](https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.22)

But it gives me this error message:
> Error: Dependency is not satisfiable: usb-creator-common (= 0.2.22).

So I go get usb-creator-common (= 0.2.22), but when I try to install, I get this error message:

> Error: Breaks existing package 'usb-creator-gtk' dependency usb-creator-common (= 0.2.12)
Help.
How do I install usb-creator-gtk 0.2.22 so that everything that it needs is installed too?

---

### Post by GSF1200S on 2010-05-02
> **hanzj said:**
> thanks. 2.19 has been superseded. I got [https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.22](https://launchpad.net/ubuntu/lucid/i386/usb-creator-gtk/0.2.22)

But it gives me this error message:
.

So I go get usb-creator-common (= 0.2.22), but when I try to install, I get this error message:




Help.
How do I install both at the same time?

Do you have USB-creator installed from 9.10's repos? If so, remove all traces of it first and then try to install the .debs.(Make sure you know you have all the dependencies for the program and you arent breaking anything else) you can use:
```
sudo dpkg -i package.deb
```
to install a package without any dependency handling.

You might also need to place a Lock on the package in Synaptic so it doesnt try to upgrade to the version in the repos. Im not sure if it will do this though considering its a newer package (I had installed rhythmbox 0.12.8 from a karmic PPA due to Lucid regressions and it still tried to upgrade to the lucid version despite being the same version of rhythmbox, as an example).

---

### Post by hanzj on 2010-05-02
i removed
 usb-creator usb-creator-common usb-creator-gtk



Then I tried:
" sudo dpkg -i usb-creator-common_0.2.22_all.deb "

Here's the printout.> 
Selecting previously deselected package usb-creator-common.
(Reading database ... 262295 files and directories currently installed.)
Unpacking usb-creator-common (from usb-creator-common_0.2.22_all.deb) ...
dpkg: dependency problems prevent configuration of usb-creator-common:
 usb-creator-common depends on udisks (>= 1.0~); however:
  Package udisks is not installed.
 usb-creator-common depends on udisks (<< 1.1); however:
  Package udisks is not installed.
dpkg: error processing usb-creator-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 usb-creator-common


Pls help.

---

### Post by GSF1200S on 2010-05-02
> **hanzj said:**
> i removed
 usb-creator usb-creator-common usb-creator-gtk



Then I tried:
" sudo dpkg -i usb-creator-common_0.2.22_all.deb "

Here's the printout.

Pls help.

You need the package udisks as suggested in the printout. This is why it can suck trying to install a package on Ubuntu newer than your release. All I can suggest is hunting that package down in deb form, removing the old version from Synaptic, and then trying to install it. Of course, this could keep happening until you end up needing to upgrade kernels, etc.. Give it a shot though.

---

### Post by hanzj on 2010-05-04
i persevered and got about a dozen depencies and now the main package can be installed. Phew.

---

