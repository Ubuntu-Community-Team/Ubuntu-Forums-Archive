---
title: "[SOLVED] windows and linux direct network file sharing HELP"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by gverrilla on 2008-04-03
Well,I've got 2 pcs : one with windows,one with ubuntu(latest version).
What I want to do is to transfer some files from my winPC to the lnxPC.
They are connected through a netwrk cable.
What I tried to do was to set ip addresses:
168.4.0.1 (win)
168.4.0.2 (linux)
subnetmask(both) : 255.255.255.0

I tried to configure samba as well.

Can somebody please help me ?
I dont want usernames or passwords for the network
cheers

---

### Post by warp99 on 2008-04-03
You don't need to install Samba, but you do need smbfs. This guide will show you how:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

It's not completely secure, but you posted stated that you weren't concerned about that.

---

### Post by Eiríkr on 2008-04-03
For sharing *from* Win *to* Lin, you don't need the full Samba package and all that configuration complexity.  All you should need are the smbclient and smbfs packages, which might come installed by default.  On your Linux machine, open your Nautilus file browser, click the location bar (hit Ctrl+L or click View -> Location Bar if it's hidden), and type:
```
smb://168.4.0.1
```

Let us know if you have any trouble past there.

Cheers,

Eiríkr

---

### Post by gverrilla on 2008-04-03
:O
thanks guys,it worked x)

---

### Post by Eiríkr on 2008-04-03
Glad to hear it!  :D  Please also mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page, then.  :)

Thanks,

Eiríkr

---

