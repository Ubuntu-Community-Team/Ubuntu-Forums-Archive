---
title: "Mount Canon Ixus 430 camera USB"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by misterspider on 2010-07-02
I need to start a new thread about this even though similar issues have been covered previously [here]("http://ubuntuforums.org/showthread.php?t=1478199").

I have a canon digital camera that does not mount when I plug in via usb. I have had this pc hardware for a while, and previous distros installed on the same hardware have not had this issue. The only new item of hardware in the pc is an SSD. 

I did a fresh install of Xubuntu 10-04 desktop with no issues during installation.

```
david@david-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04a9:30ba Canon, Inc. PowerShot S410 Digital Elph
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The camera is being detected, but I would like to know how to mount it from this information.

---

### Post by lkjoel on 2010-07-02
Could you please show me the output of this command?
```
sudo dir /media
```

---

### Post by misterspider on 2010-07-02
```
$ sudo dir /media
[sudo] password for david: 
floppy	floppy0

```

---

### Post by lkjoel on 2010-07-03
Type this in a terminal:
```
sudo nautilus --no-desktop --browser
```
And check if you see your camera.

I know that there are some camera packages in the synaptic.

---

### Post by misterspider on 2010-07-03
I've given this command a try now, all I can see is root, desktop, File System, Network, floppy0, and Trash.

---

### Post by misterspider on 2010-07-03
I've added F-Spot from the synaptic packages, this has let me find the camera. 

I would like to be able to find it in a file manager though!

---

### Post by lkjoel on 2010-07-04
Is there any SD cards?
Mount them instead.

---

