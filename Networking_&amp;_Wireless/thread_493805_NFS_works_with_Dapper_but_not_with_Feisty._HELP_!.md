---
title: "NFS works with Dapper but not with Feisty. HELP !"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by wookieman on 2007-07-06
Hi

I can't get my Feisty machine to access my NFS shares without locking up, but my laptop running Dapper works fine.

I have a NAS Linkstation running as an NFS Server, which both my Dapper machine and another running Riscos can access just fine.

The setup on Dapper is as follows...

/etc/fstab

192.168.1.150:/mnt/hda/share /home/wookie/share nfs rw,noauto,user,async 0 0

/etc/hosts.allow

ALL 192.168.1.0/24

When I use the exact same setup on my Feisty machine I can mount the share and list the contents but as soon as I try to access a file the file manager (thunar,rox) locks up. If I change  Feisty's Fstab to ...

192.168.1.150:/mnt/hda/share /home/wookie/share nfs rsize=8192,wsize=8192,timeo=14,intr

as in the wiki guide it locks up as soon as I try to list the directory.

I can access the NAS using FTP and Telnet from all machines just fine. All other network stuff works fine. I'm on a wired ethernet setup, all UID's and GUID's are the same (1000) I'm frustrated and stumped can anyone help ? please ? :(

---

### Post by BillDozer on 2007-07-06
I remember having the same problems.

Do you have the nfs-common installed on your feisty system? As I recall this was the problem I had in the start (but I am not absolutely sure)...

---

### Post by wookieman on 2007-07-06
> **BillDozer said:**
> I remember having the same problems.

Do you have the nfs-common installed on your feisty system? As I recall this was the problem I had in the start (but I am not absolutely sure)...

Yeah I got nfs-common installed and I've also installed tcpd to create /etc/hosts.allow & deny files as they are missing in a standard Feisty install.

Thanks for the reply but still stumped :(

---

### Post by wookieman on 2007-07-15
I guess I'll have to "upgrade" from feisty to Dapper to get nfs working :(

---

