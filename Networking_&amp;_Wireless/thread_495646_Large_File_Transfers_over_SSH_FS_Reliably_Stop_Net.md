---
title: "Large File Transfers over SSH FS Reliably Stop Networking Interface"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by saserlite on 2007-07-08
I use SSHFS (using FUSE) to provide network shares between my Ubuntu Feisty Server box and my Ubuntu Feisty Client box.

Unfortunately, when performing large fie transfers after 10 to 20 seconds I lose all (wireless) network connectivity (I haven't tried the wired network interface).

The line in my fstab file for mounting the share is (sasser is my username, 192.168.1.11 is IP of the server, /media/srv1 is client mount location):

```
sshfs#sasser@192.168.1.11:/home/sasser /media/srv1 fuse comment=sshfs,users,noauto,uid=1000,allow_other,reconnect,transform_symlinks 0 0
```

Can anyone shed any light on this?

Other potentially useful information:

 - I was running ping across a time I lost network connectivity and at the point connectivity was lost I had the following output:
```
ping: sendmsg: No buffer space available
```

 - The wireless network indicator appears to still "work", in that it displays the strength of my wireless signal

 - I can still see my wireless network in the visible networks list, but other networks that I can normally see are not visible

 - Restarting networking via "/etc/init.d/networking restart" doesn't help.

I'm pretty much a noob wrt linux.

Thanks in advance.

---

