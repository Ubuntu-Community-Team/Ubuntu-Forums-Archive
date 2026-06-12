---
title: "CIFS mount error(5): Input/output error-tried everything"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2014-09-28
For the life of me I can't figure out why I can't mount a CIFS share that's in my network. The CIFS share is a Western Digital MyBook World Edition 1TB with the Blue Rings (IP is 192.168.0.50, hostname is circle, share name is public). What's most weird is that it mounts just fine on 1 of my machines but not the other.  Both machines are running Xubuntu 14.04 and they are both running Samba Version: 2:4.1.6+dfsg-1ubuntu2.14.04.3 per aptitude show. Both machines have the same /etc/fstab entry which is
```
//192.168.0.50/public	/mnt/circle 	cifs	noauto,rw,noperm,iocharset=utf8,credentials=/etc/samba/.credentials,uid=1000,gid=1000	0	0
```
the credentials files on each machine are also the same as far as contents as well as owner and permissions. When I run the command "smbtree" and I enter my network password for the share it shows up like this
```
	\\CIRCLE         		Circle
		\\CIRCLE\IPC$           	IPC Service (Circle)
		\\CIRCLE\PUBLIC         	

```
I believe i have tried everything in my power to get this to mount on my gaming rig but it just will not mount, even using a manual mount command with verbose returns the following
```
sudo mount -t cifs --verbose -o username=daniel //192.168.0.50/public /mnt/circle
```
Password for daniel@//192.168.0.50/public: 
mount.cifs kernel mount options: ip=192.168.0.50,unc=\\192.168.0.50\public,user=daniel,pass=********
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I did realize that I had an entry in my /etc/hosts file which made circle hostname an incorrect IP but I have since removed that hosts entry and restarted my entire machine so I am still at a loss of how to troubleshoot this. The share mounts just fine on my other machine but not on this machine. Is there anything I haven't checked yet? I read a couple google search results and some are saying that Input/Output error are related to a bad filesystem on the share I am trying to mount but that doesn't explain why i'm able to mount it just fine on my other machine. I've unmounted and remounted it a ton of times on the other machine and it continues to work. I've also restarted the MyBook as well to no avail. 

What other suggestions do you have for me?

---

### Post by jpkidd on 2014-09-30
what kernel version do you have, 3.13.0-36-generic may require a patch to get cifs working again

---

### Post by dannyboy79 on 2014-09-30
3.13.0-37-generic is on the machine that I can't get the CIFS to mount and 3.13.0-35-generic is on the machine that it DOES mount on.

---

### Post by dannyboy79 on 2014-10-01
found the bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1373473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1373473)  waiting the fix to be pushed to trusty

UPDATE: to get around this you can either boot using the kernel that someone uploaded to that bug report OR just boot into a previous kernel like I did (since i don't trust random kernels posted to the web), I am using kernel 3.13.0-35-generic until this bug get's fixed

---

