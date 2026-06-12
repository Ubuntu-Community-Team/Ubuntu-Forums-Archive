---
title: "Boot Splash OS/Kernel Selector Missing"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by fleamour on 2010-11-25
I need to roll back to a previous kernel but the entry where different kernels/OSs are displayed is missing even with StartUp-Manager configuration.

I messed with different Plymouth splash screens a while back.  How can I restore the original settings as they should be?

---

### Post by fleamour on 2010-12-01
Bump!

---

### Post by NightwishFan on 2010-12-01
Try holding shift while booting to show grub.

---

### Post by fleamour on 2010-12-01
That worked!

Can I permanently get it to display?

---

### Post by NightwishFan on 2010-12-01
Edit the grub timeout in /etc/default/grub as root. Make it like 5 seconds or something.

```
sudo nano /etc/default/grub
```

I am not sure exactly what you have to change though. After you edit the options run:
```
sudo update-grub
```

---

### Post by fleamour on 2010-12-01
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

Seem to have "hidden timeout" enabled.

> The default behavior is to hide the menu if only one operating system is present.

Hopefully this'll work:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

---

### Post by fleamour on 2010-12-01
How do you save changes in nano?  Usually use mousepad.

---

### Post by fleamour on 2010-12-01
Ctrl + X.

---

### Post by NightwishFan on 2010-12-01
Yes, then run:
```
sudo update-grub
```

That should work. Sorry I could not be specific I had to take care of my animals and deal with some snow at the time.

---

### Post by fleamour on 2010-12-01
No worries, thanks for pointing me in right direction!

Cheerz!

---

