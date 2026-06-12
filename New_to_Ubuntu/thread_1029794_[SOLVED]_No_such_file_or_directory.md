---
title: "[SOLVED] No such file or directory"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2009-01-03
Hello,

I have set up 2 working Kubuntu 8.04 test web servers, 1 Xubuntu 8.04 test server on my laptop.  I have started setting up a 3rd Kubuntu system trying to set it up just like the other 3.  I installed the 8.04 server CD first and then installed Kubuntu 3 desktop copied all my web development files over from the other working systems.  When I try to run localhost I get the not found error, from command line I try to change to the directory my web files are stored and get bash: cd: /home/james/adweb/ no such file or directory.  I can open Dolphin file manager the directories and all my web files are there under the /home/james/adweb folder.  I can cd /home and go to that directory but in that directory cd /james/ gives the same error no such file or directory.  

Anyone got any ideas what is going on????  All pointers and suggestions on things to try will be appreciated.

James in GA, USA

---

### Post by taurus on 2009-01-03
What's the output of this command from a terminal?

```
ls -la /home/james
```

---

### Post by JKHinton CPBD on 2009-01-03
Hey taurus, thanks for the response.

Here's what I got.

> ls -la /home/james
total 13408
drwxr-xr-x 18 james james     4096 2009-01-01 15:13 .
drwxr-xr-x  3 root  root      4096 2008-12-28 20:55 ..
-rw-r--r--  1 james james    10858 2008-12-31 21:01 apache2.conf
-rw-r--r--  1 james james    10587 2008-12-31 20:58 apache2org.conf
-rw-------  1 james james      821 2008-12-31 21:52 .bash_history
-rw-r--r--  1 james james      220 2008-12-28 19:39 .bash_logout
-rw-r--r--  1 james james     2940 2008-12-28 19:39 .bashrc
drwxr-xr-x  2 james james     4096 2008-12-29 05:38 .config
-rw-r--r--  1 james james       61 2008-12-31 20:34 .DCOPserver_linuxlocalhost__0
lrwxrwxrwx  1 james james       41 2008-12-31 20:34 .DCOPserver_linuxlocalhost_:0 -> /home/james/.DCOPserver_linuxlocalhost__0
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Desktop
-rw-------  1 james james       26 2008-12-29 05:37 .dmrc
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Documents
-rw-r--r--  1 james james    25507 2008-12-29 20:18 .gtk_qt_engine_rc
-rw-r--r--  1 james james      285 2008-12-29 05:37 .gtkrc-2.0-kde
-rw-------  1 james james      205 2008-12-31 20:34 .ICEauthority
drwxr-xr-x  3 james james     4096 2008-12-31 21:51 james
drwxr-xr-x  3 james james     4096 2009-01-01 15:13 jkh
drwx------  5 james james     4096 2008-12-29 05:37 .kde
drwx------  3 james james     4096 2008-12-29 05:37 .local
drwxr-xr-x  3 james james     4096 2008-12-29 05:38 .mcop
-rw-------  1 james james       31 2008-12-29 05:38 .mcoprc
drwx------  4 james james     4096 2008-12-29 20:18 .mozilla
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Music
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Pictures
-rw-r--r--  1 james james      586 2008-12-28 19:39 .profile
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Public
drwxr-xr-x  2 james james     4096 2008-12-31 20:35 .qt
-rw-------  1 root  root      1024 2008-12-31 20:49 .rnd
-rw-r--r--  1 james james        0 2008-12-28 19:45 .sudo_as_admin_successful
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Templates
drwx------  4 james james     4096 2008-12-31 20:36 .thumbnails
drwxr-xr-x  2 james james     4096 2008-12-29 05:37 Videos
-rw-r--r--  1 james james 13510516 2008-05-26 00:18 webmin_1.420_all.deb
-rw-------  1 james james      169 2008-12-31 20:34 .Xauthority
-rw-------  1 james james    14472 2009-01-01 15:14 .xsession-errors
-rw-r--r--  1 james james     1234 2008-12-31 21:43 zaphu
-rw-r--r--  1 james james     1234 2008-12-31 21:38 zaphu~

---

### Post by taurus on 2009-01-03
I don't see adweb in your $HOME.  Are you sure it is not in /home/james/james?

```
ls -la /home/james/james
```

---

### Post by JKHinton CPBD on 2009-01-04
Taurus,

You are correct, thank you so much for the help.  I guess I copied the folder name james twice by mistake. The folks in this Ubuntu forum are the best.

---

