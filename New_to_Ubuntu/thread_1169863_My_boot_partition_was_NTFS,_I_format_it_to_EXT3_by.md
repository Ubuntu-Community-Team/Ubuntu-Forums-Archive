---
title: "My boot partition was NTFS, I format it to EXT3 by mistake, what should I do now?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-25
Hi
I realized that I format my boot partition from NTFS to EXT3 and certainly all boot information are gone.

Do you know what should I do to be able to boot into my system after I restart this session?

Here is the content of menu.lst. My Linux is installed in /dev/sda4 and the boot partition is /dev/sda1 and now it is formatted as EXT3.

```


title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		82ed7e34-910c-47ad-9766-f3faf190f2f1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=82ed7e34-910c-47ad-9766-f3faf190f2f1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		82ed7e34-910c-47ad-9766-f3faf190f2f1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=82ed7e34-910c-47ad-9766-f3faf190f2f1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		82ed7e34-910c-47ad-9766-f3faf190f2f1
kernel		/boot/memtest86+.bin
quiet

```

Thanks.

---

### Post by lwvmobile on 2009-05-25
If you truly did format your NTFS partition to EXT3 then your Windows partition plus data are pretty much toast.

Can you open terminal and give us the output of this command.

```
sudo fdisk -l
```

If it is partitioned, there are ways to recover files like pictures and documents to a point using special software, which is available in Ubuntu, but it will lose its name associations, and just be random, but there is still a way to recover some files.

I just re-read your thread, did you just use that partition to boot from or was it Windows too?

---

### Post by hexanol on 2009-05-25
I would say you are cook. When you created the ext3 file-system, a certain amount (but how much -- I don't know exactly) of sectors were written, and I doubt there's a recovery utility capable of undoing what you have done.

---

### Post by sisco311 on 2009-05-25
Edit:

Sorry, I miss read your post, it seems you don't have a separate /boot partition. 

Did you reformat the Windows partition?

---

### Post by legolas_w on 2009-05-26
Hello everyone and thank you for your help.
I fixed the boot problem using the guidelines provided at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks.

---

