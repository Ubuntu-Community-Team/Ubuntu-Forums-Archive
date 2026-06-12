---
title: "[SOLVED] can't mount network winxp shares with nautilus"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by splitlenz on 2008-10-14
I have 8.04 hardy
I have samba installed, smbfs installed, nautilus, pyneighborhood.

When i try to access and browse through my windows network using nautilus and pyneighborhood i can't get through far enough to use the files on the network.

When i use nautilus i get into /workgroup/, i don't see any computers or folders or files

When i use pyneighborhood, i see the /workgroup/computername/folders ,
but, i can't mount any of the folders to actually use them.

if i run the command 

```
sudo mount /192.168.0.140/winxpshare /media/lids1
```

This works. It mounts the folder to a cifs type. 

But darn it, i want to get the gui to work lol. this is some quirky behavior. Appreciate any help with this. Thanks.

---

### Post by superprash2003 on 2008-10-14
you could try accessing by typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine which is 192.168.0.140 here..
for reference : [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by splitlenz on 2008-10-15
hey, thanx

that works, but mounting is still an issue. any ideas?

---

### Post by superprash2003 on 2008-10-15
try this command sudo mount smb://x.x.x.x/sharedname /home/user/directory

---

