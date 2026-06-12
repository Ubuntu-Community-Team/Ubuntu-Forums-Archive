---
title: "aklog segmentation fault"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2008-08-11
I'm trying to access AFS using xubuntu and can get a kerberos ticket but aklog gives a segmentation fault:

$ lsb_release -rc
Release:        8.04
Codename:       hardy

$ uname -a
Linux macbook 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

kinit gives me a token

$ kinit [email]lars@FOO.BAR[/email]
[email]lars@FOO.BAR[/email]'s Password:
lars@macbook:/tmp$ klist
Credentials cache: FILE:/tmp/krb5cc_1000
        Principal: [email]lars@FOO.BAR[/email]

  Issued           Expires          Principal
Aug 11 23:00:48  Aug 12 09:00:50  krbtgt/FOO.BAR@FOO.BAR

$ aklog
Segmentation fault


From /var/log/syslog:

Aug 11 22:49:43 macbook kernel: [10266.997562] aklog[28177]: segfault at 48 rip 7fc820243299 rsp 7fff28672fb0 error 4
Aug 11 22:55:41 macbook kernel: [10341.667649] aklog[28432]: segfault at 48 rip 7f48124e7299 rsp 7fff1a915cc0 error 4

The AFS module seems to be available and working:

$ lsmod |grep afs
openafs               637984  3

I can even read public AFS directories, but not get an AFS token.

---

