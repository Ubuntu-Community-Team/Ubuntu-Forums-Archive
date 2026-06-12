---
title: "Need Help Bad!  I think i wiped out my HD"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Split007 on 2009-03-13
OK about a week and a half i put ubuntu on with vista it was all fine but i decided to delete partition. So then a couple of days ago my comp got restarted then it wouldnt boot up i got grub 22 error so ive been searchin how to fix it. I cant find out anything so just now i went to put ubuntu back on and it gets hung up on partiton so i got and try agian and it shows theres no vista on the hd on the partition thing and i dont have a vista cd. plz Help i want vista back!

---

### Post by taurus on 2009-03-13
Did you tell the installer to use the whole harddrive when you reinstalled Ubuntu?  Open a terminal and post the output of this command to see if your ntfs partition is still there.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by zabien1970 on 2009-03-13
Look at this link
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by starcannon on 2009-03-13
+1 to [zabien1970]("http://ubuntuforums.org/member.php?u=333975") suggestion to use Testdisk

---

### Post by Split007 on 2009-03-13
Ok i didnt wipe thank god cuz im on the ubuntu just running from disk and i have all my documents and **** but it wont let me only use like 20gs of space for ubuntu partition? and installing ubuntu back can i get back into vista

---

### Post by louieb on 2009-03-13
Not enough information about your setup. See post #2.

for now just a guess you need to restore the MBR to boot vista. Lots of ways - did you try testdisk? or [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/"). Other ways are described here.  [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Split007 on 2009-03-13
Im still lost and if i reinstall ubuntu will it fix it cuz i kinda wanna reinstall ubuntu

---

### Post by Split007 on 2009-03-13
Plz someone i want vista back

---

### Post by taurus on 2009-03-13
If you want vista back, why don't you boot your machine with vista disc and fix the mbr, removing GRUB from it.

Otherwise, use Super GRUB Disk, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

