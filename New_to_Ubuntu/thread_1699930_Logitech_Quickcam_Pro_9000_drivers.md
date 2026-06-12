---
title: "Logitech Quickcam Pro 9000 drivers?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by TAspr on 2011-03-04
Hello, can you guys tell me what I need to do to get this cam working?  Is it similar to the .tar.gz. file installation?  Also, can I specify where I would like to install the drivers, Wether it be home, user, etc., etc. and still keep the reference to the icon in the right location?

---

### Post by maqtanim on 2011-03-04
Connect the camera in your computer and post the output of the following command:
```
lsusb
```

---

### Post by TAspr on 2011-03-04
PC:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:0821 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
PC:~$ ^C
PC:~$ ^C
PC:~$ ^C
PC:~$

---

### Post by maqtanim on 2011-03-04
> **TAspr said:**
> PC:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:0821 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

See the line 
Bus 001 Device 003: ID 046d:0821 Logitech, Inc. 
which means ubuntu detects your webcam. 

Now the question is, How did you try to test/run the webcam? Install **Cheese** from Ubuntu Software Center and see whether Cheese can detect your webcam? After installing Cheese, you'll find this program in **Applications > Sound & Video > Cheese Webcam Booth**.

---

### Post by TAspr on 2011-03-04
> **maqtanim said:**
> See the line 
Bus 001 Device 003: ID 046d:0821 Logitech, Inc. 
which means ubuntu detects your webcam. 

Now the question is, How did you try to test/run the webcam? Install **Cheese** from Ubuntu Software Center and see whether Cheese can detect your webcam? After installing Cheese, you'll find this program in **Applications > Sound & Video > Cheese Webcam Booth**.

Well, I did notice it displaying with the program called **Cheese, **but I also installed Skype, and it would not recognise the web cam.It did not give me the normal controls that Skype has had, example, video button.

---

### Post by maqtanim on 2011-03-04
Just go to the Settings of Skype, then go to OPTIONS > VIDEO DEVICES. Tick the option ENABLE SKYPE VIDEO. Then test the webcam.

---

### Post by TAspr on 2011-03-04
Cool, I will try it.  Thanks for all your help.  

You know the more and more I use Ubuntu, the more I like it.

---

