---
title: "Problems with Samba, mix of RAIDed and non-RAIDed shares"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by ranjeetrao on 2007-05-25
Hi, I'm hoping for some help on a problem I'm having, I'll try and be and concise as I can about my situation, and I can give more info if needed.

I'm the administrator of a few linux computers in my research group. I'm discussing two computers right now:

Comp1 = newer Intel Core 2 Duo system, running 64-bit Feisty
Comp2 = older Intel P3 system, running 32-bit Dapper

I have samba running on both of machines, with identical smb.conf files, both computers with two shares on each, share1 and share2. Users want to be able to log into either computer and be able access files from the other computer. So, on Comp1 I mount both of the Comp2 shares, first using smbmount and once that worked, setting up the correct lines in fstab. It works fine; from Comp1 I can access the two Comp2 shares, with read/write permissions working. 
smbmount //Comp2/Share1 /mount_point -o credentials=pathtofile,gid=groupname,rw,fmask=660,dmask=770

When I do the exact same thing on Comp2 to mount the Comp1 shares, I can mount them, it shows the expected permissions, owners, and group, but if I try to make a file on that share(i.e. write to that share), I just get "permission denied".  I can access shares of Comp1 from a Windows PC (Win2k), and I can create folders and files and everything. The issue is only about trying to write files on //Comp1/Share1 when mounted on Comp2.  

While investigating this problem, I realized that I can't access //Comp1/Share2 from _any_ computer, Windows or PC.  //Comp1/Share1 is fine, but not Share2. The share definitions for Share1 and Share2 in smb.conf are identical, except for (of course) the actual share name and the mount point. The one difference between the two is that Share1 is a partition that is part of a software RAID (mirror), while Share2 is a partition that is on a separate hard drive, not RAIDed. And yes, that standalone drive is running without errors, I can read and write to it when I'm logged onto Comp1. 

So, in summary, 2 questions:
1) Has anyone had difficulty mounting a share of a 64-bit version of Ubuntu onto a 32-bit version of Ubuntu through smbfs?  I don't have problems moving in the other direction.
2) Has anyone ever had difficulty sharing a mix of RAIDed and non-RAIDed drives? 

Thanks for any help people can provide, or new avenues I can take my investigation. 

--Ranjeet

---

