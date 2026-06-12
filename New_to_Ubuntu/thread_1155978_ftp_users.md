---
title: "ftp users"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by akkad on 2009-05-11
hi, am using vsftpd where i created a user to be used for login, i set the user home directory to be the ftp directory, now how can i avoid this user to access other directories? some said i have to make it unprivileged user, how to do so?

---

### Post by Jimmyfj on 2009-05-11
You need to edit your /etc/vsftpd.conf file and in the line saying:

#chroot_local_user=YES

you remove the #-sign to the left in the line. This will make login directly to the users home-folder and set this as top (root) of his/hers tree.

Remember to restart vsftpd-server from the terminal by running the command:

```
/etc/init.d/vsftpd restart
```

---

### Post by akkad on 2009-05-11
> **Jimmyfj said:**
> You need to edit your /etc/vsftpd.conf file and in the line saying:

#chroot_local_user=YES

you remove the #-sign to the left in the line. This will make login directly to the users home-folder and set this as top (root) of his/hers tree.

Remember to restart vsftpd-server from the terminal by running the command:

```
/etc/init.d/vsftpd restart
```

thanks, worked.

---

