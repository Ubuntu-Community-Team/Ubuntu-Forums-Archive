---
title: "Sately Removing a USB Device"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mpl34 on 2009-02-23
Hi

I am really getting frustrated at the fact i cannot safely remove my external harddrives in vista and therefore am required to make a forced connection in linux.

I have tried to restart vista with them plugged in and on then remove them and restart with them disconnected then connect them once fully booted then remove them. I have been unsuccessfull.

What i would like to know is whether forcing the connection in linux can cause any harm to the drive or if there is a better way to safely move the drive through vista.

Cheers,

---

### Post by blazemore on 2009-02-23
It certainly won't cause any harm to the drive.
It could potentially bugger the filesystem, so your best bet is to shut down Windows properly, and run chkdsk every now and then.

---

### Post by mpl34 on 2009-02-23
I just shutdown windows correctly and also ran chkdsk on boot and can still not safely remove my drives any other ideas? I can't find any program that should be using the harddrives

---

### Post by bertolo on 2009-02-23
there is no problem in removing a usb pen without being umounted. be sure that there is no file transfer on the way.
external hard drives are just like big usb pen.

---

### Post by mpl34 on 2009-02-23
Yer i realise that there is no problem removing the drive without having preformed a safe removal however the problem arises when connecting the drive when running linux. Linux reports the error that the drive has not been safely removed and is required to be forced... or something a rather. 

I have no problem forcing the connection if this is known not to cause damage to the drive or its data, however if there is a possibility to remove it correctly through vista i would prefer this option. 

Thanks

---

### Post by binbash on 2009-02-23
then umount it...

---

### Post by Bölvaður on 2009-02-23
ok I have never used Vista but I think you are indeed able to unmount it. They may have changed the name of it to 'Eject' or still have it as 'Saftly remove device' somewhere in the file browser or if you right click.

Atleast I have always got people to unmount my usb sticks.

---

### Post by mpl34 on 2009-02-23
Yer i can right click and safely remove and have have been trying this process aswell but i get the same error

EDIT: Well i'm gona head off to bed now but will try again in the morning please keep posting advice but i may just settle with frocing the connection each time

---

