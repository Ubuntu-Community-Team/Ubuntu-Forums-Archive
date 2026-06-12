---
title: "USB Drive Connected to ASUS Router and SAMBA Shared. Unable to delete folder"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by ramsforums on 2015-07-18
Hi 

I Have a ASUS RT-AC66U router and I have connected USB Drive. Enabled SAMBA SHARE.


The drive is I think NTFS or FAT32 Formated. I am not sure. it is 3TB Drive.


I have mounted this drive on my Linux Mint (Xfce). I can create folders, copy files etc. even delete folders if I create.


If already a folder with ownership root, I am unable to delete this folder. When I want to delete some files unable to delete if it is owned by root.


I have used 


[PHP]sudo chown -R username:username ./folderName [/PHP]


command to change ownership. Nothing works.


See below Image.


[IMG]http://i.imgur.com/DkZZ2jG.png[/IMG]




I can not delete Discovery folder.
The video folder I have created. I can delete easily from any PC.






how do I solve this problem?


Thanks

---

### Post by TheFu on 2015-07-18
NTFS and FAT-whatever don't do permissions on Linux. I suspect you are mounting a CIFS share. If it was NFS, that would be different.

The only way to control those permissions is though the mount command used.  So, how are you mounting it and what are the options used?  BTW - FAT32 doesn't go over 2TB partitions and the disk needs to be GPT partitioned to use more than 2TB.

For local disks, something like this: ```
sudo mount -o uid=$UID,gid=$GID LABEL=$LABEL1 /mnt/$LABEL1
```

For CIFS disks, somthing like this: ```
sudo mount -t cifs -o rw,iocharset=utf8,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win-K.credentials //172.22.22.14/K /mnt/K
```

**Security:**
Please understand there have been many security issues uncovered with USB connected storage to routers. I wouldn't do it unless you don't mind accidentally sharing all those files on the internet. 
* [http://arstechnica.com/security/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/](http://arstechnica.com/security/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/)
* [http://securityaffairs.co/wordpress/21212/hacking/asus-routers-hack.html](http://securityaffairs.co/wordpress/21212/hacking/asus-routers-hack.html)

Not what you wanted to know, I'm certain.

---

### Post by ramsforums on 2015-07-18
Thank you [B]TheFu

[/B]Appreciate your help and feedback

At present I am mounting using the following command

> sudo mount.cifs '\\192.168.1.1\shared' routershare -o user=[myusername],workgroup=WORKGROUP,password=xxxxx

I also ran the following command

> 


ramdc@dc7700 ~ $ df
Filesystem 1K-blocks Used Available Use Mounted on
/dev/sda3 956977828 139826880 768516224 16 /
none 4 0 4 0 /sys/fs/cgroup
udev 1005812 12 1005800 1% /dev
tmpfs 203964 1312 202652 1% /run
none 5120 0 5120 0% /run/lock
none 1019820 76 1019744 1% /run/shm
none 102400 8 102392 1% /run/user
/dev/sda1 463844 46388 388989 11% /boot
\\192.168.1.1\shared 1953480700 428321664 1525159036 22% /home/ramdc/routershare




So which command I should use? Sorry  I am not expert in Linux. still long way to learn.

I have one 3TB drive. I want to share across my home. I am have enabled only Samba not cloud access. Any other way I can enhance security?

Once again thanks for the help.

---

### Post by TheFu on 2015-07-18
> **ramsforums said:**
> I have one 3TB drive. I want to share across my home. I am have enabled only Samba not cloud access. Any other way I can enhance security?

For security, don't use the USB port on the router for storage.  There really isn't any other choice. Pretty much every router that has this feature has a bug or 10 related to storage.

You should use the cifs mount example. BTW, putting the password in the command is extremely poor security. Use a credential file, like the example shows. Be certain to set the permissions on that file to be root:root 600.  It has 2 lines and the file just needs to be where ever the command points - best to put it under /etc somewhere for security too.
```
username=thefu
password=3424qewfaf24332wefasdafs7^%#@##$@##$@EW
```

---

