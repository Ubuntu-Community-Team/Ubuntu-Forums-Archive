---
title: "Identifying path to a USB drive"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2010-10-10
Hi all

Running Ubuntu 10.04 server and have a USB desktop drive identified as '164 GB Filesystem'.

Need to enter the path to this device in an app, so what would the path be, please?

Another point, how do you mark a thread as 'Solved'?

TIA

---

### Post by HermanAB on 2010-10-10
Howdy,

If you give the USB device a Volume Label, the the path will be /media/Label.

Read the mkfs.vfat man page to see how to set the label.

Edit your post and change the subject line.

---

### Post by ChrisRChamberlain on 2010-10-10
HermanAB

Thanks for reply.

Rightly or wrongly, formatted the drive, (it was empty), renamed to 'Movies', mounted again, and thus the path became '/media/Movies/'

---

