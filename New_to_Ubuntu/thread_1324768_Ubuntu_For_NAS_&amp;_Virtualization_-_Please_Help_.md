---
title: "Ubuntu For NAS &amp; Virtualization - Please Help I'm VERY GREEN With Linux"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by CCI on 2009-11-12
Hi All - I am a Windows lifer looking to make a switch to Linux after much frustrations in the MS world. 
 
Can someone please point me in the right direction for this requirement.
 
I want to setup linux as a storage server and also as a hypervisor. 
 
My clients have windows small business servers with 10 to 50 networked pc's running windows xp/vista/7. I am running Acronis to image and backup the SBS server and windows client pcs. 
 
Currently I am using hardware nas boxes for some clients and microsoft windows storage server for others, to store the backups. 
 
To offer a high availability system to my clients, I would like to setup a ubuntu server that doubles as a storage device for the backups and virtual machines and also as a hypervisor (esxi? or other free linux hypervisor?). In the event of a small business server failure, the current small business server virtual machine is started on the ubuntu box and business resumes. 
 
I want to remove the costs of windows storage server and that's why I'm researching this Ubuntu based solution.
 
What do you recommend I use for:
 
1. the operating system
2. the storage system (must be accesible from windows based systems)
3. the hypervisor 
 
Mike.

---

### Post by Paqman on 2009-11-14
I've got no experience of running virtualisation off a server, so i'll leave that one to someone else.

Setting up an Ubuntu file server is dead easy, just install the server version and pick that option during install. To serve to Windows clients you'll be using the SAMBA server, which is an open source implementation of the Windows SMB/CIFS network protocol.

Storage itself depends largely on your budget and redundancy/backup plan. You can create data redundancy through a RAID array, and there's about a million different types of that. An option i've heard others recommend is unRAID, which is a product based on Slackware Linux that provides an integrated RAID-like redundant file server. I have no idea whether it's realistic to add virtualisation to such a setup, especially as Slackware is a bit of a strange fruit, and uses very old packages.

---

