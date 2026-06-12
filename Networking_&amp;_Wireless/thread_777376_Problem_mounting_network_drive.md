---
title: "Problem mounting network drive"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by sixx on 2008-05-01
A coworker is trying to mount a network drive but continues to have problems. Here are the details.  Any insight?

Fresh install of 8.04

$ sudo mount -t cifs SHARELOCATION LOCALMOUNTPOINT -o uid=$USER,gid=users,workgroup=WORKGROUP,iocharset=utf8,file_mode=0777,dir_mode=0777
mount: wrong fs type, bad option, bad superblock on //dskcfile1pd.int.ad.xxxxxxxx.com/data3,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by john6six on 2008-05-01
Have you installed smbfs?

---

### Post by sixx on 2008-05-01
sudo aptitude install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for smbfs
No candidate version found for smbfs
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by john6six on 2008-05-01
Do a search in Synaptic, I could have the name wrong. But you will need the package installed to mount a cifs drive. I am not at home or near a Linux machine to verify the name.

---

