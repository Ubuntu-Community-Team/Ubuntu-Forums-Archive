---
title: "Command line help"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by theozzlives on 2009-02-20
How do I access my samba shares from the command line? I made a directory called /media/music, now I want to mount my music there. I want it permanent also. I miss my autoexec.bat.

---

### Post by mcduck on 2009-02-20
You can either use the smbclient command for command-line access to the share, or mount the samba share and access it like any other mounted drive. To mount the share permanently you'd add it in /etc/fstab.

```
mount -t smbfs -o username=name,password=password //machinename/sharename /media/music
```

If I remember right the syntax for mounting samba shares in ftsab is like this:
```
//machinename/sharename /media/music smbfs username=name,password=password 0 0
```

---

### Post by theozzlives on 2009-02-20
Thanks, I'll try that next time I'm on my laptop. I don't know if I like having my password in plain text in my fstab.

---

### Post by theozzlives on 2009-02-20
I got this:
```
mount: wrong fs type, bad option, bad superblock on //www-server/music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by mcduck on 2009-02-20
It seems that smbfs isn't installed by default in Ubuntu. Install it first and then try the mount command again:

```
sudo apt-get install smbfs
```

What comes to having password in fstab, you can actually put the password in a text file only readable by root. See this thread for more detailed instructions: [http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")

---

### Post by theozzlives on 2009-02-20
> **mcduck said:**
> It seems that smbfs isn't installed by default in Ubuntu. Install it first and then try the mount command again:

```
sudo apt-get install smbfs
```

What comes to having password in fstab, you can actually put the password in a text file only readable by root. See this thread for more detailed instructions: [http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")

do  I install it on both  machines  or just one? I use  samba.

---

### Post by mcduck on 2009-02-21
You only need smbfs installed in the client machine.

---

### Post by theozzlives on 2009-02-21
Finally got it working, but I had to use the IP instead of the name. Thanks!

---

