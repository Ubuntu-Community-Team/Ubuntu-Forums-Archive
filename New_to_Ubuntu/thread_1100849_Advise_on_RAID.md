---
title: "Advise on RAID"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-03-19
Good day,

I wanted some advise about my server in progres. First of all, I'm pretty new to linux. I've been running Ubuntu on my main PC for a couple of months now. And it's great, I love to learn new stuff everyday and enjoy linux very much.

Now I've got a (file)server in the making and I can't deside what to do with my harddrives, RAID, JBOD or nothing at all. I've got 4 discs of 1 TB and going to store mainly movies and mp3s and some other data. About 30-40% of that data is realy important to me. I already have backups of that data on DVD's and other HDD's which I keep stored away. The server will be doing: automated downloading, samba sharing, ftp and webserver. 

I've been busy the past couple of weeks expanding my knowledge about the different kinds of RAID types. I realy like the fact of having only one drive on my PC instead of 4 mountpoints. But JBOD seems to risky?
Basicly a maximum of two PC's will be simultaneuously streaming content of this server (DVD's and AVI's, maybe some HD). So I don't need alot of speed I'd guess. So RAID0 is out of the question. RAID1 seems a waste of space and money, since I already have decent backups. I thought about running 2 drives in RAID1 and the other for less important data singly. RAID10 whould be overkill I think but RAID5 looks promising..
But if a drive fails I don't want to spend alot of time recovering, this would be the case with RAID5. 
Or just make good backups and run all those puppies in JBOD? But this would mean if one drive failes I loose all the data on that particular drive. But will I be able to replace the drive and keep the rest of the data? And I want to be able to expand the array without alot of hussle.. 

You might be thinking, what the !@%(^ does that guy want from us, just do some research and make a deciscion. But I just wanted some advise and some recommendations in general.

Cheers,

---

### Post by kanikilu on 2009-03-19
For what it's worth, I use RAID5 at work. At home I'm using JBOD for now, but will eventually move to proper RAID as 1/1.5TB drive prices get lower.

---

### Post by cariboo on 2009-03-19
I would suggest Raid5 with a good backup strategy. This way one of the drives could go defective and you won't loose any data and the backups in case the data on the array gets corrupted.

With important data I have multiple backups on several different drives. In the case of photo's they are on the server, my main computer, my secondary computer as well as 4 different external drives.

Jim

---

### Post by Seq on 2009-03-19
At home I have a server with 2x 500GB drives in raid 1

I used mdadm (installed grub to both drives, a /boot partition is mirrored, and an lvm partition for everything else).

I also have good backups, but I really don't ever want to have to rely on them.

(My backups are a raid 1 synology NAS plus dumps onto a 30-tape library. So probably not a typical home scenario, but still...)

---

