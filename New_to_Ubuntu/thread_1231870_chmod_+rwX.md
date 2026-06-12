---
title: "chmod +rwX"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by diablofatt on 2009-08-05
So I was told on the Heroes of Newerth beta forum to 

> chmod +rwX the install directory and chown it to your user.

:confused:How exactly does one do that? What does it mean? What is it good for? 

My directory is saved to /home/thorn/.HoN


Thank you.

---

### Post by credobyte on 2009-08-05
chmod:
```
sudo chmod +rwx /home/thorn/.HoN
```

chown:
```
sudo chown -R thorn:thorn /home/thorn/.HoN
```

---

### Post by hyperAura on 2009-08-05
well the first command is to set permissions, to be able to read, write and execute .HoN 
and the second command is to change the ownership of .HoN file 
i hope this answers the second part of ur question..

---

### Post by slick1a on 2009-08-05
Im having a few issues with these commands too.

I understand what it is they do..but..i have a dilema.

I noticed that the 8gig card in my fone was missing 5.6gig allowing me not to have the full capacity in use...

at this point i tried : reformatting in my fone - no joy there, then i tried the following: 

slick@slick-desktop:~$  sudo mkfs.ext3 /dev/sdf1
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdf1 is mounted; will not make a filesystem here!
slick@slick-desktop:~$  sudo mkfs.ext3 /dev/sdf1
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
485760 inodes, 1939456 blocks
96972 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1988100096
60 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
slick@slick-desktop:~$ sudo e2label /dev/sdf1 usb-pen-fone

SDF1 - is the usb Sd card in question from my fone, however when i reinsert said card to my fone , the fone will not recognise it as external memory!

I fear i have turn my sd card into something else!    

Whilst the above in part worked, illiminating all previous folders and returning my missing capacity, im left with only one folder "lost and found" unable to create another folder along side it but able to create a folder within and to write to the lost and found folder.

but alas my fone will not read or find this folder..my fone is not the problem here...its my poor teching.

---

### Post by slick1a on 2009-08-09
issue now resolved...

---

### Post by colau on 2009-08-15
Cheers.

---

