---
title: "NTFS disk not visible under 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by bumblerbill on 2009-04-25
I've just upgraded Ubuntu from 8.10 to 9.04. On the notebook, Linux is installed in an NTFS directory and dual-boots via GRUB. Previously I had managed to make the NTFS folders and files accessible. Now they're not present.  I know enough to know not to go beyond the following steps without guidance.  Clues would be most welcome![br]!!![/br] [br]!!![/br] bumbler@ubuntu:~$ sudo fdisk -l[br]!!![/br] [br]!!![/br] Disk /dev/sda: 250.0 GB, 250059350016 bytes[br]!!![/br] 255 heads, 63 sectors/track, 30401 cylinders[br]!!![/br] Units = cylinders of 16065 * 512 = 8225280 bytes[br]!!![/br] Disk identifier: 0xf573430c[br]!!![/br] [br]!!![/br] Device Boot Start End Blocks Id System[br]!!![/br] /dev/sda1 * 1 30401 244196001 7 HPFS/NTFS[br]!!![/br] bumbler@ubuntu:~$ ls /dev/disk/by-label -lah[br]!!![/br] total 0[br]!!![/br] drwxr-xr-x 2 root root 60 2009-04-25 09:48 .[br]!!![/br] drwxr-xr-x 6 root root 120 2009-04-25 09:48 ..[br]!!![/br] lrwxrwxrwx 1 root root 10 2009-04-25 09:48 Bumbler_Notebook -> ../../sda1

---

### Post by Spiritous on 2009-04-25
> **bumblerbill said:**
> I've just upgraded Ubuntu from 8.10 to 9.04. On the notebook, Linux is installed in an NTFS directory and dual-boots via GRUB. Previously I had managed to make the NTFS folders and files accessible. Now they're not present.  I know enough to know not to go beyond the following steps without guidance.  Clues would be most welcome![br]!!![/br] [br]!!![/br] bumbler@ubuntu:~$ sudo fdisk -l[br]!!![/br] [br]!!![/br] Disk /dev/sda: 250.0 GB, 250059350016 bytes[br]!!![/br] 255 heads, 63 sectors/track, 30401 cylinders[br]!!![/br] Units = cylinders of 16065 * 512 = 8225280 bytes[br]!!![/br] Disk identifier: 0xf573430c[br]!!![/br] [br]!!![/br] Device Boot Start End Blocks Id System[br]!!![/br] /dev/sda1 * 1 30401 244196001 7 HPFS/NTFS[br]!!![/br] bumbler@ubuntu:~$ ls /dev/disk/by-label -lah[br]!!![/br] total 0[br]!!![/br] drwxr-xr-x 2 root root 60 2009-04-25 09:48 .[br]!!![/br] drwxr-xr-x 6 root root 120 2009-04-25 09:48 ..[br]!!![/br] lrwxrwxrwx 1 root root 10 2009-04-25 09:48 Bumbler_Notebook -> ../../sda1
Is it a good idea to install ubuntu in NTFS? It should be in ext3 / ext4... Do you want to dual-boot?

---

### Post by bumblerbill on 2009-04-25
> **Spiritous said:**
> Is it a good idea to install ubuntu in NTFS? It should be in ext3 / ext4... Do you want to dual-boot?

 It is if you can't install to a separate partition, and I can't on this particular laptop. I believe it has something to do with the way the DVD drive is set up. In any event, I had installed Ubuntu 8.10 in an NTFS directory, as I mentioned, and GRUB allows me to boot either Windows or Linux. Now that I have have upgraded to 9.04, the NTFS directories and files are invisible to Linux. They are visible to Windows.

---

### Post by Old_Grey_Wolf on 2009-04-25
See if post #3 in this thread helps. [http://ubuntuforums.org/showthread.php?t=1129237&highlight=enable+ntfs](http://ubuntuforums.org/showthread.php?t=1129237&highlight=enable+ntfs)

---

### Post by bumblerbill on 2009-04-25
> **Old_Gray_Wolf said:**
> See if post #3 in this thread helps. [http://ubuntuforums.org/showthread.php?t=1129237&highlight=enable+ntfs](http://ubuntuforums.org/showthread.php?t=1129237&highlight=enable+ntfs)

in a second or 2 you will see a program called NTFS configuration tool. [br]!!![/br] Put a check in the box beside it and then apply changes. [br]!!![/br] I had already done this. [br]!!![/br] [br]!!![/br] &quot;System-Administration-NTFS Configuration tool&quot; [br]!!![/br] After launching the tool just check the boxes next to both enable read and write to internal and external drives. [br]!!![/br] I had already tried this. The internal device line (top line) is grayed. &quot;External device&quot; is not grayed. Previously I hadn't checked it because there is no external drive. [br]!!![/br] So I selected &quot;enable write support for external drive&quot;. No change. [br]!!![/br] [br]!!![/br] If I navigate to /dev/sda1 and select it, I am told &quot;There is no application installed for block device files.&quot;[br]!!![/br] [br]!!![/br] I think it's not going to be possible to enable write support for a device that the OS can't even see.

---

### Post by bumblerbill on 2009-04-26
So here's the solution to the problem: I removed Ubuntu 9.04 and reinstalled instead of updating 8.10. This time the partitioner was successful in creating a partition for Linux, so I didn't need to use the procedure that installs Linux in an NTFS partition directory. Following the new installation, the NFTS partition was again available and could be mounted r/w.

---

