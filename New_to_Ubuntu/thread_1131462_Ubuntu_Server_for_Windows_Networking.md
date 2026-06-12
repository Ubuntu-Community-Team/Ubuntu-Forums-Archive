---
title: "Ubuntu Server for Windows Networking"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by dmaxel on 2009-04-20
I know that there are a couple of places to find information on SAMBA, which I guess it the server app used to share folders for Windows machines to use. However, I am extremely confused about configuring it, as well as with domains. I don't know how to connect to a domain, as all Windows machines are on a workgroup.

Also, somewhat related, but then again not by much: How can I make it so that I can access folders shared by Windows machines in Ubuntu? I can go into Network --> Windows Network --> MY_WORKGROUP_HERE, but when I click on that it takes forever and then says it can't find some sort of list or something...:(

---

### Post by ppl on 2009-04-20
Hi, I am in the process of building a home server myself now, and from the reading I am did, I think NFS is a better solution than SMB, and that is what I am planning to do. It is supposed to be faster, and cross platform as well, ans simpler to configure. 

But even for SMB, if you want, I think you can try to automount them in you fstab configure file so whenever you start you computer they will mounted alreay, but that will slow down your computer start up.

---

