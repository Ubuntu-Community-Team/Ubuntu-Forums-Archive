---
title: "NFS mount hangs at getdents"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by Manas B on 2016-03-11
Hello,

I have an NFS mount mounted with the options:

```
nfsvers=3,rsize=8192,wsize=8192,timeo=80,intr
```

Most of the directories seem to work fine but occasionally there will be a directory that cannot be listed using ```
ls
``` or ```
find
```.

I did a search on the internet and found a suggestion to use ```
strace
``` with the commands to see which system call the command was failing on.

```
openat(AT_FDCWD, "user", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 5
fchdir(5)                               = 0
getdents(5,

```

These are the last few lines of the output from strace. The command does not proceed any further, it hangs at ```
getdents(5,
```. It has to be killed in order to regain use of the shell.

Does anyone have any suggestions as to what causes this and how it can be fixed?

Thanks,
Manas

I should add that running 'mount' shows:
```
rw,relatime,vers=3,rsize=8192,wsize=8192,namlen=255,hard,proto=tcp,timeo=80,retrans=2,sec=sys,mountaddr=192.168.2.2,mountvers=3,mountport=30000,mountproto=udp,local_lock=none,addr=192.168.2.2
```
and I am running:
```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid
```

---

