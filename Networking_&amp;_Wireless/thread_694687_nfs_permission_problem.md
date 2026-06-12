---
title: "nfs permission problem"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by dfodor on 2008-02-12
Hi!

I have a problem concerning NFS permissions. I set up an ubuntu server, nfs is running on it and there are two clients (ubuntu and debian). I mount the sared directory with autofs because the server is not running always but the problem is the same with mount command. It makes no difference.

I have two users whose home directories are shared with nfs. Lets say user1's id is 1000 and user2's id is 1001. User1 has access from Debian client, user2 from Ubuntu client. Now, everything works properly for user1 but user2 has 1000 id on Ubuntu client. I can mount (both with autofs and mount) the shared user2 home direcotry but I have no access to the files/directories. The permissions are set to 770 on the server and every user is part of users group (that is, if a file or directory is created, its owner is user1.users). There is a shared directory in user1's home directory and a symlink points to it from user2's home directory (its permission is 770) but user2 has no access to this directory too.

I tried to set user2's id to 1001 on the ubuntu machine but I got problems then with sudo and no access was gained when I changed the uid. And actually I would like to leave it default. 

I guess it is a question of ids somehow but I could not figure out how I could manage this problem. I would appreciate any kind of help.

Best wishes

Daniel

---

