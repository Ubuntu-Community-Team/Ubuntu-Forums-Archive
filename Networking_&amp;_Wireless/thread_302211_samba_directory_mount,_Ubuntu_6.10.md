---
title: "samba directory mount, Ubuntu 6.10"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by n_hendrick on 2006-11-18
Okay I have 2 computers connected to a dsl router, both have the connection but I'm having problems getting samba to work, it worked in kubuntu but now I'm using ubuntu. I have my fstab file edited as follows:

//nathan-desktop/nathan /home/nathan/smb_share smbfs auto,uid=1000,umash=000,user 0 0

and my smb.conf file as follows:

[nathan]
path = /home/nathan
available = yes
browsable = yes
public = yes
writable = no

When I try to open the folder for the share (on either pc) I get a password dialog box....but to my knowledge I can't understand why its asking for a password? the path attribute is the same in both smb.conf machines, could this be causing a opening error...just wondering. I know when I type "smbclient -L nathan-desktop -U%" I get a share list and the share is showing up...I can't understand why I can't mount the directory without a password. Am I trying to set it up wrong?

---

### Post by MetalMusicAddict on 2006-11-18
You should have the username and password in the fstab line. Heres mine:
```
//hack/Storage       /media/Storage          smbfs    username=****,password=****,dmask=777,fmask=777 0 0
```
So something like that should work. Just make sure you have the users from both computers added to each others user list. ie: User from PC-2 is added to PC-1 and vise versa.

---

### Post by n_hendrick on 2006-11-18
okay got a little farther...now its spitting out this error:


smbmnt must be installed suid root for direct user mounts (1000,1000)

smbmnt failed: 1

am I missing a package or something?

---

### Post by n_hendrick on 2006-11-18
finally....just had to create some links in /bin ...thanks everyone

---

### Post by SBFC on 2007-03-03
I'm getting this error as well. What links did you create?

---

