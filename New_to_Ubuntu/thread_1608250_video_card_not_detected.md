---
title: "video card not detected"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by manny43 on 2010-10-28
Hello friends

DELL B110

After removing e-GeForce FX 5200 NVIDIA VIDEO CARD due to its damaged fan i'm
getting te following message: 

Ubuntu is running in low-graphic mode
The following error was encountered.You may need to update your configuration to solve this.

(EE) No devices detected.

Is there a way to make Ubuntu detect integrated video card since pci video card is no longer attached to motherboard.

This the driver that was activated when pci card was installed:
NVIDIA accelerated graphics driver version 173.

Im not sure if i have to uninstall this driver

Please help me with this problem.Thanks

---

### Post by ubudog on 2010-10-28
First of all, check if Ubuntu can see it:

```
lspci
```

You may end up having to reinstall. :(

---

### Post by beew on 2010-10-28
I think the nvidia-173 is not supported in Maverick, this seems to be the case since "Additional Drivers" doesn't detect it. If that is the case reinstalling won't do you any good. 

First maybe you should check the support status of the Nvidia-173 driver (I heard that it has been updated lately so it is supported, in that case maybe you can install it from Synaptic)

I have managed to install the nvidia-96 driver in Maverick even though it is not supported. Someone reported success in installing the nvidia-173 driver using the same trick as well
[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

There is another way that uses the nouveau driver and some 3d-acceleration package. I don't know if it works for nvidia-173(it is for nvidia-96), it works for some people but didn't work for me.
[http://ubuntuforums.org/showthread.php?t=1590367&page=1](http://ubuntuforums.org/showthread.php?t=1590367&page=1)

---

