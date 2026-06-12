---
title: "Ext3 or Ext4 which is better? Size of Root partition?"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-24
I just put jaunty on my laptop (took some getting used to - long time windows user) and now plan to go all the way and put on my PC then create a wireless network between them using a TP-Link ADSL WIRELESS ROUTER.  I have been reading that there seems to be some problems with Ext4 also how big does root actually need to be as I understand it all programs are in \home\username

---

### Post by Penguin Guy on 2009-08-24
Ext3 is the default because there are a few problems with ext4. I believe when Karmic comes out, that will use ext4. Unless you specifically want ext4 for some particular reason, just stick with ext3. As for how big your / partition needs to be, it depends on how you want to partition your disk.

---

### Post by k3lt01 on 2009-08-24
We have 3 computers running ext4 and have not had a problem yet.

As for the root / partition I set mine at 10gb in the partitioning section of the installer. Take a look at the screenshot to see how much room I have used on it and you will see that 10gb gives plenty of room to move.

I don't think the programs are in /home/username, I thought they were in /usr and more specifically /usr/bin

---

### Post by Paqman on 2009-08-24
> **Penguin Guy said:**
> I believe when Karmic comes out, that will use ext4.

Jaunty uses ext4 if you tell it to during install, but yes, Karmic will use it by default for new partitions.

Ext4 is all good. Ext3 is more widely supported by 3rd party tools though.

---

### Post by chris1950 on 2009-08-24
> **k3lt01 said:**
> We have 3 computers running ext4 and have not had a problem yet.

As for the root / partition I set mine at 10gb in the partitioning section of the installer. Take a look at the screenshot to see how much room I have used on it and you will see that 10gb gives plenty of room to move.

I don't think the programs are in /home/username, I thought they were in /usr and more specifically /usr/bin

My laptop has Ext3 if I use Ext4 on mt PC will there be any problems when I network them with file management between the two(one not seeing the other, permissions, etc.)?

---

### Post by k3lt01 on 2009-08-24
Sorry Chris, I can't answer that with any authority, I simply don't know although I would guess that it would be fine because ext4 was initially a development of ext3 so I would imagine they would be compatible.

---

### Post by mapes12 on 2009-08-24
> My laptop has Ext3 if I use Ext4 on mt PC will there be any problems when I network them with file management between the two(one not seeing the other, permissions, etc.)?This will not be a problem. ext* has no problems networking with ntfs machines either (provided the correct package is installed in Ubu). ext4 is also backward compatible with ext 2 & 3.

---

### Post by RATM_Owns on 2009-08-24
Programs are in /bin, /usr/bin, /sbin, /usr/sbin, and other directories (directories in your $PATH).
See: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

I use ext4 and have had no problem. It's also faster than ext3. It's just that ext3 is more stable (has been out longer) so people trust it more.

/ can be 10GB. Just make it big enough to hold enough data (maybe 15-20GB?).

---

### Post by kpkeerthi on 2009-08-24
I've had hard freezes using EXT4 with kernel 2.6.28. No problems with kernel 2.6.30.

---

### Post by dmizer on 2009-08-24
If you are unsure, it's best to err on the side of caution.

Regarding problems with ext4, you may want to have a look at this bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781)

Very very experienced people on this forum lost data as a result of that bug. If you're not prepared to deal with potential problems, then I highly suggest you stick with ext3.

That said, I haven't seen any reports of problems with ext4 recently, so things may have changed.

---

### Post by The Cog on 2009-08-24
No there won't be compatibility problems with file-sharing protocols such as NFS, SMB, SFTP, HTTP. These protocols all deal with file contents only, and don't worry about the local filesystem type that the server is using for storage. 

You would have issues if you dual-booted with another OS that can't read ext4 though, such as earlier versions of Linux, Windows etc. But I guess you will have figured that one out for yourself anyway.

---

### Post by chris1950 on 2009-08-24
> **The Cog said:**
> No there won't be compatibility problems with file-sharing protocols such as NFS, SMB, SFTP, HTTP. These protocols all deal with file contents only, and don't worry about the local filesystem type that the server is using for storage. 

You would have issues if you dual-booted with another OS that can't read ext4 though, such as earlier versions of Linux, Windows etc. But I guess you will have figured that one out for yourself anyway.

Your right thats why I am going to keep everything on the same OS since I want to make it a network. (Will have network questions later relating to being completely wireless after I install Ubuntu on the PC.)

Thanks Guys - Will go with Ext4 on the PC

---

### Post by davidsrsb on 2009-08-24
> **The Cog said:**
> 
You would have issues if you dual-booted with another OS that can't read ext4 though, such as earlier versions of Linux, Windows etc. But I guess you will have figured that one out for yourself anyway.

Windows cannot read ext3 either

Most of the actively maintained Linux rescue live cds now support ext4

---

### Post by barnex on 2009-08-24
This is just my experience, but I've had no problems with ext4 whatsover.

---

