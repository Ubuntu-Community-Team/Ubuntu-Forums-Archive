---
title: "not able to access other drives"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-02
I have installed vista through virtualbox, but through vista i am not able to access my non-virtual drives. I have given path to drives under shared folders in VB.........please guide

---

### Post by blueridgedog on 2009-01-02
Note the instructions on Virtual box:

"Use 'net use x: \\vboxsvr\share" to access a shared folder named share from a Dos-like OS (read vista here), or 'mount -t vboxsf share mount_point' to access it from a linux OS.  This feature requires Guest Additions"

You will first need to install the Guest Additions.  Select Devices, then "Install Guest Additions".  This will mount a cd in the fake cdrom drive of the guest OS and you will need to run the install from there.

Once done, if you have made "files" available to the vista guest os, you can open a command prompt in vista and type:

net use G: \\SERVER\files

This assumes "G" is the drive you want to use (you can pick any) and in place of SERVER you put the name of your ubuntu box or its IP.

---

### Post by eshant_engineer on 2009-01-02
> **blueridgedog said:**
> 

net use G: \\SERVER\files



system error 67 has occured
The network name cannot be found.

---

### Post by blueridgedog on 2009-01-02
net use G:\\SERVER\files was an example, did you replace server with IP or name of your ubuntu box and "files" with the name of the directory you created?

---

### Post by theozzlives on 2009-01-02
You have to change the network adapter in VirtualBox for Vista to "Intel PRO/1000 MT Desktop (8254OEM)".

---

### Post by eshant_engineer on 2009-01-03
a

---

