---
title: "Playing music from LAN"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by kroiz on 2007-10-05
On the LAN there is a windows machine with some mp3 files which I would like to play on my ubuntu 7.04.

When I double click one in the File Browser I get:
> 
Totem could not play 'smb://backup/mp3/R.E.M/R.E.M - What's The Frequency Kenneth.mp3'.


---

### Post by Lord Illidan on 2007-10-05
These bugs could be related to the problem :

[https://answers.launchpad.net/ubuntu/+question/7857](https://answers.launchpad.net/ubuntu/+question/7857)
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366)


This could be a fix : [http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

---

### Post by Spam Banjo on 2007-10-05
> **kroiz said:**
> On the LAN there is a windows machine with some mp3 files which I would like to play on my ubuntu 7.04.

When I double click one in the File Browser I get:

I always use pyNeighbourhood to mount windows shared folders. I find everything works then. Make sure you edit the pyNeighbourhood launcher shortcut to launch with root permissions

```
gksudo pyNeighbourhood
```

I play music over the LAN and also edit files over the network using wine apps which requires network fooders to be mounted.

---

### Post by kroiz on 2007-10-07
I installed pyNeighborhood and executed it with sudo but it wont let me mount the directory.
I get the message > Failed to mount
I could not find the log pyNeighborhood.log.

Should there be some Samba server installed there? cause I am able to browse the directory but I did not and I can not install there.

---

### Post by kroiz on 2007-10-07
> **Lord Illidan said:**
> These bugs could be related to the problem :

[https://answers.launchpad.net/ubuntu/+question/7857](https://answers.launchpad.net/ubuntu/+question/7857)
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366)


I don't understand how the problem was solved in those bugs. maybe time healed totem (-:

> **Lord Illidan said:**
> 
This could be a fix : [http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

I guess mounting would help but I have a laptop so I would have to mount only every time I get on that network ( I could not put it in fstab )

---

### Post by Spam Banjo on 2007-10-08
> **kroiz said:**
> I installed pyNeighborhood and executed it with sudo but it wont let me mount the directory.
I get the message 
I could not find the log pyNeighborhood.log.

Should there be some Samba server installed there? cause I am able to browse the directory but I did not and I can not install there.

I'm afraid I can not help you much here.

I know you do not need samba installed on the windows machine.

Did you install pyN from the repo's or from a download??

---

### Post by kroiz on 2007-10-08
> **Spam Banjo said:**
>  
Did you install pyN from the repo's or from a download??

the repo's. why?

---

### Post by Spam Banjo on 2007-10-08
> **kroiz said:**
> the repo's. why?

Not sure if it would make a difference but that's where I got it from. Just trying to nail what might be wrong.

---

### Post by kroiz on 2007-10-08
> **Spam Banjo said:**
> Not sure if it would make a difference but that's where I got it from. Just trying to nail what might be wrong.

Well Thanks, I guess I will live w/o it or just mount manually.
Maybe it will be fixed in gutsy, only ten days from now.

---

