---
title: "Can't Open app from Menu"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-11-02
Hello,

I clean installed 9.10 and installed kppp with the Ubuntu Software Center, when I try to open it from Applications, Internet, KPPP, I get a Failed to execute child process "kppp" (Permission denied), error.

I can open it from the terminal with sudo.

How can I change this, in 9.04 it would open from Applications OK.

Thanks.

---

### Post by samjh on 2009-11-02
Could you please perform this command in ther terminal and post your output here?

```
ls -l /usr/bin/kppp
```

---

### Post by barnaclebill18 on 2009-11-02
Hello samjh

bill2@bill2-laptop:~$ ls -l /usr/bin/kppp
-rwsr-xr-- 1 root dip 615596 2009-10-19 10:26 /usr/bin/kppp
bill2@bill2-laptop:~$

---

### Post by samjh on 2009-11-02
This was a problem some time ago in 2006-2007, which had long been fixed.  Perhaps it has resurfaced.

As a temporary workaround, do the following (if you use Gnome):
[list=1]
[*]Run this command: **sudo apt-get install kdesudo**
[*]Right-click on the Applications menu, and select Edit Menus.
[*]Find the KPPP launcher in the Items list.  You will need to double-click on Internet in the Menus list at the left of the window.
[*]Right-click on the launcher, and select Properties.
[*]In the Command field, prefix kppp with kdesudo, so that it reads: **kdesudo kppp**
[/list]

If you use KDE, please use KDE's menu editor to make the necessary changes to the KPPP launcher.  You should already have kdesudo.

The issue is that kppp needs to be run with root previlages to perform some actions.  In most distributions of kppp, this is done by using the setuid feature, which allows the program to be run by a user with previlages of a different user (in kppp's case, root).  According to the output you posted, setuid is enabled for kppp, so it should theoretically work.  My suggestion is a workaround, seeing as how the setuid feature doesn't seem to be working for your installation of kppp.

The original bug report from 2006 is here:
[https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/53879](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/53879)

---

### Post by barnaclebill18 on 2009-11-02
Thanks, I will give that a try and report the results.

---

### Post by barnaclebill18 on 2009-11-02
Well, it worked.

Thank you.

---

