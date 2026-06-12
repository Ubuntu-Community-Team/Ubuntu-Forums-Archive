---
title: "Accessing windows PC from ubuntu using samba WITHOUT knowing the shared folder name"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by dinofizz on 2008-10-15
Hello. I'm trying to use my laptop (ubuntu) at work, where the majority of the PC's are Windows machines. I have successfully set up samba so my laptop can see the shared folders of my Windows PC's at home, as well as them seeing my ubuntu shared folder.

However it seems that one is only able to view the contents of a KNOWN shared folder.

For example, say there is a Windows PC ("1.2.3.4") with a shared folder "Shared". The only way to use samba to access this folder is by pointing to

```
smb://1.2.3.4/Shared
```

But what if I don't know the actual name of the shared folder? Pointing to just the IP shows 0 items in the network folder, or it just wont connect if I use the command line. There are many PCs at work with shared folders, and in Windows I would just put the IP address in explorer, which would then show me all shared folders.

Is something like this possible using ubuntu?

Using:
Ubuntu 8.04.1 (Hardy Heron)
linux kernel 2.6.24-19-generic

---

### Post by superprash2003 on 2008-10-15
try this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by dinofizz on 2008-10-15
Thanks for the link. It appears it does sometimes work with just the IP. I will test further but it may be that guest accounts with passwords are not available with just the IP, I think the shared folder name is required in such a case.

Nonetheless I can confirm that using smb://x.x.x.x/ will indeed display shared folders when viewing some computers.

---

