---
title: "Partioning sizes and types advice"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by janthonywj on 2009-02-21
As a newb to the Linux world, I still like to learn all that I can. 

I tried out Kubuntu Intrepid about a month ago with a small side partion from my Vista partion. I liked it so much I decided to start from scratch but while I'm at it, why not go ahead and try out Jaunty Jackalope. Installed it the first time using the full hard drive, but I guess I started messing around too much there with some emerald tweeks and such, then I tanked my X desktop completely. 

SO, now I'm reformatting completely again, and I need some advice on partioning sizes and types. I'm not exactly sure what types are supposed to be used for root and home

This is what I was thinking, advice would be nice. 

80GB HD with 1GB ram
/windows - 20000MB - fat32 - Primary
/        - 20000MB - ext4 - Primary
/swap    - 1000MB - swap area - Logical
/home    - 39000MB - ext4 - Logical

Also, if you want to throw in a few comments on whether I should actually try out this ext4, or stick to the ext3 or something else, I'm all ears. 

Is 20Gigs enought for root, I can remove /windows if need be. Thought I might need game space when Starcraft 2 comes out. I will need enough space to run Virtualbox with either XP or Vista.

---

### Post by janthonywj on 2009-02-21
No replies, so I went with 1.5GiB Swap, 15GiB ext4 root, remainder /home set in ext4. (Removed the /windows partition)

Didn't find anything that clearly lined out some good rules to go by, especially with respect to ext4 filesystems. I read somewhere that GRUB was compatible with ext4 now, so hopefully I won't need a /boot partition. 

I'd remove this thread since I got no replies, but don't know how.

---

