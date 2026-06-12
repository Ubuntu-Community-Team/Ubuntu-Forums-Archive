---
title: "Understanding mount points and partitions..."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by akelsall on 2009-02-02
So, I guess I don't understand mount points as well as I thought. I have 15 partitions total, I just resized a few. Now, I want to move things around a bit.

If you look at the attached screen shot, you'll see sda11 assigned to networking, and sda12 assigned to photography. These partitions currently have data in them. I thought I could just edit fstab and were it showed sda12 for photography, I could change that to sda14, and where it showed sda11 for networking, I could change that to sda12 (they were unmounted when I did this). After doing this, when I entered cd  /networking, I saw all my photos (as if I was typing cd /photography). So, I need some help here. 

My question is: How can a "re-assign" all my photography data to sda14, and then all my networking data to sda12? Will I have to end up moving all my files over to these partitions? I'm a bit confused right now, so "dumb it down" for me. :D

Thanks,

Andy

---

### Post by akelsall on 2009-02-02
After some thought, I think I might have this figured out. Since I created partitions to hold specific info (e.g. a /music to hold mp3 files, /photography to hold photos, etc), the data in those partitions stays with the partition, regardless if I try to re-assign it by editing 
/etc/fstab.

So what I did is use the command **sudo /sbin/vol_id sdaX** to retrieve the volume ID (what Linux seems to call the UUID) for sda14 (the new partition I defined to hold my photos). I then opened /etc/fstab added the line below. I used the existing info for sda12 (my existing partition for photos) as a template to build the line needed to mount sda14 automatically at startup. The only thing I had to change between the two was the volume ID (UUID), and of course, the partition number (using sda14):

# /dev/sda14
UUID=759c02e2-fdb4-46fe-a9c6-76163a086f69 /photos         ext3    relatime        0       2

After doing this, I entered **sudo mount -a** to remount everthing. Then, I copied all my data over from my old partition, verified it was copied correctly (using two Nautilus windows), then deleted the data from my old partition. Voila! Problem solved!


Andy

---

