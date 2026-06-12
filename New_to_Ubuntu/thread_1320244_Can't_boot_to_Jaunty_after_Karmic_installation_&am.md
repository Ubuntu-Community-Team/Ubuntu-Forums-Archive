---
title: "Can't boot to Jaunty after Karmic installation &amp; upgrade."
date: 2009-11-09
forum: New to Ubuntu
---

### Post by zedi on 2009-11-09
2 days ago I installed Karmic Koala, today I did upgrade with new GRUB {grub-install &#8594;  (GNU GRUB 1.97~beta4)} and now I can't boot to Jaunty. 
Quote from /var/log/fsck/checkfs: “  fsck.ext3: Unable to resolve 'UUID=3769aaaa-269d-4d78-aee4-7ba71e8f7fe6'   fsck died with exit status 8.” 
That's very funny because, there isn't such thing like partition 'UUID=3769aaaa-269d-4d78-aee4-7ba71e8f7fe6'.
Bellow, the result of command sudo blkid:
/dev/sda1: UUID="4AB5-62A3" TYPE="vfat" 
/dev/sda2: UUID="4AB5-674F" TYPE="vfat" 
/dev/sda3: UUID="8bd9d260-04ff-439f-a29d-be2bc7aab992" TYPE="ext3" 
/dev/sdb1: UUID="b49cd7d9-dcea-466b-b35d-51b2f0853d5d" TYPE="ext4" 
/dev/sdb2: UUID="c85b1e91-60e6-468a-b511-c9d9baa58183" TYPE="ext3" 
/dev/sdb5: UUID="120babd8-22b5-4b9a-97b4-d6a11706b838" TYPE="ext3" 
/dev/sdb6: UUID="f13168b3-cb86-469f-ae3d-c811a8c9b57f" TYPE="swap" 
/dev/sdb7: LABEL="WinPage" UUID="AE23-C13C" TYPE="vfat"
My partitions are &#8594;  /dev/sdb1: Karmic, /dev/sdb2: Jaunty, /dev/sdb5: /home. The first disk - /dev/sda is for Winblows & store.
Normal booting gives just black screen with flashing cursor -, in Recovery mode – the message like above.
It's my second attempt with Karmic, the first crashed when I removed Network-manager and setup static IP address (unsuccessfully). So now I'm not touching static IP until I'll have working Jaunty. But to get there I need HELP! Please!

Zedi
PS,
      I'm not sure it's GRUB related as that was my first attempt to boot Jaunty after fresh installation over cactus Karmic ( which didn't stuff up Jaunty, BTW)

---

### Post by zedi on 2009-11-10
Ahoy! Is anybody out there?  
I need desperately somebody who knows why fsck gives me weird message and what I can do about. 
I really would like to be able to boot to my Jaunty, but if is not possible, I would like to know that so I can use this partition for another Linux distribution. 
P L E A S E !!!

Zedi

---

### Post by Mariane on 2009-11-10
These things: 3769aaaa-269d-4d78-aee4-7ba71e8f7fe6
are hexadecimal addresses. Not the name of the partition. 

What happens when you boot from the CD? 

Be careful with fsck, it stands for "f*** disk". (Only joking about the name but not joking that it is dangerous)

Mariane

---

