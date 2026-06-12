---
title: "open usb flash"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Iceice on 2009-08-17
Hey, I want to open my usb flash drive in ubuntu. Nothing happens when i plug it in,
 and cant find it on places-computer but when i type lsusb in the terminal, it's
listed there. whats the next step to open?

izis@izis-laptop:~$ lsusb
Bus 001 Device 002: ID 174f:8a12 Syntek 0.3MPixel Web Cam - Packard Bell MX37-T-003
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Im really new at ubunty so take it slow please!
Appreciate all answers:)

---

### Post by MelDJ on 2009-08-17
try going to filesystem-mnt or filesystem-media

---

### Post by Iceice on 2009-08-17
> **MelDJ said:**
> try going to filesystem-mnt or filesystem-media

Its not working!

izis@izis-laptop:~$ filesystem-mnt
bash: filesystem-mnt: command not found
izis@izis-laptop:~$ filesystem-media
bash: filesystem-media: command not found

---

### Post by sblunix on 2009-08-17
try typing```
nautilus /media
``` in your terminal and see if it's there...

---

### Post by Iceice on 2009-08-17
A window whit two folders for CDrom opens but nothing from the usb..

---

### Post by tarps87 on 2009-08-17
I must be missing something, all I can see is a web cam and a mouse?

---

### Post by mrbiggbrain on 2009-08-17
Yeah just a Mouse and Webcam

---

### Post by perce on 2009-08-17
Maybe it can have something to do with [ this ]("http://http://en.wikipedia.org/wiki/U3")

---

### Post by Iceice on 2009-08-17
> **tarps87 said:**
> I must be missing something, all I can see is a web cam and a mouse?

Yeah, you are right.. Theres just the mouse and webcam but the usb was there before.. i dont know what happened..

---

### Post by Varg_Gorgon on 2009-08-17
I have the same problem. Ubuntu is not opening my USB drive. It used to work well with my Compaq, but the problem has started now with a Dell laptop :confused:

---

### Post by tarps87 on 2009-08-18
Could you try removing it ant plugging it in and then post the output of lsusb again and dmesg | tail
It seems strange that it would dissaper, I'm thinking it may be down to a auto run program on the usb stick (can't remember it's name).
Also can you post the output of fdisk -l (l = lower case L) if you don't see anything try running it using sudo

---

### Post by Iceice on 2009-08-22
s

---

### Post by Iceice on 2009-08-22
> **tarps87 said:**
> Could you try removing it ant plugging it in and then post the output of lsusb again and dmesg | tail
It seems strange that it would dissaper, I'm thinking it may be down to a auto run program on the usb stick (can't remember it's name).
Also can you post the output of fdisk -l (l = lower case L) if you don't see anything try running it using sudo

This is what happens:

izis@izis-laptop:~$ lsusb
Bus 001 Device 003: ID 174f:8a12 Syntek 0.3MPixel Web Cam - Packard Bell MX37-T-003
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

izis@izis-laptop:~$ dmesg | tail
[ 4522.737086] hub 3-0:1.0: unable to enumerate USB device on port 1
[ 4524.728080] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 4524.862402] usb 1-3: configuration #1 chosen from 1 choice
[ 4559.908761] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4567.921835] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4575.934156] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4598.126363] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4606.138930] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4614.151757] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 33 rq 102 len 0 ret -71
[ 4622.947224] usb 1-3: USB disconnect, address 5
izis@izis-laptop:~$ fdisk -l


Does it make any scense?

---

### Post by tarps87 on 2009-08-24
Could you post the output of
```
tailf /var/log/messages
```

Do you have any automatic setting enabled for media? It looks like it thinks it is a camera. Try disabling all auto loading programs, it is under the preferences menu but I can't remember what it is called.

---

