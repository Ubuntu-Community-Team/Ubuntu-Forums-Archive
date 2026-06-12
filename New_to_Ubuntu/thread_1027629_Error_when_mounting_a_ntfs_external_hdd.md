---
title: "Error when mounting a ntfs external hdd"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by arya6000 on 2009-01-01
Hello


I installed ubuntu 8.10, everything is working good, but when I connected my ntfs external hard drive, and tried accessing it from Places --> OneTouch 4 I get a long error, I have attached the screen shot of the error. I would appreciate any help on making this work.


Thank You

---

### Post by newbee70 on 2009-01-01
> **arya6000 said:**
> Hello


I installed ubuntu 8.10, everything is working good, but when I connected my ntfs external hard drive, and tried accessing it from Places --> OneTouch 4 I get a long error, I have attached the screen shot of the error. I would appreciate any help on making this work.


Thank You

Did you follow the advice on the error report?

---

### Post by marcgh on 2009-01-01
I had the same problem just yesterday and solved it as follows:
opened my windows session
plugged the external drive in
Then did the 'safely remove hardware'
went back to Ubuntu ...done, external HDD mounted.
Hope this will help you.

---

### Post by drs305 on 2009-01-01
What the previous posters suggested should do the trick. If not, you can do a search on these forums for mounting using the "force" option or using "ntfsfix". These are *not* preferable to the previous solution but may work if the first one doesn't or you don't have access to a windows machine.

---

### Post by balloooza on 2009-01-01
> using the "force" option or using "ntfsfix"
I can tell you here, run
```
sudo mkdir /media/exharddrive
```
```
sudo ntfs-3g /dev/sdb1 /media/exharddrive -o force
```
this will mount it, and place an icon on the desktop, then run
```
sudo umount /dev/sdb1
```
to cleanly unmount it.
same  as mounting it in windows, just thought you would like to
> enjoy a life without walls and fences

---

### Post by nothingspecial on 2009-01-01
```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/yourdrive
```

To find your drive```
 sudo fdisk -l
```

look down the list and determine which it is. Do not choose the wrong one.
To be sure you could type ```
mount
```
The drive you want to apply ntfsfix is the one in the output of fdisk -l but not the output of mount
If you`re not sure post back

---

