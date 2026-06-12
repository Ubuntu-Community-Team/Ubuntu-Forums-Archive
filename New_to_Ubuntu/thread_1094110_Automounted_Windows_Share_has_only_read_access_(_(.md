---
title: "Automounted Windows Share has only read access :( (AD Domain)"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Alexandre74 on 2009-03-12
Hello Everyone,

I've followed carefully the guide from the following post [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534), and the drive is nicely automounted when I start up my Ubuntu.

The problem that I have is that I am unable to anything in the folder without SUDOing into it, like deleting or creating a file for example. I've browsed most of my day for the forums trying to find a solution, but in vain.

Here is the line of my fstab where I mount the folder:

//server/share    /home/folder/MyDocs        cifs    credentials=/root/.smbcredentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Any solution would be greatly appreciated, as I cannot even change the ownership of the folder using SUDO CHOWN, it returns the message 'permission denied'

Regards, Alexandre

---

### Post by victorbrca on 2009-03-15
Hi there,


  Try this:

1- Find your UID with *id | awk '{ print $1 }'*:
```
$ id | awk '{ print $1 }'
uid=[COLOR="Red"]1000[/COLOR](victor)
```

2- Add *gid=1000,uid=1000* to your mount options in /etc/fstab
```
credentials=/root/.smbcredentials,iocharset=utf8,[COLOR="Red"]gid=1000,uid=1000[/COLOR],nounix,file_mode=0777,dir_mode=0777
```


Vic.

---

