---
title: "scanner work with sudo xsane but not xsane"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by matchstich on 2009-08-16
i installed a brothers 210c using these instructions

[http://ubuntuforums.org/showthread.php?t=590793&page=14](http://ubuntuforums.org/showthread.php?t=590793&page=14)

the printer works but the scanner only works when i use sudo xsane

but when i go to applications-graphics-xsane  all i get is a error 

failed to open device 'brother2:bus4;dev1':

error during device i/o

can any one help me to understand how to get the scanner working with out having to log in as root?

in simple non-confusing language.

when i go to   sudo gedit /etc/udev/rules.d/45-libsane.rules

all i get is a blank page.

thanks

---

### Post by plucky on 2009-08-16
> when i go to sudo gedit /etc/udev/rules.d/45-libsane.rules


Assuming you are on 8.04,try```
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules
```

and  "Edit "0664" to "0666" in "USB devices" section."

So it look like ```
Before the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

```

Save and reboot.

Good Luck

---

### Post by CatKiller on 2009-08-16
Don't forget to add yourself to the scanner group.

```
sudo adduser *username* scanner
``` (replacing *username* with your user name, obviously)

You'll need to log out and log back in for this change to take effect.

---

### Post by matchstich on 2009-08-17
ok, thanks yall

sudo adduser username scanner

i got no scanner group found


for the permissions thing

i got another blank file

thanks

---

### Post by CatKiller on 2009-08-17
> **matchstich said:**
>  i got no scanner group found

That would probably do it. I believe the *scanner* group is supposed to be automatically set up when you install one of the sane packages. The principle is that the scanner device is set to be owned by the *scanner* group, and then whichever user is in the *scanner* group gets access to the scanner. Since *root* has access to everything, it still works with *sudo* even though it doesn't work for normal users. Possibly creating this group yourself with ```
sudo addgroup scanner
``` and then adding yourself to that group will work. You'll need to log out and log back in for changes to groups to take effect.

Actually, from a quick read of the [documentation]("http://www.sane-project.org/docs.html"), it might be that when I set up my scanner that things were different (it was some time ago). I might not be able to help you, since my knowledge may be out of date.

---

### Post by matchstich on 2009-08-18
thanks yall, it works and every thing is ok.  how do i mark this as solved?

---

