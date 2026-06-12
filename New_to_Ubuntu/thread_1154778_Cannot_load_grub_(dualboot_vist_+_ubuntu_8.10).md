---
title: "Cannot load grub (dualboot vist + ubuntu 8.10)"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2009-05-10
My friend has a laptop with vista installed. Then he installed intrepid through wubi. It worked perfectly for a while, untill he can't boot into ubuntu anymore. Vista boots fine, but not ubuntu. When i try and choose ubuntu it gives me a grub prompt. And thats it. 
I tried running
```
grub> root
(hd0,1): Filesystem type is ntfs, partition type is 0x07

grub> setup (hd0,1)
checking if "/boot/grub/stage1" exists... no
checking if :/grub/stage1" exists... no

Error 15: File not found
```

Any thoughts on what is going on and how to fix it?

---

### Post by Didius Falco on 2009-05-10
> **Abu_Dayya said:**
> My friend has a laptop with vista installed. Then he installed intrepid through wubi. It worked perfectly for a while, untill he can't boot into ubuntu anymore. Vista boots fine, but not ubuntu. When i try and choose ubuntu it gives me a grub prompt. And thats it. 
I tried running
```
grub> root
(hd0,1): Filesystem type is ntfs, partition type is 0x07

grub> setup (hd0,1)
checking if "/boot/grub/stage1" exists... no
checking if :/grub/stage1" exists... no

Error 15: File not found
```Any thoughts on what is going on and how to fix it?

Hi,

This is from the Wubi Wiki:

> **Cannot boot into Ubuntu**

 Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again. 
Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the windows explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location. 
Make sure you did not install on a RAID array or in an encrypted disk. Also make sure you did not install using an Alternate or DVD ISO. 


You can get a lot more information at that Wiki.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I hope this helps...

Regards,

Didius

---

