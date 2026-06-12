---
title: "ftp and ssh mounts in fstab"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by gregology on 2008-09-13
Hello all,
       I am having troubles mounting ftp and ssh in fstab. I can mount the following in terminal using.

for ssh
```
sshfs username@shell.host.tld:/home/username/files /home/username/files1
```

I've set up a key so I don't need to type in a password, it just works,

and for ftp
```
curlftpfs -o allow_other username:password@ftp.host.tld /home/username/files2
```

But I am having trouble converting this to fstab. I've tried

```
sshfs#username@shell.host.tld:/home/username/files /home/username/files1 fuse auto,fmask=0777,dmask=0777 0 0
```

and

```
curlftpfs#username:password@ftp.host.tld /home/username/files2 fuse allow_other,rw,user,auto 0 0
```

but neither work. I am using a wireless connection. I am using some network samba mounts that work perfectly

```
//192.168.0.1/FILES /home/username/files3 cifs auto,fmask=0777,dmask=0777 0 0
``` 

I've installed fuse, sshfs, and curlftpfs, and I have made sure the users are part of the fuse group.

Can anyone see what I'm doing wrong?

Thanks

---

