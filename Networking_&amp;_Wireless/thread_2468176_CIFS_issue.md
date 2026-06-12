---
title: "CIFS issue"
date: 2021-10-20
forum: Networking &amp; Wireless
---

### Post by sebastianalemany22 on 2021-10-20
hi to everyone in the forum. First, sorry for my english. 

I have a problem whit mount command. I try to BackUp a Win Server whit smb protocol vers 2.10, on that server i have many shared folders and my idea is to use rsync to backup all of them. When I mount for the first time any folder, evererything work fine; but in less than 2 sec when I need to mount another folder don't work, same folder don't work neither, I receive a message error whit err code (2), that mean the folder does not exist, but the folder exist. I think, maybe, the problem come from keep alive or echo_interval.
My command

```
mount -t cifs //x.x.x.x/folder /home/user/backup -o vers=2.1,credentials=/home/user/.ca
```

I try it whit 

```
mount -t cifs //x.x.x.x/folder /home/user/backup -o vers=2.1,echo_interval=60,credentials=/home/user/.ca
```

but no.

thanks for any help.

---

