---
title: "USB Startup Creator Fail"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-04-11
I can't create a USB startup disk, it say that the disk isn't there when I try to formate it but it's clearly there. I have this usb [http://www.sandisk.com/products/computing-products/sandisk-micro-usb-flash-drive](http://www.sandisk.com/products/computing-products/sandisk-micro-usb-flash-drive) (2gb version)

---

### Post by Doctor Mike on 2010-04-11
I had one of those. They have hard to remove software embedded in them. Do a google search on removal then repartition and reformat.

---

### Post by pastalavista on 2010-04-11
I've gotten good results with the Gnome Partition Editor (gparted) on some flash drives getting rid of persistent filesystems. It's in the Software Center. Also, USB Creator has been flaky lately with things like checksums and filesystems. You could try Unetbootin, also in the software center, to create the start-up disk.

---

### Post by SpinningAround on 2010-04-14
Solved it, problem was that my native language wasn't supported since the name of the folder included letters that isn't in the English alphabet. Moved the file to another folder and it worked.

---

