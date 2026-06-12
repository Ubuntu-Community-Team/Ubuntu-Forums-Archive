---
title: "smbmount without password"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2013-12-19
Hello, I created at script to mount music from my network drive. It works great, here is the script:

```
#!/bin/bash

gksudo smbmount //192.168.1.250/Music /mnt/comp/Music 

nautilus /mnt/comp/Music
```

I'd like for it to not request a password.  I've tried adding the file /etc/sudoer.d/smbmount and it contains:

```
david ALL = (root) NOPASSWD: /sbin/mount.smbfs
```

If i run the script from Nautilus it does nothing.  If I run it from terminal it just hangs.

Any ideas?

---

### Post by tfrue on 2013-12-20
Are you worried about security? If not, when you defined the share in the 'smb.conf' file, add 'guest ok = true' and possibly take off the 'valid users = (user) and restart the smbd and nmbd service.

---

### Post by wewantutopia on 2013-12-20
Thanks for the reply.  My smb.conf files are set up properly and working great.

I'm tring to setup the guest computer so when I do: gksudo smbmount...  it dosen't prompt me for a password.  It needs a root password for sudo that I'm trying to eliminate.

Anything I can add to sudoers??

Thanks.

---

### Post by SeijiSensei on 2013-12-20
Follow the instructions in [this document](https://wiki.ubuntu.com/MountWindowsSharesPermanently) to create an entry in /etc/fstab that will mount the share at boot.

---

### Post by wewantutopia on 2013-12-20
Thanks for the reply.  I don't need it mounted at boot.  It is a laptop so I'm not always in the same network as the share.  I have that script setup to mount it on demand.

---

### Post by tfrue on 2013-12-20
Here is the man page, which I'm sure you have read lol, but as I skimmed through, it said that it's deprecated and no longer used. So you might want to give that a read.
[http://linux.die.net/man/8/smbmount](http://linux.die.net/man/8/smbmount)

---

### Post by tfrue on 2013-12-20
When I say "it said" I meant smbmount.

---

### Post by steeldriver on 2013-12-20
... how about using autofs?

I'm an ignoramus when it comes to SAMBA, but on my laptop I have set up autofs to mount NFS shares off my NAS 'on demand' (i.e. if I'm on my home network, then they mount automatically when I try to access them - no script required). I believe the same should be possible with SMB/CIFS.

---

