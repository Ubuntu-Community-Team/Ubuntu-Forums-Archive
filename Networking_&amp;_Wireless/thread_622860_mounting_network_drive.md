---
title: "mounting network drive"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by henderbops on 2007-11-25
Hey, I'm relatively new to linux, I'm using the new Ubuntu 7.10 Gutsy Gibbon and I am trying to mount a network drive at my university to my home computer. After reading a short tutorial provided by my university I have tried this command.

sudo mount -t smbfs //hudson.dur.ac.uk/myusername /media/uni -o username=myusername,workgroup=mds

where hudson.dur.ac.uk is the server and myusername is the share and obviously myusername is my username (Note: Replacing instances of myusername with my actual username for university)

This brings forth the following error message (Note: Again replacing with my actual username)

mount: wrong fs type, bad option, bad superblock on //hudson/myusername,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've also tried it replacing mount -t smbfs with smbmount but this command is not recognized. Any help would be greatly appreciated. 

Thanks, Jonathon.

---

### Post by jetsam on 2007-11-25
Try 
```
sudo apt-get install smbfs
```
... and then re-try the mount command.  
This package need to be installed to mount samba shares.

---

