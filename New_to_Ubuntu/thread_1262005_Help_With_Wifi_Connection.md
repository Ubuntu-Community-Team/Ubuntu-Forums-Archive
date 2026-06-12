---
title: "Help With Wifi Connection"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by DaSkinna on 2009-09-09
I have just installed Ubuntu 8.04 LTS edition, and have had some versions before on earlyer and more "unstable" computers, anyway to get to the point, i have a Dynamode 11G wireless USB adapter and cannot get an internet connection, or even link to my wireless network, but when in Windows Vista i don't have the problem, so could anyone help me please, but explain simply because i am not too great with it

---

### Post by mapes12 on 2009-09-09
Hi

You may want to edit your thread title to something like "Help With Wifi Connection". Then others will have a better idea about your problem.

Go to Applications>Accessories>Terminal and type ```
lsusb
``` and post the out put back here please.

Forget what Visat does with wifi. Ubu does things differently.

---

### Post by Perfect Storm on 2009-09-09
> You may want to edit your thread title to something like "Help With Wifi Connection". Then others will have a better idea about your problem.

Fixed.

---

### Post by DaSkinna on 2009-09-09
right.. just done what you said and the whole screen flashed and brought me to a black screen with some white writing on it, saying "type help for a list of commands"

not going too well me thinks

---

### Post by cariboo on 2009-09-09
Open an Applications-->Accessories-->Terminal and then type the command mapes12 posted. you should get something that looks like this:

```
lsusb
Bus 001 Device 018: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 016: ID 13fd:1650 Initio Corporation 
Bus 001 Device 015: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

If you have no internet connection on the computer you installed Ubuntu on, it may be easier for you to run the command this way:

```
lsusb > lsusb.txt
```

This will create a listing of your usb devices in a text file called lsusb.txt. Copy the text file to the system you are using to post and paste it in your next post.

---

### Post by DaSkinna on 2009-09-09
i typed in the command that maples12 posted and now ubuntu won't start up, all i get is a black screen

---

### Post by DaSkinna on 2009-10-07
no... wait it has life again, i cought alt+one of the "F" Buttons
i'll make sure i post what it comes up with now. and my sincere appologies to Maples 12

---

### Post by listerdl on 2009-10-07
Hi, I dont want to hijack this thread but I have the same problem which might help Daskinna - I am unable to connect at all to the internet as well. So we both understand, does Applications>Accessories>Terminal and type 'lsusb' minus the '' give information to help us determine our machines resisitance to connect to the web?

---

### Post by DaSkinna on 2009-10-07
Bus 002 Device 004: ID 044f:b106 ThrustMaster, Inc. 
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000  

that's what it gives me

---

### Post by DaSkinna on 2009-10-07
to answer your question Listerdl, I'm not too sure as I'm new to ubuntu. so my knowledge is extremely limited so sorry if i can't be much help

---

