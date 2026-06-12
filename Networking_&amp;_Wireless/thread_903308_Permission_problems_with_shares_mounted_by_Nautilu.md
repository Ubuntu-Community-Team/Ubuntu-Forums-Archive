---
title: "Permission problems with shares mounted by Nautilus/gvfs"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by W. Irving on 2008-08-28
I can't get shares to mount in a consistent manner when opening a network share in Nautilus. The share appears in "Places" and in ~/.gvfs/, and can be viewed, but the permissions vary:
```
elias@trotsky:~/.gvfs$ ls -lh
total 0
dr-x------ 1 elias elias 0 2008-08-28 11:16 documents on engels
drwx------ 1 elias elias 0 2008-08-25 22:56 trotsky-backup on engels

```

engels is my Windows XP machine, and the two shares are identical as far as the sharing preferences go. I have configured them with full permissions for the user engels/elias, which is my user on that computer, and it's evident the credentials I supply to engels are correct since it lets me mount and view the shares. What doesn't work is creating files inside "documents on engels". Writing to folders inside said share does work.

If I access the shares on engels from engels (using the same credentials as trotsky, my Ubuntu PC), I can create files in the documents share.

So why are some shares mounted write protected, while others aren't?

This doesn't work either:
```
elias@trotsky:~/.gvfs$ chmod 770 documents\ on\ engels/
chmod: changing permissions of `documents on engels/': Operation not supported
elias@trotsky:~/.gvfs$ sudo chmod 770 documents\ on\ engels/
chmod: cannot access `documents on engels/': Permission denied
```

---

