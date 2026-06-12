---
title: "How fast Netbook Remix installs on a netbook? Something's off in my case"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Julita on 2009-12-12
Hello! I am currently installing UNR on my netbook. I used unetbootin. When I clicked on "default" choice, a small white mouse circle (when sth is launching) appeared on a black screen, and it is there for more than 40 minutes. Before that, I used usb creator, but the result was the same. Is this normal for an install from the flash? CPU is 1.6GHz Intel Atom with 1GB RAM.

---

### Post by Julita on 2009-12-12
Please, hjalp!

---

### Post by Cheesemill on 2009-12-12
Something is definitely not right.
It usually takes me only 10-15 minutes to complete a netbook install.

What's your hardware?

---

### Post by Julita on 2009-12-12
My netbook is Asus EEE PC 1001HA (clone of 1005.) It might be the problem with my flash - Kingston DataTraveler 8GB. Could it be that the size of the flash is too big?

---

### Post by AlphaWhelp on 2009-12-12
I managed to install UNR on my Asus EEE PC 1005 with no problems from a 2gig flash drive.  Perhaps your bootable flash drive was not created correctly?

---

### Post by Julita on 2009-12-12
I tried it with two different apps (of course, it was formatted before each install) - first, with usb creator, the second time with unetbootin, with the same result described above. *confused*

---

### Post by anaconda on 2009-12-12
> **Julita said:**
> My netbook is Asus EEE PC 1001HA (clone of 1005.) It might be the problem with my flash - Kingston DataTraveler 8GB. Could it be that the size of the flash is too big?

Mine installed in about 3 hours! (a bit more actually)

I think it took that long because I have a really slow 8GB SSD disk in it...

I actually thought that SSD disks would be faster than normal hard disks.

Oh And I have asus aspire one..

EDIT, and then installing the updates took over an hour on top of that.. (downloading took 30mins, and the installing 1,5hours)

---

### Post by Julita on 2009-12-12
anaconda, mine is a hard drive of 160GB. In fact, the advantage of SSD is that they are carrying-friendly, they are less sensitive to "shaky" environment (e.g., in a bus on the baaad road)... But 8GB storage is really small for me... *sigh*

---

### Post by Merk42 on 2009-12-12
Maybe [check the md5sum](https://help.ubuntu.com/community/HowToMD5SUM) of the iso you downloaded to make sure it wasn't corrupt

---

### Post by 3rdalbum on 2009-12-12
The white Ubuntu logo shows that the live Ubuntu system is loading. After the syystem has loaded, the installer program will run.

In other words, it's not reaching the installer.

Check the MD5 sum hash of the disc image you downloaded. If that comes up clean, try searching for tips on booting Ubuntu on your specific machine as there might be some hardware incompatibility there...

If your disc image is corrupt (the md5 sums don't match), try downloading Ubuntu again using Bittorrent.

---

### Post by Julita on 2009-12-13
Thank you for information! I downloaded both from torrents and direct download, and the result was the same. Later I installed .img of 9.04, and it worked!

---

