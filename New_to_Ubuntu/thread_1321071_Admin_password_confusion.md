---
title: "Admin password confusion"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by JoshinBuffalo on 2009-11-09
I installed 9.10 on a 4 GB USB flash drive using USB System Creator utility, and selecting for a 'persistent' install.  I was not prompted to create user accounts.  Running firefox I tried to install Adobe flash - but was prompted for an admin password.  As I had never set one, I didnt know how to respond.  Null response didn't satisfy the OS.  I've found other places within the OS that also require admin PW which I can't provide.

So I tried to create a password for the 'root' user account (couldn't really tell if I was successful - no confirmation response), and also created a new user account, which I gave admin privileges to (both through the OS GUI).  Oddly I wasn't prompted for a password to create that account, but it's properties now include 'administration'.

So, back to firefox, and I still am denied the ability to add modules because the admin password is not accepted.

What next?  Thanks for the help.  In the mean time I'm working through 'the manual'.

-Josh
Lenovo Y510

---

### Post by Bunnybugs on 2009-11-09
The live-cd mode isn't made to install stuff in...

That means that you don't need the password function... that's why you don't have an PW...

If you boot Ubuntu on an USB drive, using the ISO, makes your flashdrive an USB live-cd, not actually a system on a stick!

---

### Post by sgosnell on 2009-11-09
However, you can install from that drive to another USB drive, and get a standard install.  What you download is an installation CD (which can be put on a USB drive) and you use that to actually install the OS.  You'll need, temporarily, two USB drives or an SD card, or a CD drive.  Once the install is done to the second drive, the original one can be reformatted and reused, if desired, unless you put it on a CD.

---

### Post by JoshinBuffalo on 2009-11-10
I don't think the USB is a LiveUSB after this process.  I selected for persistence using the USB Startup Disk Creator, and this is working.  For example, new user accounts I created persist after reboot.

This [link]("http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/") describes the process.

Any other thoughts? Thanks!

---

### Post by TironN on 2009-11-10
Its persistent for data but installing programs is difficult

---

### Post by sgosnell on 2009-11-10
That's not the same as a regular install, though.  If you want full functionality, you have to do a full install, and that's easy with Ubuntu.

---

