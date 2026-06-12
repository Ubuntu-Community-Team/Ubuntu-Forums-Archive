---
title: "Unable to use long directory path with cifs in fstab"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by SoundFriend on 2007-09-13
Can anyone explain why I cannot mount a server share in fstab, when the server directory is more than one deep?

eg::

```
//servername/JLE   /mnt/JLE   cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```
works, as /JLE is one deep, but

```
//servername/Shared/Urls  /mnt/Urls   cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

doesn't mount.  This is a bit of a limitation!!

SF

---

### Post by kidders on 2007-09-14
Hi there,

You may be misunderstanding the Windows networking protocols. If you were to share a directory called /home/SoundFriend over NFS, the name of the share would be "/home/SoundFriend". If you do the same thing in the Windows world, the share would most likely just be called "SoundFriend", since including '/' symbols in share names is illegal.
[LIST]
[*]The depth of the shared directory in the server's filesystem is irrelevant ... unless you've found a bug in the software the server is running.
[*]You cannot mount *part* of a share. If the server's admin wanted to allow clients to independently mount /home/SoundFriend/Desktop, for example, he would have shared it independently.
[*]You can't mount something that's not a share.[/LIST]I'm not 100% sure why you would expect something called "//servername/Shared/Urls" to mount successfully, but hopefully something in this post helps you see why it couldn't work.

---

### Post by Zorael on 2007-09-14
You can mount //servername/share to a directory and then bind the subshare to another directory though, no?

```
//servername/share /opt/blaawp cifs defaults 0 0
/opt/blaawp/subshare /home/username/easyAccessToSubshare none bind 0 0
```

---

### Post by SoundFriend on 2007-09-19
Thanks both for your help.  I shall experiment.

SF

---

