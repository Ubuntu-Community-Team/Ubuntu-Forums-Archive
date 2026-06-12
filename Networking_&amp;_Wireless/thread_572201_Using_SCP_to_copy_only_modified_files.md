---
title: "Using SCP to copy only modified files?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by elspiko on 2007-10-10
This is probably a stupid question, but is it possible to use scp to copy files that have been modifyed since the last time they were copied?? The cp equivalent would be:

```
cp -r -u /path/to/src/ /path/to dest
```

Failing that, does any one know how to mount remote shares over ssh, where the server is running openssh in Cygwin??

I've tried the following lines is fstab with no joy:

```
sshfs#user@ipaddress:/share/ /mnt/foo  fuse comment=sshfs,users,noauto,allow_other,reconnect,transform_symlinks 0 0 
```

And also

```
sshfs#user@ipaddress:/cygdrive/c/path/to/folder/ /mnt/bar  fuse comment=sshfs,users,noauto,allow_other,reconnect,transform_symlinks 0 0
```

There isn't an issue with ssh as i can connect to the server

Cheers

---

### Post by vanadium on 2007-10-10
rsync will copy modifications only, directly over the network (using the ssh protocol) if you wish.

[Edit]I am not sure this is entirely correct, or convenient for you. Indeed, according to the man pages, rsync needs to be installed on the remote machine as well for this to work.

---

