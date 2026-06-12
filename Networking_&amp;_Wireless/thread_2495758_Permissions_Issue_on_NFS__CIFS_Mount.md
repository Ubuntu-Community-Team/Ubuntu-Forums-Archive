---
title: "Permissions Issue on NFS / CIFS Mount"
date: 2024-02-29
forum: Networking &amp; Wireless
---

### Post by wallace4793 on 2024-02-29
Hi,

This is my first post on here, although ive been using linux a little while but at a very basic level with raspian mainly. I have recently installed Ubuntu 22.04 and installed Zoneminder to record my home CCTV. Ive got all the cameras working and want to mount my NAS as storage and can record to it using the methods below. Ive used the same NAS mounted lots before for various media storage etc so thought it would be straightforward. 

I have tried both NFS and CIFS as a mount method and both are somehow having issues with permissions. I will describe the behaviour of both but I assume there is a common issue :

1. NFS
Ive mounted manually with **"mount IP://share /mountpoint/directory"** and also tried at boot with /etc/fstab "[B]IP:/mnt/array/torrents/CCTV    /var/cache/zoneminder/events/ nfs  rw"

[/B]Both these methods allow me to see the remote drive in mounted folder, however i can not open any videos but bizarrely i can open **jpg files **in the same folder**. **Ive tried a few different mount options like rw and also changed recursive folder permissions to 777 at both the NAS and at the terminal in ubuntu for the shared folder. What I dont understand id that I can *navigate to the files,* I* can see them*, *rename them*, copy and move them even but not open them (except the .jpgs which opens fine). When I check the VLC log I see a "no such file or directory" when trying to open the video. ls -l shows the same permissions on the working jpg and failing mp4.

2. CIFS
I mount with sudo mount -t cifs -o username=user //IP/NAS-SMB /home/user/cifs

Again I can see the files, open the jpgs but not the mp4. Tried the same with permissions etc but no joy. The error in VLC this time though is "permission denied"

If I copy the file from the shared folder to the local ubuntu drive I can play it, so I know VLC can play the file **AND** on my windows installation the file play perfectly from the shared SMB/CIFS mount in situ.

What else can I try?

John

---

### Post by TheFu on 2024-02-29
VLC in ubuntu is a snap package.  Purge that from your system and load it from a non-snap version.  Snap packages have constraints meant to protect our systems from bad things. I have a different opinion about the true purpose of snaps that I'll keep to myself, but it isn't good.

BTW, don't mount storage under your HOME directory. There are many reasons this is a terrible idea. Rather, mount it somewhere else - I use /d/D1 .... D9 myself, but lots of people would mount it to /mnt/D1 or /media/D1.

Anyway, mount it, say under /media/D1/  then create a symbolic link from your HOME directory to /media/D1 to make accessing all the files there easier.

Please don't use CIFS unless you have no other choice. It doesn't fully integrate with Unix owner, group, permissions, ACLs, or xattrs.

BTW, your NFS mount command shouldn't have '//'.  
The fstab for NFS, looks like this:

```
1.2.3.4:/mnt/CCTV /d/D1   nfs     defaults    0    0
```
In theory, the last 2 fields aren't mandatory, but I've never seen a system without them.  The fstab manpage explains each field.

---

