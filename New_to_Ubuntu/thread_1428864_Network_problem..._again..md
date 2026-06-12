---
title: "Network problem... again."
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-13
I asked about this on the networking board too, but it doesn't seem like much is going on over there.

The other day, I got my connection to a Windows network working just fine.  Even the shared printer was up and running without a hitch.

Now I'm getting a "Unable to mount location.  Failed to retrieve share list from server"  error every time I try to open the workgroup.  The annoying part is that I can get right into the Windows computers if I put their IPs into Firefox like this "smb://192.168.0.100/".  I can see files, edit files, all that stuff. 

So the network is obvious working just perfectly, I just can't get Samba to browse it.

---

### Post by Overcast32 on 2010-03-13
> **Everynameistaken said:**
> I asked about this on the networking board too, but it doesn't seem like much is going on over there.

The other day, I got my connection to a Windows network working just fine.  Even the shared printer was up and running without a hitch.

Now I'm getting a "Unable to mount location.  Failed to retrieve share list from server"  error every time I try to open the workgroup.  The annoying part is that I can get right into the Windows computers if I put their IPs into Firefox like this "smb://192.168.0.100/".  I can see files, edit files, all that stuff. 

So the network is obvious working just perfectly, I just can't get Samba to browse it.

Windows firewall's not on is it?

If you want to keep it up, but allow local traffic, make sure to change the 'scope' to local subnet.

[http://ubuntuforums.org/showthread.php?t=1082148](http://ubuntuforums.org/showthread.php?t=1082148) found that too, if it's any help.

---

### Post by Everynameistaken on 2010-03-13
Nope, no firewall in Windows or in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)  I went through this guide and everything is the way they recommended it.

---

### Post by Everynameistaken on 2010-03-13
And somehow the printer test page I tried that gave me an error just printed about 15 minutes later.

It's taunting me, isn't it?

---

### Post by Everynameistaken on 2010-03-13
And... now it's working fine.  I still have no idea why.  Bleh.  

Oh well.  Thanks anyway.

---

