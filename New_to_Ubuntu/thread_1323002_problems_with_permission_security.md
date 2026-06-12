---
title: "problems with permission security"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by oberengu on 2009-11-11
Hi,
I have some problems after I wrote in my terminal:

$sudo chown username -R/

It is now impossible to mount volume in usb, CD and no connection through wifi or wire (I am not allowed to it) My computer is completely blind.

It is no possible to reinstall ubuntu from CD because is not recognized and when I try to work with terminal it says:

$ sudo: must be setuid root

Some help please...

---

### Post by lavinog on 2009-11-11
That is a dangerous command.

You are going to need to reinstall...
Basically you changed the ownership of every file to username
I doubt you will be able to repair the ownership of every file in a timely maner.

You can still save the files on your home folder.
if username is not your username, you can chmod your files back to your username or make a backup of them.

I must know though: Why did you run that command?  Were you following a guide or another post?  If so can you post the link to it.  It should be flagged as a dangerous command.

---

### Post by oberengu on 2009-11-12
Hi,

I had some problems to mount my pendrive volume, and I typed a wrong command, because it would have been:

$sudo... -R/pendrive

I have no problem to reinstall my ubuntu, but it is no possible to mount my CD, even after starting my computer.

Do you know if it is possible to reinstall from recovery mode or some other way, because I have no permission.

Finally, thanks for your advice.

---

### Post by lotharmat on 2009-11-12
> **oberengu said:**
> Hi,

I had some problems to mount my pendrive volume, and I typed a wrong command, because it would have been:

$sudo... -R/pendrive

I have no problem to reinstall my ubuntu, but it is no possible to mount my CD, even after starting my computer.

Do you know if it is possible to reinstall from recovery mode or some other way, because I have no permission.

Finally, thanks for your advice.


Can you not change your boot order in your PC's BIOS? (Usually F10, F2 or F8.) This should allow you to boot from the Live CD and re-install from there!

---

### Post by ukripper on 2009-11-12
> **oberengu said:**
> Hi,

I had some problems to mount my pendrive volume, and I typed a wrong command, because it would have been:

$sudo... -R/pendrive

I have no problem to reinstall my ubuntu, but it is no possible to mount my CD, even after starting my computer.

Do you know if it is possible to reinstall from recovery mode or some other way, because I have no permission.

Finally, thanks for your advice.

Boot from your ubuntu 9.10 live cd and re-install.

Check bios if First boot device is set to CDROM or not.

---

### Post by oberengu on 2009-11-12
You are right! my friend.

I am now trying to recover some important files and I will reinstall all. 

I hope I won't have problems with permissions... I am not sure.

---

### Post by ukripper on 2009-11-12
Just make sure not to run this comand again without knowing! it was dangerous move.

---

