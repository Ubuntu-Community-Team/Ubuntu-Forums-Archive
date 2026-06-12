---
title: "Help - Permanently map Windows Shares during boot up."
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by eha1990 on 2008-06-02
**Question #1:** How do you permanently mount/map to a Windows Share folder that is on another computer?

**Question #2:** How do you change the permissions on a mounted Windows Share so that you can have full rights on the share network folder?

I am attempting to figure out to permanently automatically mount/map to a Windows Share on another computer when I log into Ubuntu.  For example, I can manually mount the following share using:

smb://192.168.1.102/ShareFiles

But I'd like to know how to mount the Windows Share permanently at boot up.  How do you change the access permissions on a mounted Windows Share so that you will have read/write rights on the share folder?  I have not been able to figure this out.  I have attempted to edit the /etc/fstab, but I haven't been able to figure this out either.  Any assistance would be greatly appreciated.

---

### Post by mbaker824 on 2008-06-03
Check out this thread for a tutorial:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=288534](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=288534)


I usually have good luck googling any Linux subject I'm looking for - I found this thread by searching for "Ubuntu permanent SMB mount".

Mark

---

### Post by eha1990 on 2008-06-03
Mark - Thank you for the feedback.  I'll check out the post and let you know what happens.  Hopefully, it will do the trick for me and resolve this annoying problem.

eha1990

---

### Post by sbrandon on 2008-06-03
Good series of instructions, but will there be a "one click" way of doing this at some time in the future?  That and logging on to a Windows network easily will do alot to move Linux forward to office acceptance (obvious statement, but it is probably my main sticking point)

---

### Post by Iowan on 2008-06-03
Find a post by **dmizer** - in his signature is a link for mounting **cifs** shares - probably more up-to-date than the link in my signature for mounting **smbfs** shares.

---

