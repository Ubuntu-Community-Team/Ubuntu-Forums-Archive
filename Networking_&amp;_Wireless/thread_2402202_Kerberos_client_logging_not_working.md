---
title: "Kerberos client logging not working"
date: 2018-09-27
forum: Networking &amp; Wireless
---

### Post by ericjoh on 2018-09-27
I've upgraded from Ubuntu 16.04 to 18.04 and now SMB-Kerberos printing through smbspool_krb5_wrapper no longer works and I would like to figure out what is wrong. In 16.04 I can just type "lpr file.pdf", but when doing this in 18.04 I   get "Password for [myuser] on localhost?" and it expects me to type my   password instead of using my Kerberos ticket for sending the print job   to the print queue.

Maybe smbspool_krb5_wrapper is not compatible with the Kerberos version   in 18.04. When I "strace -f" the "lpr" command and then grep for "open"   and "krb" I get almost the same lines in both 16.04 and in 18.04 (the   difference is in the beginning of the lines: "open(" vs   "openat(AT_FDCWD, "):

16.04$ grep ^open /tmp/strace.out|grep krb
open("/usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2", O_RDONLY|O_CLOEXEC) = 3
open("/usr/lib/x86_64-linux-gnu/libkrb5.so.3", O_RDONLY|O_CLOEXEC) = 3
open("/usr/lib/x86_64-linux-gnu/libkrb5support.so.0", O_RDONLY|O_CLOEXEC) = 3

18.04$ grep ^open /tmp/strace.out|grep krb
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libkrb5.so.3", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libkrb5support.so.0", O_RDONLY|O_CLOEXEC) = 3

In 16.04 the three files belongs to libgssapi-krb5-2:amd64,   libkrb5-3:amd64, and libkrb5support0:amd64 which all are version   1.13.2+dfsg-5ubuntu2 while they in 18.04 are version 1.16-2build1.

Question: How can I turn on logging of the Kerberos actions to try figure out the  problem? I have tried setting the user environment variable with "export  KRB5_TRACE=$HOME/krb5.log" before typing "lpr file.pdf", but I get no  log in "$HOME/krb5.log"

---

