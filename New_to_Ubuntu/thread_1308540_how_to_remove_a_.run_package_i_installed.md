---
title: "how to remove a .run package i installed"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by thomz92 on 2009-10-31
i installed a .run package that was a nvidia driver for my video card. but now i want it off and i want to install it using "restricted drivers". how would i go about uninstalling it? (yes im using 9.10)

---

### Post by sisco311 on 2009-10-31
> **thomz92 said:**
> i installed a .run package that was a nvidia driver for my video card. but now i want it off and i want to install it using "restricted drivers". how would i go about uninstalling it? (yes im using 9.10)

Assuming that you downloaded the nvidia installer to your ~/Desktop:
```
sudo sh ~/Desktop/NVIDIA*.run --uninstall
```

---

### Post by thomz92 on 2009-10-31
whoops bad idea. now the gui wont boot and it goes to text login and blinks. is there anyway to reset xorg config or whatever? or maybe do a "safe mode" boot?

---

### Post by sisco311 on 2009-10-31
> **thomz92 said:**
> whoops bad idea. now the gui wont boot and it goes to text login and blinks. is there anyway to reset xorg config or whatever? or maybe do a "safe mode" boot?

Reboot the computer and select Recovery Mode from the grub menu.

You may have to press the Escape key during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select *xfix Try to fix X server*  option from the Recovery Mode menu, then resume a normal boot.

---

### Post by thomz92 on 2009-10-31
i dont see any xfix option in the 9.10 recovery menu

---

### Post by sisco311 on 2009-10-31
> **thomz92 said:**
> i dont see any xfix option in the 9.10 recovery menu

okay, then select the *root Drop to root shell prompt* option.


the nvidia installer creates a backup of your original xorg.conf

list the file:
```
ls /etc/X11/xorg.conf?*
```

restore the original xorg.conf:
```
cp /etc/X11/xorg.conf<extension of the backup file> /etc/X11/xorg.conf
```

```
exit
```

resume normal boot.

---

### Post by thomz92 on 2009-10-31
its not finding any /etc.X11/xorg.conf.* file!

---

### Post by sisco311 on 2009-10-31
> **thomz92 said:**
> its not finding any /etc.X11/xorg.conf.* file!

sorry, i've edited my last post; it's:
```
ls /etc/X11/xorg.conf?*
```


if there is no backup file, just  remove the old xorg.conf:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old
```

or edit the file:```
nano /etc/X11/xorg.conf
```

and replace the 
```
Driver    "nvidia"
```
line with:
```
Driver    "nv"
```
(Ctrl+x, y, Enter to save the file and exit)

---

### Post by thomz92 on 2009-10-31
it worked! thank u sisco311!!

---

