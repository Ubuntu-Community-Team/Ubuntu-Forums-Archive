---
title: "problem in partition  HD 1000 GB"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by magedsoft on 2010-11-25
hay all : 


i have a little qestion here : 

i have 1000 GB harddisk in installation process i found mount point >>>
/
/home
/temp
/boot
/usr
/usr local 


i need to make 
 50 giga fot root "to give more space for download deb package in apt folder"
 6 giga swap
 100 mega boot 
  260 giga home 
  and other disk 

i don't know what  i do with it 

tell me ..... and if i install another linux the date in home will be lost or not and the rest of hd what i can do , i need make partition with my name to add to places menu 

thank you

---

### Post by Mark Phelps on 2010-11-25
Everyone has their own preferences regarding partitioning, but you're making a lot of unnecessary work for yourself using this scheme. It looks like you're thinking along MS Windows terms ("temp") and trying to segregated different kinds of files into different partitions.

You can accomplish much the same with a simpler three-partition scheme:
1) /  (root)
2) /home
3) Linux-swap

As to the "/usr local", I would NOT use that because it has an embedded blank.

---

### Post by magedsoft on 2010-11-25
thank you [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399")
 are you advise me to make 3 partition only 
root 
home 
swap 


i need to know the size of them which you advise me ,"some friends told me that update and deb package download in apt folder and advise me to make root with large volume what you say " 


thank you again for respond me

---

### Post by linux-hack on 2010-11-25
You can make LVM partitions that way you can grow them when you need.

---

### Post by ajgreeny on 2010-11-25
Generally 10GB is considered sufficient for root; 50GB is huge, even if you install enormous numbers of packages, so I would reconsider that and perhaps reduce it.  If you really want to be certain you have enough room for cached packages go up to 15 or 20GB, but I can not believe you will ever need 50GB.  You can always get rid of un-needed archived .deb packages if necessary.

You suggested swap is also big, but OK and if you will want to hibernate the system, leave it at the 6GB mentioned.

The /home partition can be all the remaining space.  Should you have a dual boot system, however, you may wish to make a forth partition in the space noted above as /home, and format it as NTFS.  You can then make that partition mount at boot time in Ubuntu, and you will be able to read and write to it from Ubuntu as well as Windows.

If Wondows does not need to be accommodated, ignore this last part of my post.

---

