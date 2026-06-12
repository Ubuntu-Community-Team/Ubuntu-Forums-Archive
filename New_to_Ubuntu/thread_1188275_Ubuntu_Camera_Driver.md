---
title: "Ubuntu Camera Driver"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by alket on 2009-06-15
I have a Sony Camera (not webcam) that i plugged in USB port, but nothing happens, i think that the driver is missing, how can i install them ?

---

### Post by alket on 2009-06-16
> **babaroga said:**
> I have a Sony Camera (not webcam) that i plugged in USB port, but nothing happens, i think that the driver is missing, how can i install them ?

please help, its a Digital Camera ?

---

### Post by Amilo1718 on 2009-06-16
got the same issue with a sanyo :p
:popcorn:

---

### Post by unutbu on 2009-06-16
What is the output of 
```

lsusb
```

---

### Post by alket on 2009-06-16
```
Bus 002 Device 004: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92/W1 Cybershot/Mavica Digital Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0810:0001 Personal Communication Systems, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by philinux on 2009-06-16
Install the application gthumb. Add remove/ synaptic or..

In firefox webrowser address bar type this.

apt://gthumb

The app is run from Applications>graphics

This app usually detects the camera.

---

### Post by unutbu on 2009-06-16
Hurray! Ubuntu is detecting your Sony camera:
```

Bus 002 Device 004: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92/W1
```

Check in the ~/.gvfs directory. If you use Nautilus, this directory may be hidden (because its name starts with a period). You can press Ctrl-h in the Nautilus file browser to show these hidden files. Look inside the ~/.gvfs directory. There should be a subdirectory in there which contais the images on your camera's data card.

If you do not find the images in there, please post the output of 
```

dpkg --get-selections | grep gvfs
dpkg --get-selections | grep gphoto
ls -l ~/.gvfs


```

---

### Post by alket on 2009-06-16
> **philinux said:**
> Install the application gthumb. Add remove/ synaptic or..

In firefox webrowser address bar type this.

apt://gthumb

The app is run from Applications>graphics

This app usually detects the camera.

Its not working ,I tried Import Photos option and it sad "No camera detected".

---

### Post by alket on 2009-06-16
```
xxx-laptop:~$ dpkg --get-selections | grep gvfs
gvfs						install
gvfs-backends					install
gvfs-bin					install
gvfs-fuse					install
libgvfscommon0					install
xxx-laptop:~$ dpkg --get-selections | grep gphoto
libgphoto2-2					install
libgphoto2-port0				install
xxx-laptop:~$ ls -l ~/.gvfs
total 0

```

---

### Post by unutbu on 2009-06-16
babaroga, perhaps try installing the gphoto2 package. Then turn off the camera, unplug in from the USB port. Then plug it back into the USB port and turn on the camera. Then check if the files are mounted in ~/.gvfs.

---

### Post by Amilo1718 on 2009-06-16
works like a charm for me 
thanks

edit: but i also installed other apps like gthumb & flphoto...

---

### Post by alket on 2009-06-18
in gThumb , Import Photos options says:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

---

### Post by alket on 2009-06-18
please ?

---

### Post by Amilo1718 on 2009-06-18
gphoto didn't work?

---

### Post by alket on 2009-06-18
> **Amilo1718 said:**
> gphoto didn't work?

No, even gphoto displayed the same error message.

---

### Post by unutbu on 2009-06-18
babaroga, perhaps try this: [http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

---

### Post by Sealbhach on 2009-06-18
Another suggestion from here, make a change in your camera settings:

[http://ubuntuforums.org/showpost.php?p=4660948&postcount=3](http://ubuntuforums.org/showpost.php?p=4660948&postcount=3)

.

---

### Post by alket on 2009-06-18
> **Sealbhach said:**
> Another suggestion from here, make a change in your camera settings:

[http://ubuntuforums.org/showpost.php?p=4660948&postcount=3](http://ubuntuforums.org/showpost.php?p=4660948&postcount=3)

.

wow, thank you.

---

