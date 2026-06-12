---
title: "BUG Mounted SMB volume eventually times out"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by thevinn on 2007-01-27
When I mount my ReadyNAS (connected via Ethernet) it works great for a little while but eventually everything related to the volume starts timing out. Rebooting Ubuntu and re-mounting the volume fixes the problem temporarily, until it happens again (takes only several minutes until it hangs). I know its not a problem with the device because under Windows XP it never goes down (and rebooting Ubuntu fixes it).

I have this line in my fstab:

# ReadyNAS
//192.168.1.200/Data /media/nas  smbfs  _netdev,password="",ro,suid,dev,exec,noauto,nouser,async,dmask=770,fmask=770,gid=plugdev   0      0

To mount the drive I use
sudo mount /media/nas

---

