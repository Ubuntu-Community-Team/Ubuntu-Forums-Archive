---
title: "Help How do I install my Webcam"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2009-01-07
please Help ppl I have liek a Nexxtech cam and I have no clue how to install it on ubuntu

---

### Post by Maheriano on 2009-01-07
Most times it just works. Plug it into your machine and see if anything pops up about proprietary drivers. I doubt it will so then go into your package manager and download Cheese to your machine. Run that after it installs and it should work with your camera without problem.

---

### Post by friyia@hotmail.com on 2009-01-07
> **Maheriano said:**
> Most times it just works. Plug it into your machine and see if anything pops up about proprietary drivers. I doubt it will so then go into your package manager and download Cheese to your machine. Run that after it installs and it should work with your camera without problem.

OKay like it works in Cheese but not in My aMSN now :( how can I get it to work there?

---

### Post by Kosimo on 2009-01-07
> **friyia@hotmail.com said:**
> OKay like it works in Cheese but not in My aMSN now :( how can I get it to work there?

open a terminal and type:  ```
lsusb
```

then past here the answer, so we can try to find out the driver you need for it

---

### Post by cosimix72 on 2009-01-07
I have the same problem, the webcam (Genius) works with cheese, but does not with Skype, the image is only colored bars... 

This is what I got from lsusb first without the webcam connected and then with the webcam connected:

cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 004: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ 

Thanks in advance

---

### Post by Kosimo on 2009-01-07
> **cosimix72 said:**
> I have the same problem, the webcam (Genius) works with cheese, but does not with Skype, the image is only colored bars... 

This is what I got from lsusb first without the webcam connected and then with the webcam connected:

cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ lsusb
Bus 002 Device 004: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cosimix@cosimix-laptop:/$ 

Thanks in advance

Looks like your cam is suffering from some bug that has been reported already. Check it out here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292086](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292086)

---

### Post by friyia@hotmail.com on 2009-01-07
> **Kosimo said:**
> open a terminal and type:  ```
lsusb
```

then past here the answer, so we can try to find out the driver you need for it

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:106b Canon, Inc. S520 Printer
Bus 001 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

This is what I got man

---

