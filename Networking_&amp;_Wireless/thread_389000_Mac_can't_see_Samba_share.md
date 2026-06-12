---
title: "Mac can't see Samba share"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by DrQuincy on 2007-03-20
Hi there

I have set up a share on samba on a Kubuntu box.  I have a Macbook Pro on the same network; I need the Mac to be able to access the Samba share but it just can't see it.  I've tried smb://{IP address}/sharename/ and smb:/{computer name}/sharename/ but it doesn't see it.  Both those command bring the share up on my Kubuntu machine.

Am I missing something?

My samba.conf looks like this:

```
[Sharing]
comment = Shared Area
path = /home/tim/share
public = yes
writable = yes
create mask = 0777
directory mask = 0777
hosts allow = All
#hosts deny = All
guest ok = yes
browse list = yes
```

Also there is another Windows machine on the network - will the fact the global variable is set to

```
   workgroup = MSHOME
```

make a difference?  How can you make a non-Windows machine part of a workgroup?

Thanks.

Edit: I've realised the Mac and Linux box can't even ping each other - does this suggest some problem with the settings on the router?

---

