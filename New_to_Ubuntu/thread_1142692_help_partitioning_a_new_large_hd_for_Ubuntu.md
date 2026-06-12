---
title: "help partitioning a new large hd for Ubuntu"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by BertP on 2009-04-29
I am considering purchasing a  relatively inexpensive 750 HD for  use with Ubuntu.

(for anyone interested 
[http://www.dealigg.com/story-Western-Digital-Caviar-Black-WD7501AALS-750GB-7200-RPM-32MB-Cache-SATA-3-0Gb-s-3-5-Hard-Drive](http://www.dealigg.com/story-Western-Digital-Caviar-Black-WD7501AALS-750GB-7200-RPM-32MB-Cache-SATA-3-0Gb-s-3-5-Hard-Drive))


1) any problems using Ubuntu with a drive this size?
2) Is there a way to prepare to **eventually** make this duel boot with windows vista, or must I have the Windows DVD at the time I initially install Ubuntu?
3) how should I partition it? How many partitions? Are there OS limitations on partition size? How much should space should be allocated for the OS's boot partitions for Ubuntu and Windows?

Thanks in advance!

---

### Post by piousp on 2009-04-29
1) There is no problem with those sizes. I have a 1TB External WD harddrive and it works like it should.
2) The "easy" way is to install vista first, then ubuntu.
3) Let me check for a guide for dual boot

---

### Post by Didius Falco on 2009-04-29
> **BertP said:**
> 

1) any problems using Ubuntu with a drive this size?
2) Is there a way to prepare to **eventually** make this dual boot with windows vista, or must I have the Windows DVD at the time I initially install Ubuntu?
3) how should I partition it? How many partitions? Are there OS limitations on partition size? How much should space should be allocated for the OS's boot partitions for Ubuntu and Windows?

Thanks in advance!

1. None at all. AAMOF, that's the drive I'm using.

2. It's easier to install Windows first, but if you install Windows afterwards, you'll just need to restore Grub to the Windows MBR after you've installed Windows, and add the Windows partition to your menu.lst and fstab files in UBuntu.

3. See, this is smart thinking. Make a partition at the very front of the drive where you'll install Windows. Format it to NTFS. Windows likes to be the first partition on the first drive. Personally, I always make a second NTFS partition to store all my own windows data and move My Documents, etc. to it.
 
For Ubuntu, you can make extended partition and add Logical drives inside it. I recommend that you make a separate /Home partition. This will make reinstalls, etc, much easier.

Personally, I use a 3rd partition that I call /Data, where I store all my own data. That way I can share that drive between various linux installs without worrying about configuration/software conflicts. This is strictly optional.

Lastly, you will need a Linux Swap partition. I have a 5 Gig one, but with 4 Gigs of ram it's never been used. The old rule of thumb is to make it 1.5 to 2x your RAM size, but depending on what you do (move editing, editing very large files, use Hibernation) it can be smaller.

As to partition sizes, I don't use Vista, so you'll have to check a more Vista-orientated site for recommended partition size.

I made my Ubuntu root partition 20 gigs, and even after installing tons of apps, I've got plenty of breathing space left. My /Home partition is 10 gigs, and again, tons of room left.

My /Data partition is 100 gigs, and it's doing fine, but I seem to add a few hundred megs to it a week.

With 750 gigs, you can afford to not go too small, and still have unallocated space left for future needs...

Ultimately, it's up to you to decide, after considering what you'll be doing with it.

I hope this helps...

---

### Post by BertP on 2009-04-29
> **piousp said:**
> 1) There is no problem with those sizes. I have a 1TB External WD harddrive and it works like it should.
2) The "easy" way is to install vista first, then ubuntu.
3) Let me check for a guide for dual boot

did you reformat it to something other than fat32?  or are do you just tar
your backups?
 
I find that if I try to copy directories to fat32, it breaks copying linked files and folders.  Plus there are more restrictions in file names on fat32

---

### Post by BertP on 2009-04-29
> **Didius Falco said:**
> 1. None at all. AAMOF, that's the drive I'm using.

2. It's easier to install Windows first, but if you install Windows afterwards, you'll just need to restore Grub to the Windows MBR after you've installed Windows, and add the Windows partition to your menu.lst and fstab files in UBuntu.

3. See, this is smart thinking. Make a partition at the very front of the drive where you'll install Windows. Format it to NTFS. Windows likes to be the first partition on the first drive. Personally, I always make a second NTFS partition to store all my own windows data and move My Documents, etc. to it.
 
For Ubuntu, you can make extended partition and add Logical drives inside it. I recommend that you make a separate /Home partition. This will make reinstalls, etc, much easier.

Personally, I use a 3rd partition that I call /Data, where I store all my own data. That way I can share that drive between various linux installs without worrying about configuration/software conflicts. This is strictly optional.

Lastly, you will need a Linux Swap partition. I have a 5 Gig one, but with 4 Gigs of ram it's never been used. The old rule of thumb is to make it 1.5 to 2x your RAM size, but depending on what you do (move editing, editing very large files, use Hibernation) it can be smaller.

As to partition sizes, I don't use Vista, so you'll have to check a more Vista-orientated site for recommended partition size.

I made my Ubuntu root partition 20 gigs, and even after installing tons of apps, I've got plenty of breathing space left. My /Home partition is 10 gigs, and again, tons of room left.

My /Data partition is 100 gigs, and it's doing fine, but I seem to add a few hundred megs to it a week.

With 750 gigs, you can afford to not go too small, and still have unallocated space left for future needs...

Ultimately, it's up to you to decide, after considering what you'll be doing with it.

I hope this helps...


yes thanks for the advice!

---

### Post by Didius Falco on 2009-04-29
Glad I could be of some help. If you would, please set this thread to solved.

You can do this by editing your first post. When the edit windows loads, click the "Go Advanced" button and just start typing "solved" at the back of the thread title (just above the body of the message) and it will offer you variations to add. Save the edit and you are all set.

This makes it easier for others looking for the same answers to find threads that can help them.

Thanks for taking the time to do that, and enjoy your new hard drive and Ubuntu setup...

---

