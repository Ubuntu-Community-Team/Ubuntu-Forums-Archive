---
title: "fstab issue"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Matt26 on 2009-12-06
i'm trying to mount an NTFS share on a remote Windows PC using ```
sudo mount -a
``` but i getthe following error message:

> mount: wrong fs type, bad option, bad superblock on //192.168.0.102/Share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

here's the line in the fstab file:
```
//192.168.0.102/Music /home/user/path/to/mount cifs  iocharset=utf8,credentials=/home/user/.smbcredentials,uid=1000 0 0
```

if i replace the credentials parameter in the fstab entry with the username and password the mount works.

the .smbcredentials file is owned by root and has been set with read and write access for root.

any ideas?

---

### Post by andrewc6l on 2009-12-07
Do you have CIFS support installed? If you run:
```
which mount.cifs
```

do you see /sbin/mount.cifs? If not, you're probably need to install smbfs using the package manager.

If you do have /sbin/mount.cifs, what do you see when you run:
```
sudo mount -tcifs //192.168.0.102/Music -oiocharset=utf8,credentials=/home/user/.smbcredentials,uid=1000 /home/user/path/to/mount 
```

Also, I wonder if credentials needs to stand alone (or at least be last) in the options list - maybe mount is looking for the file .smbcredentials,uuid=1000 instead of .smbcredentials?

Next, ```
dmesg | tail
``` might show you something interesting.

Finally, you might want to put .smbcredentials somewhere other than in /home/user (which is possibly world or group-readable). I make a subdirectory of /etc/samba called /etc/samba/credentials/ and put the files in there. You can chmod it to be 500 and owned by root so other people can't read the credentials.

---

### Post by Matt26 on 2009-12-07
> **andrewc6l said:**
> Do you have CIFS support installed? If you run:
```
which mount.cifs
```

do you see /sbin/mount.cifs? If not, you're probably need to install smbfs using the package manager.

If you do have /sbin/mount.cifs, what do you see when you run:
```
sudo mount -tcifs //192.168.0.102/Music -oiocharset=utf8,credentials=/home/user/.smbcredentials,uid=1000 /home/user/path/to/mount 
```

Also, I wonder if credentials needs to stand alone (or at least be last) in the options list - maybe mount is looking for the file .smbcredentials,uuid=1000 instead of .smbcredentials?

Next, ```
dmesg | tail
``` might show you something interesting.

Finally, you might want to put .smbcredentials somewhere other than in /home/user (which is possibly world or group-readable). I make a subdirectory of /etc/samba called /etc/samba/credentials/ and put the files in there. You can chmod it to be 500 and owned by root so other people can't read the credentials.

interesting, the 'which mount.cifs' command didn't return anything- how do i install smbfs using the package manager?

i've tried searching for the package under Ubuntu Software Center but it didn't show up there.

---

### Post by andrewc6l on 2009-12-09
Not sure how in the package manager, but from the command line you can:
```

sudo aptitude install smbfs

```

(unless it's a package that doesn't exist in 9.10 anymore - have to check when I'm near a 9.10 machine).

edit: Just checked - you will need to install smbfs on 9.10. If you want to use the GUI package manager, just search for smbfs and install that package :-)

---

### Post by bodhi.zazen on 2009-12-09
That credentials file should work, make sure the syntax is correct in the credentials file.

cifs should be sufficient.

---

### Post by TxRx on 2009-12-15
Perfect thread for me, couldn't figure out what I had done wrong on my fresh install. (from a previous clunky 9.04 nbr install). ;-)

Many thanks!

---

