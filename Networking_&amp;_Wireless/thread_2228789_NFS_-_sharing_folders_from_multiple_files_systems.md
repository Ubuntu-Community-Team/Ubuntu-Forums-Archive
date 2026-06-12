---
title: "NFS - sharing folders from multiple files systems"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by neptune39 on 2014-06-09
Hi,

I think this is something simple I have missed. Any help would be much appreciated.

I am running Kubuntu 14.04. I would like to use NFS for some devices over samba (which I have working fine). The devices would be OSX and a raspberry pi running xvmc Raspmc.

I have the following line in my /etc/exports file:

/home/user/Public 192.168.0.0/24(rw,async,insecure,no_root_squash,no_subtree_check,no hide)


/home/user/Public is on the main filesystem and I can connect to this fine. In that folder are movies, tv and other folders that are mounted filesystems. Specifically other drives mounted at these folders. When I they and open these from the client (OSX for example) I cannot see the contents of these folders/filesystems (e.g. /home/user/Public/movies). After a little looking around I thought no hide would do the trick but to no avail. Any ideas?

Also my preference would be that any changes via NFS are as if the local user has made them. For example by samba I have force user = microserver (the local user) and any changes I make over samba are made under this user. I'd like a similar effect by NFS. Any hep on this would be delightful.

Thanks for your time.

---

