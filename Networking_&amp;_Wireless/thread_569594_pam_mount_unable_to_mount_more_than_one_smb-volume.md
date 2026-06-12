---
title: "pam_mount: unable to mount more than one smb-volume"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by thoralf on 2007-10-07
hi there,

i'm in the middle of setting up a medium-sized network with a server that runs samba acting as a pdc, with ldap as authentification backend. the domain is running fine, the only thing left to do is integrating the linux clients (running feisty fawn).
more precisely, i want pam_ldap to do the user authentification und pam_mount to mount both the users home dir from the samba server and some network shares as well. mounting just one share during logon works as expected.
now, the odd thing is that trying to mount more than one share at logon causes pam_mount to hang. all volumes are indeed being mounted, with all the right permissions (i checked this on another console) - it just seems like pam_mount never returns from calling smbmount.

here are the relevant parts of /etc/security/pam_mount.conf:

```
mkmountpoint 1
lsof /usr/bin/lsof %(MNTPT)
fsck /sbin/fsck -p %(FSCKTARGET)
losetup /sbin/losetup -p0 "%(before=\"-e\" CIPHER)" "%(before=\"-k\" 
KEYBITS)" %(FSCKLOOP) %(VOLUME)
unlosetup /sbin/losetup -d %(FSCKLOOP)
cifsmount /bin/mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o 
"user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"
smbmount /usr/bin/smbmount //%(SERVER)/%(VOLUME) %(MNTPT) -o 
"username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"
ncpmount /usr/bin/ncpmount %(SERVER)/%(USER) %(MNTPT) -o 
"pass-fd=0,volume=%(VOLUME)%(before=\",\" OPTIONS)"
smbumount /usr/bin/smbumount %(MNTPT)
ncpumount /usr/bin/ncpumount %(MNTPT)
fusemount /sbin/mount.fuse %(VOLUME) %(MNTPT) "%(before=\"-o\" OPTIONS)"
fuseumount /usr/bin/fusermount -u %(MNTPT)
umount /bin/umount %(MNTPT)

# mount home dirs ...
volume * smbfs doc-server & /home/& - - -
# mount shares on server ...
volume * smbfs doc-server shares /mnt/doc-server - - -
```

commenting out either one of the volume ... lines causes pam_mount to mount the other share just fine. leaving both lines uncommented causes pam_mount to hang after printing out the following lines:

```
pam_mount(mount.c:851) mount errors (should be empty):
pam_mount(mount.c:100) pam_mount(misc.c:341) set_myuid(pre): real 
uid/gid=0:10001, effective uid/gid=0:10001
pam_mount(mount.c:100) pam_mount(misc.c:376) set_myuid(post): real 
uid/gid=0:10001, effective uid/gid=0:10001
```

i'm stuck at this point ... could it be that this behaviour gets triggered by a not-so-optimal pam stack?

thank you for your help,
thoralf.

---

### Post by thoralf on 2007-10-09
hi,

a quick follow-up: mounting these shares as cifs instead of smbfs does the trick.
I'd like to know why ...

with kind regards,
thoralf.

---

