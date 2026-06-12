---
title: "My canon powershot a580 won't show up!"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ballzoboy69 on 2009-01-04
Alright, i'm not sure what version of kde i'm running, but my cameras not showing up when i plug it in. The farthest i've gotten is by going to the kmenu, then the computer tab, system settings, and then it says camera. When i click on it, it just doesn't work. The i click this menu that says add, and has a huge list of cameras, and the only powershot model not there i the a580. please help, i've used the search forum.

---

### Post by shizuto on 2009-04-20
I've got the same camera.
Did you try putting it into "Playback" mode? (i mean as opposed to the "shooting mode")

---

### Post by halitech on 2009-04-20
old thread but have you checked to see if it is being recognized?
```
lsusb
```

---

### Post by cmdrtebok on 2009-05-21
I have the A560 and I am having the same problem... lsusb shows 

```
Bus 001 Device 011: ID 04a9:314d Canon, Inc.
Bus 001 Device 006: ID 1058:0400 Western Digital Technologies, Inc. External HDD
Bus 001 Device 005: ID 1058:0600 Western Digital Technologies, Inc.
Bus 001 Device 002: ID 1058:0500 Western Digital Technologies, Inc. hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

So it does show it as devise 011, but its not shoing up in the recently connected list or dolphin.

---

### Post by anewguy on 2009-05-21
Try running an application that works with photos and cameras but run it as super user or as root, i.e.:

in a terminal window:

sudo f-spot <press enter>

See if your camera is found then.  Post back the result, since if it is found when you run as super user or root I may have the solution for you.

Dave :)

---

