---
title: "[SOLVED] how to can I access a mounted network drive"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by cybergalvez on 2008-07-10
I have connected to a windows smb server via the "Places>Connect to Server" menu option and the drive appears on my desktop.  However I can not find it anywhere in my filesystem.  I have read that connecting this way uses the new GVFS, however nothing appears in my .gvfs folder.  So is there no way to get access to th drives via a terminal?  Thanks

Jose

---

### Post by df6269 on 2008-07-10
You only need to mount it from windows share folder to local folder.

---

### Post by cybergalvez on 2008-07-11
Ok so this is was I have been able to find out, when you login to a windows share using "Places>Connect to Network" you are using the gvfs, which should via fuse mount the recourse in your .gvfs folder.  However for that to happen correctly you need to be a member of the fuse group which I was not.  I added myself to the fuse group logged out and then back in and it is now working as expected!.  To make it simpler for myself I added a simplink from .gvfs to ~/Vfs.  Bottom line make sure you are a member of the fuse group
Jose

---

