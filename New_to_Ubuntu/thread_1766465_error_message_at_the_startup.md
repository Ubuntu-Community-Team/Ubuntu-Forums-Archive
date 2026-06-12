---
title: "error message at the startup"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-05-24
This is the content of my /etc/fstab file

[B]UUID=5210A9B810A9A407 /mnt/sda1 ntfs-3g auto 0 0
UUID=b1332f0f-d55b-4082-8350-e17a14c2a316 swap swap sw 0 0
UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /mnt/sda2 ntfs-3g auto 0 0
UUID=0F75E0010C16ED5B /mnt/sda5 ntfs-3g auto 0 0
UUID=4a616438-6a2f-41c0-9f5a-b9ad54d500f0 / ext4 defaults 0 1
UUID=6AD0D8DA3589C220 /mnt/sda6 ntfs-3g auto 0 0
UUID=349551E454320BE4 /mnt/sda7 ntfs-3g auto 0 0
UUID=6C44538F27B40F61 /mnt/sda8 ntfs-3g auto 0 0
UUID=23E4386C3B553D13 /mnt/sda9 ntfs-3g auto 0 0
kevin@kevin-desktop:~$[/B]

the partition mounted on /mnt/sda2 was previously formated in ext4 format for installing Gentoo, but I gave up the Gentoo installation process of Gentoo. I wanted to use that partition for storing the data, so formated that partition in ntfs format using KDE partition damager and restarted and while i booting a got an error message that

**partition on /mnt/sda2 is not ready or not present**

**continue to wait s for skip m for manual recovery **

I am able to log in without any problem but that partition /mnt/sda2 is not going according to /etc/fstab file! Even though I gave the mounting as auto in the fstab, it is not auto mounting. Previously and now the /mnt/sda2 partition with uuid **UUID=10791e7b-df61-4a5b-a543-a250c0d1ca49 /mnt/sda2 ntfs-3g auto 0 0 is  **of the three primary partitions! 
Please Help!
Thank You!!

---

### Post by dnairb on 2011-05-24
Assuming the other ntfs partitions do mount correctly, you need to check that you have the correct UUID in your fstab file for sda2. In terminal, run:

```
sudo blkid
```

and check the UUID listed for sda2.

It looks like you are using the original UUID for sda2 when it was ext4. When it was formatted as ntfs, the UUID changed.

---

### Post by 1991sudarshan on 2011-05-24
> **dnairb said:**
> Assuming the other ntfs partitions do mount correctly, you need to check that you have the correct UUID in your fstab file for sda2. In terminal, run:

```
sudo blkid
```and check the UUID listed for sda2.

It looks like you are using the original UUID for sda2 when it was ext4. When it was formatted as ntfs, the UUID changed.

here is the output of blkid

[B]kevin@kevin-desktop:~$ sudo blkid
[sudo] password for kevin: 
/dev/sda1: UUID="5210A9B810A9A407" TYPE="ntfs" 
/dev/sda2: UUID="436111D017CE294A" TYPE="ntfs" 
/dev/sda3: UUID="4a616438-6a2f-41c0-9f5a-b9ad54d500f0" TYPE="ext4" 
/dev/sda5: UUID="0F75E0010C16ED5B" TYPE="ntfs" 
/dev/sda6: UUID="6AD0D8DA3589C220" TYPE="ntfs" 
/dev/sda7: UUID="349551E454320BE4" TYPE="ntfs" 
/dev/sda8: UUID="6C44538F27B40F61" TYPE="ntfs" 
/dev/sda9: UUID="23E4386C3B553D13" TYPE="ntfs" 
/dev/sda10: UUID="b1332f0f-d55b-4082-8350-e17a14c2a316" TYPE="swap" 
kevin@kevin-desktop:~$[/B]

It seems that the uuid of the /dev/sda2 has changed! By changing the uuid in the /etc/fstab will solve this issue?

---

### Post by dnairb on 2011-05-24
As I said, when you formatted sda2 as ntfs, the UUID changed.
Changing the UUID in your fstab file will correct the problem.

---

### Post by 1991sudarshan on 2011-05-24
> **dnairb said:**
> As I said, when you formatted sda2 as ntfs, the UUID changed.
Changing the UUID in your fstab file will correct the problem.


Thank you dnairb, that idea worked the issue is solved, Thank you so much!

---

