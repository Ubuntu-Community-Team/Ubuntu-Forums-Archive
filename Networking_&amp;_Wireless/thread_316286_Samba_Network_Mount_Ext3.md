---
title: "Samba Network Mount Ext3"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by FlashOmega on 2006-12-10
I know very little about samba ... and what im doing lol... I have one of my harddrives mounted as /home/myname/Media/ and it works fine... no problems.

So here is the deal. 
***fstab***
//192.168.1.100/Media  /home/user/Desktop/Data  smbfs  username=user, password=userpassword, default 0 0

This does not mount on boot as I think it should.

***mount***
sudo mount -t smbfs -o username=user,password=userpassword //192.168.1.100/Media /home/user/Desktop/Data

This returns an error basically telling me everything is wrong.   

wrong fs type, bad option, bad superblock on //192.168.1.100/Media,

       missing codepage or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so

***smb.conf***

[Media]
  comment = Group Folder
  path = /home/myname/Media/
  public = yes
  writable = no
  valid users = user
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup
available = yes
browsable = no

So thats my problem... no solution is too obvious for me.  It is my first time doing this.  OH and I had it working the other day with a different system that has since then been formatted (you'll laugh... we installed 32bit ubuntu on it ... its an AMD athlon64)

If there is anything else you would like to take a look at feel free to let me know.

Thanks

---

### Post by loeppel on 2006-12-18
Make sure the package **smbfs** are installed!
Try cifs instead of smbfs... - if the server version is very fresh, smbfs probably don't support it!

look what dmesg shows if it's something like that: 
> 
[17180702.248000] smbfs: mount_data version 1919251317 is not supported

you should use **cifs**

greets,
loeppel

---

### Post by Iowan on 2006-12-18
You've probably seen these - but just in case:
[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
[http://www.ubuntuforums.org/showthread.php?t=280473]("http://www.ubuntuforums.org/showthread.php?t=280473")

---

### Post by FlashOmega on 2006-12-18
...... I CANT believe it was that easy.... I feel so stupid for not installing samba on the client computer.... someone slap me lol.... thanks so much for your help.  Although I walk away a broken man... at least my network isnt broken.

---

