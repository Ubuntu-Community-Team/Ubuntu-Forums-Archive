---
title: "Permission problems mounting a raid array"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by cmsimike on 2008-12-28
I have 2x 1.5tb hard drives in a raid one on my system. This md is 2. I've been trying to mount it in my home directory but it fails to mount after running this command
```

sudo mount -o uid=mike,gid=mike -t ext3 /dev/md2 /home/mike/media

```
with this error:
mount: wrong fs type, bad option, bad superblock on /dev/md2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
the output from dmesg is:
sudo mount -t ext3 -o uid=1000,gid=1000 /dev/md2 /home/mike/media/

mike's userid is 1000. removing the problem options
```

sudo mount -t ext3 /dev/md2 /home/mike/media

```

mounts it, but of course i cannot create any files on the mounted device.

 I guess my question is, what am I doing wrong and how can I get this raid device mounted and usable by the mike account?

---

### Post by cmsimike on 2008-12-29
reading the man page for mount  > me

So I just found out that none of the options that I use for NTFS are applicable for ext3, which is why it is failing. Now I'm curious what the proper way to mount a hard drive so that a user (mike, for instance) has full access without having a root user create files and folders for him.

---

