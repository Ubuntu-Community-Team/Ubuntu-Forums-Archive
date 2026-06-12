---
title: "initrd.img?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-02-10
in my root dir there are some files which i think were not there from the start of time . initrd.img , initrd.img.old , vmlinuz and vmlinuz.old . where they came from , do i need them and if yes , why ? in properties of initrd.img.old for example it says that it is a link to a backup file , and the link target is boot/initrd.img-2.6.31-17-generic .

---

### Post by mwcrowley on 2010-02-10
Definitely leave those there.  initrd.img is your boot image. The simplified answer is that when Linux starts up, it loads initrd.img to get everything rolling.  No initrd.img, no startup.  When the kernel is updated, it installs a new initrd.img for startup.  Keep the old one around  in case the new one doesn't work, or hiccups.  
I have an old box whose ethernet did not work after a kernel update, I was able to reboot with the older kernel version, and get online to troubleshoot the issue.

---

### Post by nick_goodfate on 2010-02-10
ok i ll leave tsoe where they are . it only keeps the two last kernels ? i have updated three times my kernel , and in grub menu there four of them . so my first two kernels are just in grub menu , but they arent exist ? thnx for reply !

---

### Post by mcduck on 2010-02-10
> **nick_goodfate said:**
> ok i ll leave tsoe where they are . it only keeps the two last kernels ? i have updated three times my kernel , and in grub menu there four of them . so my first two kernels are just in grub menu , but they arent exist ? thnx for reply !

No, if they are in Grub they are also on your computer. Ubuntu never uninstalls a kernel automatically, ythat's soem,thign you need to do yourself if you want to. Just take a look inside /boot directory. (Only the latest version is linked directly into /, that's just for backwards compatibility while almost everyhting knows to look for the kernel images in /boot instead. Anyway, the files you see in / are just links and don't take any space on your drive so leave them where they are. Actually leaving files where they are is a prtty good universal advice when it comes to dealing with any system files.. ;)

---

