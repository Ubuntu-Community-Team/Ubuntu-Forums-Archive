---
title: "Ubuntu as universal NAS storage"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by aldennis on 2011-04-09
Hi,

Its my first post in and was new in Ubuntu forums though I've been using Ubuntu since 8.10. Anyway my question relates to the following scenario:

Server1: Windows 2K3 Std 32bit (w/ 1 running ZCS 6.0.7 virtual machine) 
Server2: Windows 2K3 Std 32bit (w/ 3 running Windows 2K3 virtual machines)
Server3: Ubuntu Server 10.04 64bit

Server3 has 2x500GB Soft RAID1 and 2x1TB Soft RAID1 disks. The 500GB RAID is ext4 formatted and contains the / and swap paritition while the 1TB RAID has a single NTFS partition. I'll be installing samba in this server to allow sharing of the 1TB for my two Windows server. The 500GB would have ZCS 6.0.12 (Zimbra) installed.

Server1 and 2 would saved its Windows NT backup file in Server3:1TB disks and my new ZCS 6.0.12 from 500GB disk would also saved its backup to the 1TB disks. Now my problem is that the NTFS partition does not handle symlinks from my ZCS backup and so I decided to reformat the 1TB and use ext4 instead.

My question is, does the Windows NT backup from my Windows servers still can be saved to an ext4 disks without affecting its consistency? I need to make sure that I could still extract my Windows backup from the ext4 disk once I needed it.

I woud also save the following backup to that 1TB ext4 disk:
- MS SQL Databse Backup
- VMware Virtual Machine files and snapshot
- Acronis image (*.tib)

I hope you could clarify me on this issue.


Cheers :)

---

### Post by aldennis on 2011-04-11
Anyone who can answer?

---

### Post by CharlesA on 2011-04-11
Are you using Samba to share the drives from Server3 ?

If so, there will be no problem.

---

