---
title: "Driverless Webcam in VirtualBox"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by dasajed on 2008-12-20
I discovered that my Creative Live! Cam Voice does not have a linux driver. So, I ascertained a copy of windows XP, and downloaded virtualbox and installed them both. I'm now trying to get the webcam to work in Virtual Box. I looked at the [VirtualBox USB thread]("http://ubuntuforums.org/showthread.php?t=1015474&highlight=virtualbox+usb"), but that didn't seem to fix the problem. I told VirtualBox to add an empty filter (because linux doesn't see the camera).The webcam is not showing up. Can anybody help?

Other information:
I already installed the drivers in XP because I mistook some other hardware it detected for the camera. I'm running Hardy and XP sp3. The LED on the camera does not turn on. 

 

Thanks in advance.

---

### Post by dasajed on 2008-12-20
Ok, I forgot to run the scrip mentioned in the other thread. 

However, now, when I run XP, and and plug in the camera I get the following pop-up (to virtualbox).

Failed to attach the USB device Live! Cam Voice [0102] to the virtual machine XP.

Not permitted to open the USB device, check usbfs options.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

---

### Post by dasajed on 2008-12-20
Ok. Mucking around with permissions, I got it to find the device. Now, however, when I tested the camera in Skype, I got a black rectangle instead of any video.

---

