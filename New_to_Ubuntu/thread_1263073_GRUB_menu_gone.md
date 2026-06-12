---
title: "GRUB menu gone?"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by William S on 2009-09-10
I just installed Windows 7 on my laptop and GRUB was gone. I managed to restore it using super GRUB, but then I got another problem. The menu is not there and I am just booted to the command line... 
I manage to find the menu.lst using the Super GRUB, but I would like it to be there when I boot normally. 
Any idea how to fix this?

---

### Post by drs305 on 2009-09-10
See if this Ubuntu Wiki helps you out:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by William S on 2009-09-10
> **drs305 said:**
> See if this Ubuntu Wiki helps you out:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindowshttps://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")


That is actually what I tried first.

---

### Post by William S on 2009-09-11
Anyone who can help me with this problem? I really dont like booting up with super GRUB cd all the time...

---

### Post by talsemgeest on 2009-09-11
> **William S said:**
> Anyone who can help me with this problem? I really dont like booting up with super GRUB cd all the time...
Give the instructions on my how-to a try: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2009-09-11
First, what version of Ubuntu and grub are you using? To be sure you can run the following commands while booted into Ubuntu:

```
cat /etc/issue
```

```
grub-install -v
```

---

### Post by LewRockwell on 2009-09-11
> **William S said:**
> Anyone who can help me with this problem? I really dont like booting up with super GRUB cd all the time...

IIRC, SuperGrubDisk will rebuild your grub set-up

or you can use a *nix LiveCD or LiveUSB to re-install the grub

.

---

