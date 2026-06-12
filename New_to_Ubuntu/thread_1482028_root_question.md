---
title: "root question"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Recon20k on 2010-05-13
I cant create or move files into any of the folders below (except temp).
Is this normal ? (I'm the only user on this computer.)

$ ls -l
total 40
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 bin
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 etc
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 games
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 include
drwxr-xr-x 4 root        root 4096 2010-05-10 13:57 lib
lrwxrwxrwx 1 root        root    9 2010-05-08 15:37 man -> share/man
drwxr-xr-x 3 root        root 4096 2010-05-12 16:31 matlab
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 sbin
drwxr-xr-x 9 root        root 4096 2010-05-10 13:57 share
drwxr-xr-x 2 root        root 4096 2010-04-29 13:17 src
drwxr-xr-x 5 bmosullivan root 4096 2010-05-11 13:47 temp

---

### Post by wojox on 2010-05-13
What command are you using?

---

### Post by Recon20k on 2010-05-13
I'm trying to install matlab and having fierce difficulty.

I was just wondering if it was normal that  all those files are root and i cant create or delete files in those folders if i dont chown

---

### Post by wojox on 2010-05-13
> **Recon20k said:**
> I was just wondering if it was normal that  all those files are root

Yeah that's normal. You just need root permission to do anything else with them.

---

### Post by 3rdalbum on 2010-05-13
Normal. Your ordinary user account can only modify its own home directory. This is for security - your security, the system's security and the security of other users of the same computer. Only root (the administrator) can modify and add to those directories.

You can open a root file browser. Hit Alt-F2:

```
gksudo nautilus
```

which temporarily gives you unlimited powers over the filesystem - be careful!

If you are running a command that needs root permission, put the word 'sudo' before it, for instance:

```
sudo cp preferences.conf /etc/preferences.conf
```

Another good idea is to install the "nautilus-gksu" package, which gives you an item in your right-click menu called "Open As Administrator". You can right-click a file or folder and Open As Administrator.

---

### Post by Recon20k on 2010-05-13
Thanks! v useful!

---

