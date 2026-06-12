---
title: "I can't log in as root"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Tasoan on 2010-06-16
I need to mount a usb flash drive and I cannot becaues it says that "only root can do that"

I followed this thread
[http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/](http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/)
and got down to 

Type: sudo gedit /etc/X11/gdm/gdm.conf

and when it pops up nothing is there. 

What do I do.

---

### Post by wojox on 2010-06-16
That file doesn't exist being the how to is two years old and a lot has changed. Here's a guide in root [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Here's help on mounting [URL="https://help.ubuntu.com/community/Mount/USB"]Mount USB
[/URL]

---

### Post by bodhi.zazen on 2010-06-16
First , Ubuntu uses sudo, not su

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Second, use gksu for graphical apps

```
gksu gedit
```

Third that how to is just poor advice. Running a desktop / logging in as root is uncalled for and is not supported here.

What problem are you having with what USB device ?

One thing that comes to mind, if you have multiple users, and you switch users, the usb device is owned/mounted by the first user, hard to know what your problem may be though.

Running as root is not the best of solutions.

---

### Post by cariboo on 2010-06-16
There is no /etc/X11/gdm/gdm.conf. That has been changed, as you really don't want to run the desktop as root. I know from personal experience that mistakes can be made

What version are you using? I haven't been ask to mount a usb drive as root for the last several version. I would suggest you are trying to mount the device to a directory you don't have permission to. If you want to mount the drive to a directory you don't have write permissions to, open a terminal and type:

```
sudo mount /dev/sdc1 /mnt
```

Change the device label to your devices and the mount directory to where you want

---

### Post by Tasoan on 2010-06-16
Oh...the fact that it's 2 years old makes sense. ^^ I am using Ubuntu 8.04
I try to mount my usb and it says that you are not privileged to mount "usb disk"

---

