---
title: "update manager doesn't update"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by medic8ted on 2009-09-11
It says theres 101 updates, but won't install them, only checks and says theres a bunch out there.  When I click check, it checks and gets the list and descriptions, but when i click install it just says "reading state information" then nothing, back to normal screen.  It never even asks for password.  This has been going on a for a long time, I just now got around to posting.

Ubuntu 8.01
kernel 2.6.27-14

EDIT: No broken packages in Synaptic

---

### Post by wojox on 2009-09-11
Open a terminal and try:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by LewRockwell on 2009-09-11
how does the 9.04 LiveCD run on that machine?

.

---

### Post by medic8ted on 2009-09-11
> sudo apt-get update && sudo apt-get upgrade is working so far, we'll see shortly if it completes...but any ideas why gui won't work?

> **LewRockwell said:**
> how does the 9.04 LiveCD run on that machine?

.

No I have it somewhere but haven't tackled it yet.  I'm not the most proficient person and Murphy wrote his law of things going wrong about my upgrade experiences so I was going to wait for the next LTR before tackling it again.  Maybe going to try another distro, but I'm only familiar with Debian and Gnome so another distro will be time consuming to learn, plus my laptop dual boots XP and Intrepid.  Also with multiple distros, me and Mr. Grub don't get along well, I have reinstalled several times just to fix grub, as I cannot get just grub to install without a complete reinstall.

---

### Post by philinux on 2009-09-11
> **medic8ted said:**
> is working so far, we'll see shortly if it completes...but any ideas why gui won't work?



Keep an eye on it and report any error messages.

---

### Post by LewRockwell on 2009-09-11
> **medic8ted said:**
> ...
Also with multiple distros, me and Mr. Grub don't get along well, I have reinstalled several times just to fix grub, as I cannot get just grub to install without a complete reinstall.

grub must be installed/re-installed via a LiveCD or LiveUSB session since the main/internal hard drive needs to be unmounted(which would be impossible while booted up from that drive)

grub is installed/re-installed quite easily

complete operating system re-installs are not necessary

read all of the following link for a better understanding of this process:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

.

---

### Post by medic8ted on 2009-09-11
> **philinux said:**
> Keep an eye on it and report any error messages.

No error messages from CLI.  Going to leave this thread open until next update since now everything's updated and I can't try it from gui.

---

