---
title: "Problem with Windows not seeing Ubuntu's Partition on My Computer"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Alucard_Jh on 2009-03-18
Well, I am dual booting Windows XP Professional and Ubuntu 8.10 and it seems that when I'm on Ubuntu I can access the files on XP and see everything but on Windows when I click My Computer it just shows my Windows partition. Is there any possible way to fix this so Windows shows both partitions?

---

### Post by Alucard_Jh on 2009-03-18
Bring up mah post! :D

---

### Post by NE Key on 2009-03-18
I think you will have to persuade Mr Gates that his system should be compatible with the rest of the world. (This he does not like.)

Other systems try to to be compatible with every other system.

---

### Post by presence1960 on 2009-03-18
> **Alucard_Jh said:**
> Well, I am dual booting Windows XP Professional and Ubuntu 8.10 and it seems that when I'm on Ubuntu I can access the files on XP and see everything but on Windows when I click My Computer it just shows my Windows partition. Is there any possible way to fix this so Windows shows both partitions?

Windows cannot natively read/write Linux ext2/ext3 partitions. You can download a driver for Windows which will accomplish this from [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Alucard_Jh on 2009-03-18
> **presence1960 said:**
> Windows cannot natively read/write Linux ext2/ext3 partitions. You can download a driver for Windows which will accomplish this from [http://www.fs-driver.org/](http://www.fs-driver.org/)
Thank you very much. The only problem now is when I click the drive, it tells me that it hasn't been formatted yet, and I'm afraid if I click Yes let it format, it will wipe all my datas. Will it do that, or am I safe?

---

### Post by presence1960 on 2009-03-18
> **Alucard_Jh said:**
> Thank you very much. The only problem now is when I click the drive, it tells me that it hasn't been formatted yet, and I'm afraid if I click Yes let it format, it will wipe all my datas. Will it do that, or am I safe?

I do not know, that did not happen to me. Definitely **DO NOT format the drive or kiss your data goodbye!**

Maybe someone else who has used this has encountered your specific problem and can help. For reference the driver is ext2IFS.

---

### Post by egalvan on 2009-03-19
> **Alucard_Jh said:**
> when I click the drive, it tells me that it hasn't been formatted yet, if I let it format, it will wipe all my datas. Will it do that, or am I safe?

Yes, if you let it format, it will wipe your data.

This "error" occurs because the current version has problems with the newer Linux kernels,
mainly the Large Inode thing.

Here is a quote from the web site...

[I]Large inodes
The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup.[/I]

There are a couple of other projects out there to have MS read Linux, but I am  not familiar with them, 
I´ve never used them.

ErnestG

---

### Post by 73ckn797 on 2009-03-19
If the drive is ext2 it will work just fine.

---

