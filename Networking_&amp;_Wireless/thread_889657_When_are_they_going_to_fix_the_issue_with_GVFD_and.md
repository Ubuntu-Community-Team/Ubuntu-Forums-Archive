---
title: "When are they going to fix the issue with GVFD and Samba  in Hardy?"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by c0rwyn on 2008-08-14
I just did a clean install of Hardy 8.04.1 along with all the updates.  Ever since going to 8.04 I've had issues with Samba not being able to see folders at the 'root' of a Windows network server.  But if you know the folder you are looking for then it works.  (i.e. smb://my-server shows 0 folders shared but if I go smb://my-server/stuff I can see all it's subfolders).

Apparently this is an issue with the GVFS ( Gnome Virtual File System ). 

When I Googled this issue I found a patch for a file called gvfsd-smb-browse. It works great, but every so often an update blows away the patch and I have to do it all over again.

Why don't they fix this in the main branch??  I've seen others having this issue and I can't understand why this is still broken.  Is this working for most folks? :confused:

---

