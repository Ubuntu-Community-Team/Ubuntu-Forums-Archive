---
title: "After partition resize, I can't login to ubuntu"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by hayseedix on 2011-06-18
Hello, I am running Ubuntu 10.10 on a 250 gb hdd. I choosed at installation to install all on one partition(it was recommended for beginners). But unfortunately I have to use Windows 7 too. I didn't want to format the drive so I used gparted to resize the 250 gb partition. So, I resized it, I made a 65 gb one(ntfs primary), I installed windows 7 but upon restart it boots automatically to Windows 7. I can't see ubuntu. I did try to press shift many times to bring up GRUB but nothing. What can I do in this situation? 


I'm waiting for a suggestion. Please tell me if you need other info.

---

### Post by nzjethro on 2011-06-18
Hi there, welcome to UF. First up, boot from your Ubuntu Live CD,  run the bootinfo script (in my signature), and post the results here. This will clear everything up as to what your boot situation is, and make prescribing a solution easier
.
What likely happened is that Windows overwrote Grub with the MS MBR. You should try reinstalling Grub from the Live CD. [This thread]("http://ubuntuforums.org/showthread.php?t=24113") should help.

---

