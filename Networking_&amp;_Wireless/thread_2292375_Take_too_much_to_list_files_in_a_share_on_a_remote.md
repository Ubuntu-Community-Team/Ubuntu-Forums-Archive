---
title: "Take too much to list files in a share on a remote site"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by damin2 on 2015-08-27
Hello,
Few days ago I installed Ubuntu 14.04 in a new computer in an enterprise which has 2 branch, it is taking about 5 minutes to list files in a shared folder in other site.
The enterprise has 2 branch, both branch has a internet conection and there is a point to point line between both branch
Both branch have a file server with centos and both file servers have a shared folder named public, which are accesed from any branch and in any OS
The problem I saw in this new PC with Ubuntu but I tested it in an older PC with Centos 6.3, it took less than in ubuntu but too much, but in any Windows it take about 2 seconds
To mount the shared folder permanently, after search in google I added the following lines to the /etc/fstab file:
//192.168.2.32/public /media/public2 cifs guest,uid=1000,iocharset=utf8  0  0
//192.168.1.32/public /media/public1 cifs guest,uid=1000,iocharset=utf8  0  0
The first one add the public folder of the remote site and the second add the public folder on the server of the same site
The problem doesn't happen when I try to access the the second (local site), just with the first one (remote site)
Each time I open Nautilus and access to public2 it took about 5 minutes to list the files
When I do a "ls" the files appear inmediately but doing a "ls -l" it take more than 1 mimute (less than Nautilus but more than Windows explorer)
I think it is a problem with the way I am mounting the shared folder but I am not sure
I discard Internet problem or a problem in the server because from Windows it works fine
I discard a Nautilus problem because also it happen with "ls -l"
I disabled preview in Nautilus, and tried to change the view (list or icons), nothing changed
 
Anyone know what is the problem?
Sorry about the lenght of the post, and sorry about my english
Thanks in advance.
Regards!

---

### Post by TheFu on 2015-08-27
CIFS is find for Windows clients, but for Unix-to-Unix file sharing, **NFS** is much better and faster.  NFS doesn't rely on broadcasting "here I am" across subnets, which some remote connections don't support. I think **mdns** addresses that issue, but don't know any more about it. We don't use CIFS outside the LAN and definitely NOT over a WAN link. Broadcasting like that can impact WAN link performance.

BTW - if the WAN link isn't private, there needs to be a point-to-point VPN for either NFS or CIFS.

If you just wont this to be really simple, you can use sshfs or sftp which works over an ssh connection. This is secure from anywhere in the world, provided ssh-keys are used, never passwords.

For NFS and SSH, all the systems need to be able to ping each other by name. That means having the /etc/hosts with all the systems specified or using DNS for all of them.

I didn't provide a good answer for CIFS sharing across WAN links. I simply don't know how to do that. Hopefully, someone else will come later with that.  OTOH, if you use any of the other option from above, then I'm positive the only performance issue will be the WAN bandwidth and any VPN used.

---

### Post by damin2 on 2015-08-27
Thanks TheFu,

I dont know too much about Linux, I forgot to mention that
I really was using CIFS because it was the only I found in Internet
I will look for NFS on google now
If anyone can assist me better
Regards

---

### Post by damin2 on 2015-08-27
Hi,

I left the /etc/fstab file without modify anything and I wrote in the terminal:
sudo mkdir /media/public3
sudo mount //192.168.2.32/public /media/public3
I opened Nautilus and went to /media/public3, it took more than with CIFS to list all files, also with "ls -l"
There are 4831 files and folders in there but it Windows it appear inmediatly

Thanks in advance
Regards

---

### Post by TheFu on 2015-08-27
Having more than 1K files in a directory will always cause performance issues.  Windows Exploder is probably caching the list on the first read and it doesn't have to look at all the ownership, group, permissions and ACLs, since it doesn't support them with CIFS mounts.  

NFS is designed as a network file system - NFS.  Some resources for learning Linux, starting to think like a Unix person and having system manuals which explain step-by-step how to accomplish things.  Most of these step-by-step guides are written for admin-to-admin instructions. We assume a basic knowledge of the shells, system layout, etc - basically the things that require about a year to learn with a mentor.  Any way - here's [my link to other links.]("http://blog.jdpfu.com/2014/12/28/learning-linux")  Hopefully the links at the top of the page help to explain "why" - which is often more important than "how."

Good luck to you.

BTW - if there are Windows clients, then you'll want to get CIFS working, so look for some guides on mDNS. The links in my link list might have some data about that. So might samba.org.

---

