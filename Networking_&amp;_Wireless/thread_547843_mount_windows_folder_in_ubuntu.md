---
title: "mount windows folder in ubuntu"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Osamabingandhi on 2007-09-10
I am trying to mount my windows-machine-harddrive(sharefolder) onto my filesystem in ubuntu. Otherwise i cannot play my music in amorak or xmms....

The best solution i found is here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I've tried to do what i says but everytime it says something like: 13283: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name) or Could not resolve mount point. 

I open fstab with sudo gedit/etc/fstab and i add at the end: 

//WINDOWS/MEDIAE     /media/winshares        smbfs   auto,credentials=/etc/smbcredentials,workgroup=MSHOME,gid=smb,uid=ubuntu,fmask=770,dmask=770,rw       0       0

the windows computername is windows and have 198.168.0.116, i have tried both

I've tried /media/winshares, /home/ubuntu/Musik, nothing helpes.

as far as the password i have put into the: gksu gedit /etc/smbcredentials 
password="" cause i have no password...

Anyone with a solution?

---

### Post by Osamabingandhi on 2007-09-11
Sometimes it is very very nice to find the answer you are looking for. I started to look at the name of the drive i wanted to share in windows...I guess it was to easy so i didn't think of it.

When I shared my drive in windows the share name came up as MEDIAE (D:). To write that in linux is probably possible but not what you want to do. So I changed the name to MEDIAE....and there it was.

---

