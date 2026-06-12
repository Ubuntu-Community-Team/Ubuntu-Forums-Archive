---
title: "Partitioning for triple boot, shared data and VM"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by paddyng on 2009-10-24
Bought a new Dell Vostro 1520 with Win XP, 4Gb RAM and 320Gb HD, after my Thinkpad died. I want to setup this laptop as a learning platform, with the aim of using as much Linux/open source as possible.

I think dual booting is impractical. I much prefer the virtualisation option. On this basis, I want to setup so that I can trial (1) XP with Linux VM and (2) Linux with XP VM, using VirtualBox.

Also I like to try a leaner/faster version of Ubuntu, eg. Xubuntu. As I'm not ready for that yet, I'll have an empty partition set aside for later.

I have read many forum threads and articles but still have many questions (see below). Any advice would be great.

**Proposed setup:**

The factory setup includes 39Mb FAT (recovery) and 298.05Gb NTFS (XP).

My plan is to re-partition as follows:

Primary 39Mb FAT (factory recovery - retain)
Primary 60Gb NTFS (XP - shrink existing)
Extended/logical 4Gb swap
Extended/logical 30Gb ext3 (Ubuntu 8.04 LTS)
Extended/logical 30Gb ext3 (placeholder for trialing other distros)
Primary 174Gb NTFS (sharing data between XP and Ubuntu)

**Questions:**

1. For sharing data, is NTFS reliable for read/write from both XP and Ubuntu? Is FAT32 a better option? I mainly don't want to corrupt any important Excel files. Or is sharing files between MS Office suite and OpenOffice not a good idea?

2. Does the shared data partition have to be primary?

3. If I have a shared data partition, can I not use /home at all? I assume I still need to have /home inside the Linux partitions.

4. Do the VirtualBox files get very large? Do they reside in the system or the data partition?

5. Are 60Gb and 30Gb too generous for XP and Ubuntu, respectively, for OS + programs + VM requirements?

Thanks

---

### Post by DezSP on 2009-10-24
1. NTFS is a much better option than FAT32, which is a very dated filesystem now. With the ntfs-3g package installed as standard on Ubuntu now, read/write operations to NTFS are no problem whatsoever.

2. There is no problem having it as a logical partition.

3. Ubuntu (well, all distros in fact) will allow you to specify seperate mount points for certain folders, the most useful offshoot being the ability to re-map /home to another partition. So you could have a smallish partition for Ubuntu (generally I find 10GB more than ample), and a larger, shared partition for /home. This also means you can use the /home on any other Linux distro you care to install, and as /home is where all your config files live, your profile will be the same accross both installs.

Read/write to Linux (ext3) partitions in Windows is possible using [Ext2 IFS](http://www.fs-driver.org/), which is quite stable. However it doesn't support partitions that have an "inode" larger than 128 bytes. I can't remember if 8.04 makes partitions with the correct inode size for this or not, if it doesn't you may have to tinker further to make the /home partition usable under Windows.

4. I'm not too savvy with virtual machines, but I think like with partitions, they have to be defined at a fixed size and can't be grown/shrunk after that (unless you get clever).

5. As I said above, Ubuntu will be quite happy on a 10 GB partition, it's all your personal data that'll stuff up space. A base XP install is around 7 GB, but you then need to consider other programs installed to the C drive, which can eat up a whole lot more space. Really depends what you'll be using XP for I guess.

---

### Post by paddyng on 2009-10-24
Thanks DezSP for your time and detailed response.

Having reflected on the recommendations, I think I will go with the following setup.

Primary 39Mb FAT (Dell recovery)
Primary 60Gb NTFS (Win XP)
Extended/logical 4Gb swap
Extended/logical 100Mb (/home)
Extended/logical 20Gb ext3 (Ubuntu 8.04LTS)
Extended/logical 20Gb ext3 (another distro)
Extended/logical 194Gb NTFS (sharing data between XP and Ubuntu)

I have trimmed down the Linux partitions but still on the high (safe) side. XP partition is kept large because I want to run Cubase and a few other bits and pieces.

I've added a /home partition for sharing Linux configs. I think it only needs to be small because I'm using a separate data partition.

Anyway trial and error is the best learning method. That's what the recovery partition is for. Wish me luck!

---

