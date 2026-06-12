---
title: "Sharing second harddrive with windows networked computers"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by clazzics88 on 2016-09-14
Hi Guys, 

I have tried a few different methods and have not been able to figure out how to share my second hardrive with windows computers on my home network. 
I have successfully created a share from the primary hardrive, but no matter what I have tried I continue to get "Windows cannot access *filename* you do not have permission to access the file. contact your network administrator to request access " when trying to access the share from the windows computer. I have not tried to access it with a non windows computer as I have no others. 

I am using Ubuntu 16.04 LTS

I have tried creating the share like I did through nautilus, adjusting the permissions through the GUI interface as I did with the share on the primary harddrive but no joy. 

I have also, as per recommendations I have seen on other forums attempted to add the permissions to smb.conf 
(Linux2 being the drive label and Linuxshare being the folder name)  however no luck 

[Linuxshare]
   path = /media/mediapc/Linux2/Linuxshare
   browseable = yes
   guest ok = yes
   read only = no

I have ensured that the drive is auto mounted through the disk utility and even tried adding it into fstab directly 

fstab 
#device        mountpoint             fstype    options  dump   fsck
/dev/sdb1    /media/Linux2    ext4    defaults    0    0


I am using the most up to date version of nautilus and samba. 

I was thinking it might have something to do with how the actual permissions on the drive have been setup? 

Any suggestions would be greatly appreciated.

---

### Post by clazzics88 on 2016-09-14
Found a fix 

# Ubuntushare settings
[Ubuntushare]
   path = /media/mediapc/Linux2/Ubuntushare
   browseable = yes
   guest ok = yes
   read only = no
   create mask = 0755

added to the global section of smb.conf
re triggered the share through nautilus and then restarted the smbd service 
now it will let me log into with my windows computers via the samba user name and password

---

