---
title: "Security issue on cifs perm share mounts in fstab"
date: 2016-09-28
forum: Networking &amp; Wireless
---

### Post by mcapaldo on 2016-09-28
I installed the new Ubuntu 16.04 64 bit LTS and setup CIFS perm mount in  fstab shares as I have been using for some LTS releases now.  

1. I pulled old 120gb SSD and installed a new bigger one (250gb) and formated Ext4 and installed LTS 64 Bit Ubuntu.

2.  I put the old 120GB SSD running 14.042 LTS in an external usb 3.0 case  and copied all my data back over to new drive.  I got 168Mbps xfer rate  WooHoo!!!.

3. I copied my perm mounts in fstab from 14.04 fstab.  And removed usb ssd and rebooted.

4. I powered up the 12.04 LTS Ubuntu file server (yea have not upgraded that one yet).  Anyhoo.

5.  I switch back over to new 16.04 LTS and run SUDO MOUNT -A.  Then just  MOUNT.  And I can see the username=xxx and servername=xxx in plain text   

Fstab Entry 

//MYSERVERIP/music /mnt/music cifs  credentials=/home/MYHOMEDIR/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777  0 0

When I run MOUNT <enter> I get...

//MYSERVERIP/music  on /mnt/music type cifs  (rw,relatime,vers=1.0,cache=strict,username=AAA,domain=BBBBBBBBBB,uid=1000,forceuid,gid=1000,forcegid,addr=MYSERVERIP,unix,posixpaths,serverino,mapposix,acl,rsize=1048576,wsize=65536,actimeo=1)

AAA = my user id in plain text

BBBBBBBBBBB = my servername in plain text.

Is this a problem????? Please Advise ASAP!!!!!

---

### Post by cariboo on 2016-09-28
Duplicate post closed.

---

