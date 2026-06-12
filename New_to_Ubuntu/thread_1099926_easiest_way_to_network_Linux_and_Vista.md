---
title: "easiest way to network Linux and Vista?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by janem on 2009-03-18
I have a Vista PC and a Linux laptop. I want to network them. I already have set up shared folders on Vista, as already networked from when laptop was also Vista.

What I have done so far... installed Smb4K. Can see my Vista shared folders but cannot mount/access them. Get error 

> mount error 112 = Host is down
Refer to the mount.cifs(8 ) manual page (e.g.man mount.cifs)

I tried to get it working by following this article [http://http://blogs.zdnet.com/Bott/?p=236]("http://http://blogs.zdnet.com/Bott/?p=236")

But when i tried to add a Samba username and password ```
sudo smbpasswd -a username
``` I get error > Failed to modify password entry for user username

Why does Linux hate me? I can't seem to get anything to work without these time consuming problems. 

Jane

---

### Post by MrWES on 2009-03-18
> **janem said:**
> I have a Vista PC and a Linux laptop. I want to network them. I already have set up shared folders on Vista, as already networked from when laptop was also Vista.

What I have done so far... installed Smb4K. Can see my Vista shared folders but cannot mount/access them. Get error 



I tried to get it working by following this article [http://http://blogs.zdnet.com/Bott/?p=236]("http://http://blogs.zdnet.com/Bott/?p=236")

But when i tried to add a Samba username and password ```
sudo smbpasswd -a username
``` I get error 

Why does Linux hate me? I can't seem to get anything to work without these time consuming problems. 

Jane

I'm sure you're not typing 'username' but enter an actual username on the system...right? :)

---

### Post by stchman on 2009-03-18
I have personally found that Ubuntu has a hard time connecting to Windows(SMB) shares.  Windows can easily connect to Samba shares.

I personally use NFS for my home network.  Unfortunately M$ does not support NFS.  You can Google NFS for Windows and there might be a few apps that can enable that.

I have read that Windows 2003 Server supports NFS.

---

