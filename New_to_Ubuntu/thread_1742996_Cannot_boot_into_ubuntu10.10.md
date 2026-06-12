---
title: "Cannot boot into ubuntu10.10"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by darkphantom on 2011-04-29
I Recently tried dual booting windows 7 on my Ubuntu 10.10 machine. However about 3/4's of the way through the installation it failed and said it would revert my computer back to how it was before the install. So I restarted the computer and it did its thing by now I cannot boot into my ubuntu partion i get an error loading operating system message. Does anyone know what i can do?
I have the live CD if that can help.

---

### Post by Calash on 2011-04-29
So I am sure we understand was the system previously an Ubuntu only setup and you were trying to install Windows 7 next to it?

---

### Post by darkphantom on 2011-04-29
Yes I created the second partition from within Ubuntu and formated it to ntfs.

---

### Post by Calash on 2011-04-29
Ok, what happened is that Windows deleted Grub and installed it's own MBR.  Unfortunately the Windows MBR does not recognize other operating systems.

For future reference it is a bit easier to start with Windows and then add Ubuntu as Grub will recognize both operating systems.

The fix is not that bad but you will need a LiveCD.  The instructions here should get you going again.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by darkphantom on 2011-04-29
Thanks for that is fixed now.

---

