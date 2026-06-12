---
title: "question with the back in time program"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-24
okay i have my home on a separate partition

so if i backup just "/" it should backup my home also correct or do i still have to specify "/home/ray" also ?/tks

---

### Post by mapes12 on 2010-07-24
I've not used Back In Time but you will find that if you have / and /home on there own partitions (very wise by the way) then unless you image your entire disk (time consuming) you will have to back them up separately.

Personally, I do my backups using 2 different methods. The reason for this is that for me / backup has to be comprehensive and /home only has to be incremental (i.e. only backing up new and modified files).

1. For / I image the partition with Partimage (ext3 file system. Doesn't support ext 4 = try Clonezilla)
2. For /home I use Grsync (in Synaptic)

Mark

---

### Post by rburkartjo on 2010-07-24
mapes tks for the info my luck on my new install for ubuntu 10.04 went to ext4 and ideas of a good backup program that will handle ext4/tks

---

### Post by mapes12 on 2010-07-25
> my luck on my new install for ubuntu 10.04 went to ext4 and ideas of a good backup program that will handle ext4/tksFor backing up / with ext4 some posts are recommending [FSarchiver]("http://www.fsarchiver.org/Main_Page").

I haven't tried it yet but plan to this week.

---

### Post by rburkartjo on 2010-07-25
tks mapes for all your help

---

