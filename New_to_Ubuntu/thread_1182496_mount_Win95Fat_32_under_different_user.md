---
title: "mount Win95/Fat 32 under different user"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by televisi on 2009-06-09
Hi All,
As far as I know to mount a system you do:

```
- mkdir abc
- chown USER:USER abc
- sudo mount -t vfat /dev/sda1/ abc

```

By doing the above commands, it will load all files inside /dev/sda1 to abc folder. Now the problem is, right after I mount it using sudo, **folder abc _by default _set the folder owner & group = root**.

Is there any other way to load that under different user / group so that only USER that have access to that folder?

I've tried:
```
sudo mount -o owner=USER -t vfat /dev/sda1 abc/
```
It gives an error message:
```
[COLOR="Red"]mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]

```

Thanks!

---

### Post by televisi on 2009-06-09
Ah... found the resolution,
apparently I need to mount it:
```

- get user UID and GID (from /etc/passwd?)
- sudo mount -o uid=100,gid=100 -t vfat /dev/sda1 abc/
 
```

Now the question is, what is **umask / dmask / fmask**? and what's the different with **uid and gid** as mentioned above?

---

