---
title: "Allow program to access usb"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by jjjaroscak on 2010-06-25
I have an RFID reader that I can plug into my usb drive, and I've been writing a C++ program to use it.  It works great, the only problem is I have to run my program with sudo otherwise it can't detect the RFID reader.  How do I allow my program to see the USB device without using sudo?

Thank you!

---

### Post by anewguy on 2010-06-25
This is one case where a new rule is needed in the udev rules.

Post back the output of sudo lsusb while the device is plugged in, and I'll post back what you need.

Dave ;)

---

### Post by jjjaroscak on 2010-06-25
sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 06c2:0031 Phidgets Inc. (formerly GLAB) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


it should be the Phidgets one

---

### Post by anewguy on 2010-06-26
Here's what to try:

sudo gedit /lib/udev/rules.d/100-local-permissions.rules

Should start the editor with a blank file - sudo is required in this instance.

Put the following in the file:

#  The following rule set up the Phidgets, Inc. RFID reader to be
#  be accessed by everyone.  
#  Without this, they are owned by root and causes 
#  permissions problems and a libusb error.


SUBSYSTEMS=="usb" ATTRS{idVendor}=="06c2" ATTRS{idProduct}=="0031" MODE:="0777" SYMLINK+="RFID reader 


Save the file and exit the editor.

Next, unplug your rfid reader, wait a few seconds, plug it back in and then try your program again.

I suggest this because I have some non-standard USB cameras (and I doubt your rfid reader looks like any form of "standard" USB device either) and I had to run the program as root, which also messed up my permissions on files the app created (I wrote the app in C using libusb calls).  It also caused a failure on one of the libusb calls.

This rule says the for the device identified, give everyone read/write/execute access.  This solved my problems - I hope it works for you!

Dave ;)

---

### Post by anewguy on 2010-06-30
Did this work for you or are you still having problems?

---

### Post by df26925 on 2011-06-20
This thread has been inactive for a while, but anyway thanks to **anewguy** because this worked for Weather Display (a weather station software) to acess the USB port without running it as root (wich, of course, is a bad idea...). I'm running Ubuntu 10.10

---

### Post by mensfort on 2011-06-22
I type sudo lsusb and get as reply;
Bus 006 Device 002: ID 072f:2200 Advanced Card Systems, Ltd 

Next to this rfid-reader, there is a parallel port which has a similar problem. I cannot write to this port after reset:
Bus 004 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

thanks for your help.

---

