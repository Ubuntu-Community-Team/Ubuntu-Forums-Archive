---
title: "[SOLVED] Could not start the X server"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by rybaxs on 2008-12-16
Help!!!

before Ubuntu login screen comes up, an error display in blue screen.

```

Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when
the problem is corrected.

```


The problem is like this,
someone accidentally log as root in the server
then query a command "mv"

After I see the log files, i move back the move files to the original location. Ubuntu grub and other works well. but after the login screen,
that error occur. And everything are in READONLY FILE SYSTEM

---

### Post by PmDematagoda on 2008-12-16
When the person logged in as root, exactly what files did he move?

---

### Post by rybaxs on 2008-12-16
```


Dec 16 17:09:46 xxxxxx-desktop sudo:   myaccountname : TTY=pts/1 
; PWD=/var/www/my-site ; USER=root ; COMMAND=/bin/mv 
/mytool.log /attachments /bin /boot /cdrom /default-formatting.properties 
/dev /etc /home /initrd /initrd.img /initrd.img.old 
/lib /lost+found /media /mnt /ndb_pid4571_error.log /ndb_pid4602_error.log 
/ndb_pid4609_error.log /ndb_pid4698_error.log 
/ndb_pid4705_error.log /ndb_pid4839_error.log /opt /out.jpeg /proc /root 
/sbin /srv /svn /sys /tmp /usr /var /vmlinuz 
/vmlinuz.old /my-webapps-here /var/www/my-site/contentslist/


```

This was the last system log.

---

### Post by goma on 2008-12-16
> **rybaxs said:**
> ```


Dec 16 17:09:46 xxxxxx-desktop sudo:   myaccountname : TTY=pts/1 
; PWD=/var/www/my-site ; USER=root ; COMMAND=/bin/mv 
/mytool.log /attachments /bin /boot /cdrom /default-formatting.properties 
/dev /etc /home /initrd /initrd.img /initrd.img.old 
/lib /lost+found /media /mnt /ndb_pid4571_error.log /ndb_pid4602_error.log 
/ndb_pid4609_error.log /ndb_pid4698_error.log 
/ndb_pid4705_error.log /ndb_pid4839_error.log /opt /out.jpeg /proc /root 
/sbin /srv /svn /sys /tmp /usr /var /vmlinuz 
/vmlinuz.old /my-webapps-here /var/www/my-site/contentslist/


```

This was the last system log.

what's bothering me is HOW did someone managed to have a command like that? I think the user just wanted to do this:
```
mv my-webapps-here /var/www/my-site/
```

There could've been a mistake in the user's command that makes those system files moved to other dir.

---

### Post by rybaxs on 2008-12-16
Is there a way Ubuntu server will have a GUI? i was installing the Ubuntu serve 8.04.1 because the Ubuntu feisty is having lots of error as stated above..

---

### Post by rybaxs on 2008-12-16
[http://ubuntuforums.org/showthread.php?t=591664](http://ubuntuforums.org/showthread.php?t=591664)

read this one..

---

### Post by rybaxs on 2008-12-17
chown was the answer.. thanks

---

