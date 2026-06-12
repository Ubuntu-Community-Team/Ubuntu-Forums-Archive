---
title: "How to access hardware"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by imtired111 on 2010-11-04
Could someone tell me how to access a list of hardware? i cant seem to find an application for it so im assuming it is in terminal. only one problem. im not good at using terminal.

---

### Post by Enigmapond on 2010-11-04
A list of hardware? Can you be more specific? What exactly are you looking for?

---

### Post by Zill on 2010-11-04
imtired111:  1)  Open a terminal.  Enter the following code:
```
sudo lshw -html > ~/Desktop/hardware.html
```
2)  Enter your logon password.

3)  Click on the "hardware.html" file on your Desktop and all your hardware will be listed in your web browser.

---

### Post by Hippytaff on 2010-11-04
```

lshw

```
is that what your looking for?

---

### Post by imtired111 on 2010-11-04
i am looking for a list of installed hardware such as usb drives etc. i am trying to see if my sd reader is recognized by the system.

---

### Post by Hippytaff on 2010-11-04
```

lsusb

```
for usb devices and
```

lspci

```
for pci devices

---

### Post by imtired111 on 2010-11-04
thank you all.

---

### Post by Enigmapond on 2010-11-04
Read this thread..:)

[http://ubuntuforums.org/showthread.php?t=880497](http://ubuntuforums.org/showthread.php?t=880497)

also just type in the terminal:

```
lspci
```

---

### Post by mcduck on 2010-11-04
> **imtired111 said:**
> i am looking for a list of installed hardware such as usb drives etc. i am trying to see if my sd reader is recognized by the system.

The suggested lsusb and lshw commands should do the trick.

But there's even a better way of checking if removable devices like USB drives are recognized correctly or not. Just open a terminal and run "*tail -f /var/log/messages*" and then plug in the device. You'll see the messages about how the device is recognized, what drivers are used for it, and if it's a usb drive also where it's mounted etc.

Saves you from scrolling the full output of lshw, and also works for troubleshooting in case a device isn't recognized or doesn't have a driver.

(as an explanation, "tail" reads the last lines of a text file, and the -f option tells it to keep reading the file so it will print any new lines to you as they are added to the file. And /var/log/messages is one of the system log files.)

---

### Post by Hippytaff on 2010-11-04
> **mcduck said:**
> The suggested lsusb and lshw commands should do the trick.
 
But there's even a better way of checking if removable devices like USB drives are recognized correctly or not. Just open a terminal and run "*tail -f /var/log/messages*" and then plug in the device. You'll see the messages about how the device is recognized, what drivers are used for it, and if it's a usb drive also where it's mounted etc.
 
Saves you from scrolling the full output of lshw, and also works for troubleshooting in case a device isn't recognized or doesn't have a driver.
 
(as an explanation, "tail" reads the last lines of a text file, and the -f option tells it to keep reading the file so it will print any new lines to you as they are added to the file. And /var/log/messages is one of the system log files.)
 
Nice :-) I'll add that to my list of useful commands!

---

