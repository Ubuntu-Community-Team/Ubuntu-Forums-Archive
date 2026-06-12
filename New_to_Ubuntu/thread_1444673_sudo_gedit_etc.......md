---
title: "sudo gedit/ etc......"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by duncanmaybury on 2010-04-01
Hi I am trying to get an old laptop to use a edimax usb wireless stick. I am following the instructions here[http://ubuntuforums.org/showthread.php?p=8851236#post8851236 ]("http://ubuntuforums.org/showthread.php?p=8851236#post8851236")
it worked on my other machine, but on this one when I run the command 
sudo gedit /etc/modprobe.d/blacklist.conf 
it says no such command! any ideas?
I am using xubuntu with a gnome desktop session

---

### Post by theozzlives on 2010-04-01
try nano, gedit is a GNOME program.

---

### Post by snowpine on 2010-04-01
For Xubuntu, you can use:

```
gksudo mousepad /etc/modprobe.d/blacklist.conf
```

(Mousepad is the Xubuntu text editor; gksu is better than sudo for graphical applications.)

---

### Post by sisco311 on 2010-04-01
gedit is a GUI text editor, it's not installed, by default, in Xubuntu.

Xubuntu's default GUI text editor is mousepad.

You should always use gksu for GUI applications. 

```
gksu mousepad /etc/modprobe.d/blacklist.conf
```

---

### Post by duncanmaybury on 2010-04-01
Great, thanks all working now!

---

