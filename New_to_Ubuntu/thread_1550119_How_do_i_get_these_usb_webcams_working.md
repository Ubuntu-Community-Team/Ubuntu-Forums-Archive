---
title: "How do i get these usb webcams working"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-10
I have a bunch of iMicro webcams... they are a simple as they get i got them for like $8 but I dont know how to use them with ubuntu or ZoneMinder

---

### Post by dca on 2010-08-10
If they're USB, plug them in, open terminal and type *sudo lsusb*
 
...see if they're recognized, if so, open Synaptic or Ubuntu Software Center, install 'Cheese' application, and see if you get an image...

---

### Post by e.jejcic on 2010-08-10
Sorry to disrupt in this manner, but I have the same webcam and the same problem. Mine is Microdia webcam and I get a fairly dark picture (in Cheerse).My camer4a ID is 0c45:6143 and I am unable to get driver for it. Thanks in advance.

---

### Post by Spacestationmax on 2010-08-10
> **dca said:**
> If they're USB, plug them in, open terminal and type *sudo lsusb*
 
...see if they're recognized, if so, open Synaptic or Ubuntu Software Center, install 'Cheese' application, and see if you get an image...

=========
max@EeePC901:~$ sudo lsusb
[sudo] password for max: 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6128 Microdia 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==============

Cheese webcam booth just quits after it loads??

---

### Post by sandyd on 2010-08-10
should work since the 2.6.31 kernel -> [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

---

### Post by Spacestationmax on 2010-08-11
> **carlee said:**
> should work since the 2.6.31 kernel -> [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

I will check it out.... Thanks

---

