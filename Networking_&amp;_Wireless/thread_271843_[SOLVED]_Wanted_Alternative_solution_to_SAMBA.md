---
title: "[SOLVED] Wanted: Alternative solution to SAMBA"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2006-10-05
Hi, 

A few weeks ago I decided to ditch all Windows machines in my network and installed Ubuntu on each single PC. Up to then SAMBA was the best option for "file sharing" for obvious reasons. Since I am Linux only now I am thinking about options since SAMBA has got a fairly poor performance.

Could anybody point me to an alternative solution and possibly tell me where I find a good & complete howto? I really want to get rid of SAMBA as soon as possible.

Thanks, guys.

---

### Post by skymt on 2006-10-05
I use SSH for file transfer. It's a bit slower, but for smaller files (< 1 GB) it's fast enough. It doesn't even need any configuration. Just install sshd and use Nautilus/Konqueror/gFTP to connect.

A lot of people use NFS for n*x-only transfer. It's a lot faster because of the lack of encryption, but it means configuring and running an extra service. See the [wiki](https://help.ubuntu.com/community/SettingUpNFSHowTo) for instructions.

---

### Post by wieman01 on 2006-10-05
> **skymt said:**
> I use SSH for file transfer. It's a bit slower, but for smaller files (< 1 GB) it's fast enough. It doesn't even need any configuration. Just install sshd and use Nautilus/Konqueror/gFTP to connect.

A lot of people use NFS for n*x-only transfer. It's a lot faster because of the lack of encryption, but it means configuring and running an extra service. See the [wiki](https://help.ubuntu.com/community/SettingUpNFSHowTo) for instructions.
Excellent. Thank you.

---

### Post by Yolan on 2006-10-05
There is also a sshfs that you can use do mount directories over ssh if you want to go a more command line direction. Scp always works too :).

sudo apt-get install sshfs
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

---

### Post by wieman01 on 2006-10-05
> **Yolan said:**
> There is also a sshfs that you can use do mount directories over ssh if you want to go a more command line direction. Scp always works too :).

sudo apt-get install sshfs
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)
Sounds like a good option as well. But I'll go for **NFS** since my wireless network has strong encryption (AES) & all I need now is performance & a bit of convenience. I have SSH running but mainly to synchronize my personal files.

Thanks, guys.

---

