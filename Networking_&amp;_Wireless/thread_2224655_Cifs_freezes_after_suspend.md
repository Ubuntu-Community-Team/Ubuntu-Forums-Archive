---
title: "Cifs freezes after suspend"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by Kljuka on 2014-05-17
I have a Windows share mounted through /etc/fstab:
```
//192.168...   /media/files   cifs   credentials=/root/.passwd,iocharset=utf8,file_mode=0777,dir_mode=0777   0   0
```

Sometimes (about 30% of time) when my laptop comes from suspend (sleep) I can't access cifs mounts. All programs that want to access it just freeze and wait indefinitely (become unresponsive). Example in bash:
```
cd /media
ls
(freezes and I can only close terminal by force)
```

I've read this is a common bug that when Ubuntu goes to suspend, it stops network before CIFS mount is unmounted which "locks" the mount. But those bugs are quite old (dating from 2008 to 2011) and I still can't find a solution.


What should I do?

Anyone has any suggestion how to debug this? It's really annoying and the only notable problem with Ubuntu Desktop.

I'm using Ubuntu 14.04 Desktop 64bit.

I still haven't solved this problem. I've tested it a bit further:
- **the problem gets reproducet 100% of time** (I just need to suspend laptop for about half an hour or more) ((maybe until session expires???))
- I've tested on **2 separate laptops and the problem occurs on both**
- I've tested with **Ubuntu 14.04 and Ubuntu 12.04 and the problem is happening on both systems**
- when cifs share freezes, I have to wait for a couple of minutes for CIFS share to start working again. Afterwards it just starts working. I did count the time once - it took 2 minutes to start working again

The problem is really annoying. Any help would be appreciated.

Still haven't solved the problem.
I've also tried with 3 different servers (runing Windows 7 and Ubuntu 14.04) and the freezing always occurs. It seems to me there is a Samba (CIFS) problem

This is the line in /var/log/syslog that might be of some help for debugging:
> Dec 27 02:17:55 <my-computer-name> kernel: [  217.576087] CIFS VFS: Server 192.168.1.5 has not responded in 120 seconds. Reconnecting...

---

