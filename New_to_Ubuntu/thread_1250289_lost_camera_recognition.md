---
title: "lost camera recognition"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mpennell on 2009-08-26
Issue: Camera no longer recognized by my computer. Appears to be computer, not camera (I tried a diff camera with its own cord as well).  

Thoughts?

---

### Post by Daveth on 2009-08-26
I assume, from what you say, that it used to be recognised? What sort of camera is it? Did you alter your system much, or did it "just stop"?

---

### Post by mpennell on 2009-08-26
The camera, a Fujifilm, was working fine on my Xubuntu system until one day it mysteriously stopped being recognized. It is not the camera, because a test camera also was not recognized.

---

### Post by Daveth on 2009-08-27
what happens when you plug the camera's usb cable into the pc, turn the camera on, and run lsusb in a terminal? Does it list it?

---

### Post by mpennell on 2009-08-27
Apparently not. I get:

]mark@family:~$ lsusb
Bus 001 Device 003: ID 0d49:3100 Maxtor Hi-Speed USB-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 043d:0065 Lexmark International, Inc. X5130
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Daveth on 2009-08-28
um, that is rather tiresome. I was hoping it might list something and we could try setting up a udev/rule, as noted here

[http://ubuntuforums.org/showthread.php?t=346840](http://ubuntuforums.org/showthread.php?t=346840)

but I'm a bit perplexed if it does not even "see" it. I assume you have not altered the camera's setting with respect to its usb mode setting? It might be worth re-setting that and see if it behaves.
Sorry i cannot be of much more help here.

---

