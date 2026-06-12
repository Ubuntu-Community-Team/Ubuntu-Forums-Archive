---
title: "Partitioning..."
date: 2010-03-01
forum: New to Ubuntu
---

### Post by ppk on 2010-03-01
I recently reinstalled my desktop. It used to be on vista and I decided to set it up to dual boot with kubuntu for office work since it has a large HD. I used the partitioning tool in vista to chop two bits off the main windows partition, so now it goes like that :

1- vista (300gb/ntfs)
2- shared (78gb/ntfs)
3- kubuntu (75gb/ext4)
4- vista recovery (8gb/ntfs)
5- linux swap (about 3gb)

Now my problem is that it turns out that I don't really like kubuntu. I wanted to try it out but now I'd much rather have ubuntu, which I've been using on my laptop for a while now. So I took my ubuntu live-cd and fired up the installation but I'm confused as to what I need to do to replace kubuntu without messing with anything else.

None of the basic options will do that, and I looked into the 'specify partitions manually' part but quite frankly I don't understand what some of these things will do. If I use the option to delete the kubuntu partition, will it turn into free space that I can install into? Or do I need to format it as ext4?

---

### Post by J V on 2010-03-01
you don't need to delete it or format, just tell it to install and mount as / at that partition and it will install without partitioning or screwing with the other partitions...

Note: Always a good idea to backup

---

### Post by ppk on 2010-03-01
Thanks!

Installation is running now... That's exactly what I needed to know.

---

