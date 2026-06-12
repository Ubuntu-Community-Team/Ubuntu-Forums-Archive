---
title: "issues with NFS"
date: 2021-02-18
forum: Networking &amp; Wireless
---

### Post by mstjohn1974 on 2021-02-18
I am working on setting up a NFS Server and Client for a project and it used to work just like it but it is no longer and I dont understand what am I missing. Here is what I did:
```
sudo apt update
sudo apt upgrade
sudo apt install nfs-kernel-server
sudo mkdir /var/nfs/myshare -p
sudo chown nobody:nogroup /var/nfs -R
sudo vim /etc/exports
   /var/nfs/myshare *(rw,sync,no_subtree_check)
sudo systemctr restart nfs-kernel-server
sudo exportfs -a
```

and on the client side:
```
sudo apt update
sudo apt upgrade
sudo apt install nfs-common
mkdir /home/username/nfs-share
sudo mount server_ip_address:/var/nfs/myshare /home/username/nfs-share
```
so far all good but when I try to run: "touch /home/username/nfs-share/test.txt " then I get: "touch: cannot touch 'home/username/nfs-share/test.txt': Permission Denied"

Client Side: nfs mounted folder drwnr-xr-x 2 nobody nogroup
Server Side: nfs share folder myshare: drwxr-xr-x nobody nogroup

What am I missing?

---

### Post by TheFu on 2021-02-18
nobody?  Doubt that maps to userid on the client. Only nobody can create a new file 

The uid and gid on the client and server should probably match based on the users involved. It is about the numbers, not the names.
'id' is the command to check the numbers.

---

### Post by SeijiSensei on 2021-02-19
If the mount point is owned by nobody, ordinary users cannot write to it. Try exporting a directory you own on the server like /home/username. Can you mount that?

NFSv4 has some additional features that sometimes require using the "fsid" parameter in the entry in /etc/exports. I don't know if applies when only one filesystem is exported, but you might try adding "fsid=1" to the option list in /etc/exports.

I usually avoid these problems by using no_root_squash on the server and mounting the share to a root-owned directory on the client. Then the usual permissions apply as long as the user IDs and usernames are the same on both the server and client.

---

