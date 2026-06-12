---
title: "Ubuntu on USB HHD, HDD removed wont boot Windows"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by VK743U on 2011-01-23
From a newbie. I have 10.10 desktop installed on an external USD HDD, dual booting with Vista.  If I remove the HDD from the system it won't boot Vista.  Any help would be appreciated, as I have to use the USB HDD as the Vista HDD is nearly full.

---

### Post by Linyx on 2011-01-23
> **VK743U said:**
> From a newbie. I have 10.10 desktop installed on an external USD HDD, dual booting with Vista.  If I remove the HDD from the system it won't boot Vista.  Any help would be appreciated, as I have to use the USB HDD as the Vista HDD is nearly full.

You means to say that your internal Hdd contain vista and External Contain Ubuntu...?

Please Explain it a little bit

---

### Post by wilee-nilee on 2011-01-23
1) Boot with your Vista installation or recovery disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
```
BootRec.exe /fixmbr
```

Above is a link to a visual tutorial of the commands, below is a Vista recovery disc link.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You will probably have to load the external with grub2 to boot it, ask any questions as needed.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by VK743U on 2011-01-24
All fixed - Thanks for the help.

---

