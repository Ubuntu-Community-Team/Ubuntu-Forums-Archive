---
title: "Basic Network Questions"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by DirtDawg on 2007-06-09
I have two computers in my home I would like to network. One is a red imac g3 running Xubuntu Dapper, the other a Dell desktop running Ubuntu Dapper. The Dell also dual-boots with XP. They are both connected to the internet via a wireless router, though both are connected by ethernet (not wireless. In other words, I'm using the wireless router as a basic router because it's the kind I have). 

I would like to share files easily between the two and possibly allow them both to print through the same printer (connected to the Dell), if it's not too complicated.

So I have been researching things, but I'm pretty confused. Do I need to use ssh, Samba, NFS, or is there an even simplier way I have not found yet? I understand Samba is good if you want to network with XP, but that is not terribly important to me, especially if it ups the complication factor.

I have absolutely not-a-shred of experience with networking and wondered if there's a guide for complete boobs like myself.

If not, maybe someone could get me started in the right direction.

Thanks.

---

### Post by empthollow on 2007-06-09
in my expierence nfs is by far the most solid.  i use it and highly recommend it. however, windows does not read it although microsoft does have a toolkit you can install.  i have not found where to download it or if it costs money.  you can share nfs via the system -> administration -> shared folders. you may have to install nfs-kernel-server via apt-get or synaptic before the option will show there.  to access this server from another computer you will need to use the mount command like this:
```
sudo mount 192.168.2.2:/path/to/share /place/to/mount
```
if you create a directory in media it will show on the desktop like partitions do.  good luck let me know if you have any other questions.

---

### Post by DirtDawg on 2007-06-10
> **empthollow said:**
> in my expierence nfs is by far the most solid.  i use it and highly recommend it. however, windows does not read it although microsoft does have a toolkit you can install.  i have not found where to download it or if it costs money.  you can share nfs via the system -> administration -> shared folders. you may have to install nfs-kernel-server via apt-get or synaptic before the option will show there.  to access this server from another computer you will need to use the mount command like this:
```
sudo mount 192.168.2.2:/path/to/share /place/to/mount
```
if you create a directory in media it will show on the desktop like partitions do.  good luck let me know if you have any other questions.

Thank you

---

### Post by DirtDawg on 2007-06-12
I finally found the time to give this a shot. After some initial trouble, I used [this guide]("https://help.ubuntu.com/community/SettingUpNFSHowTo") and some help from the IRC channel and eventually got things working. 

Thanks again.

---

### Post by empthollow on 2007-06-13
glad you got it working

---

