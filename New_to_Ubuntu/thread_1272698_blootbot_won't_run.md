---
title: "blootbot won't run"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by moondoggy17 on 2009-09-22
ok i install blootbot via package manager and tried to run it in terminal and this is a i get.

```
moon@old:~$ blootbot

Can't locate /etc/blootbot/directories in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/blootbot line 35.

BEGIN failed--compilation aborted at /usr/sbin/blootbot line 52.

moon@old:~$ sudo apt-get install perl

[sudo] password for moon: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

perl is already the newest version.

The following packages were automatically installed and are no longer required:

  esound

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.


```

i'm using xubuntu with fluxbox wm

---

### Post by si3ge on 2010-12-16
so I'd like to revive this thread because I am running into the exact same issue also running xubuntu
I installed all the packages it requires and recommends to run but i see this when i try to start it.
has anyone resolved this yet?

---

