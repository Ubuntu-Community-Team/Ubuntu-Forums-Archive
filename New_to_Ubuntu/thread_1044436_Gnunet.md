---
title: "Gnunet"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by iball8888 on 2009-01-19
How do i use gnunet once it is installed when i try runing it in terminal "gnunetd" the console gives me errors.

anthony@anthony-desktop:~$ gnunetd
Jan 19 13:08:35 ERROR: `fopen' failed on file `/var/log/gnunetd/gnunetd.log' at file.c:338 with error: Permission denied
Jan 19 13:08:35 ERROR: `access' failed on file `/var/run/gnunetd' at console.c:91 with error: Permission denied
Jan 19 13:08:35 FATAL: Cannot change user/group to `gnunet': Operation not permitted
anthony@anthony-desktop:~$ 

what do i do?

---

### Post by compiledkernel on 2009-01-19
User permsissions, as in the user in question does not have the proper permssions to run the appropriate application. 

Look here -- [https://gnunet.org/drupal/node/360](https://gnunet.org/drupal/node/360)

---

### Post by llamakc on 2009-01-19
Have you ran `gnunet-setup` like the instructions @ [http://gnunet.org/user_gnunet.php3?xlang=English](http://gnunet.org/user_gnunet.php3?xlang=English) say?

There's also a README @ /usr/share/doc/gnunet-client/README.gz

You can check it out with:

```

zcat /usr/share/doc/gnunet-client/README.gz | less

```

---

