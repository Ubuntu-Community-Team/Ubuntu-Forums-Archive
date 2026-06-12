---
title: "Testdisk - Can it read External USB drives?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-04
I have a external cradle usb 2.0 and an 80 gig ide (PATA)drive in it. I want to run Testdisk on or for that external drive.

1. Can I install Testdisk on my primary master (sda) drive and see the usb drive?

2. Can work be done using Testdisk on the UNMOUNTED usb drive without damanging the main drive? That is: does Testdisk write to both in the course of it's work?

---

### Post by cariboo on 2008-12-04
When you run testdisk, it will put up a menu and allow you to choose what partition you want it to run on. For more info look here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Jim

---

### Post by Mark_in_Hollywood on 2008-12-04
> **cariboo907 said:**
> When you run testdisk, it will put up a menu and allow you to choose what partition you want it to run on. For more info look here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Jim

I had already read the wiki and couln't find words about USB. I ran Testdisk from a LiveCD (Gparted) and see it finds the external drive. I wasn't able to figure out how to fix the problem. The external usb had a 'copy' of my main drive's /home. I deleted the backup /home with shift-delete. Now I need to recover that.

Do all drives have to be unmounted for Testdisk/PhotoRec to work? If I have my 'main' disk with recovery software on it, can I unmount the USB drive and use Teskdisk/PhotoRec on it?

---

