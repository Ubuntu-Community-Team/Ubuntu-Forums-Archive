---
title: "Printing via SMB-Kerberos not working in Ubuntu 18.04"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by ericjoh on 2018-09-20
After upgrading from Ubuntu 16.04 to 18.04 printing via SMB-Kerberos no longer works (printing still works in 18.04 when I print via SMB but I don't want to have the password stored in clear text in /usr/lib/cups/backend/smb).

In 16.04 I can just type "lpr file.pdf", but when doing this in 18.04 I  get "Password for [myuser] on localhost?" and it expects me to type my  password instead of using my Kerberos ticket for sending the print job  to the print queue.

I have the same Kerberos ticket available according to "klist" in 18.04 as I had in 16.04.
I have "AuthInfoRequired negotiate" in /etc/cups/printers.conf
The file /usr/lib/cups/backend/smb is a symbolic link pointing to  /usr/lib/x86_64-linux-gnu/samba/smbspool_krb5_wrapper (in 16.04 it was  pointing at /usr/bin/smbspool_krb5_wrapper).
The permission is 700 on /usr/lib/x86_64-linux-gnu/samba/smbspool_krb5_wrapper.
The version of cups is 2.2.7-1ubuntu2.1 in 18.04 while it was 2.1.3-4ubuntu0.5 in 16.04.
The version of smbclient is 2:4.7.6+dfsg~ubuntu-0ubuntu2.2 in 18.04 while it was 2:4.3.11+dfsg-0ubuntu0.16.04.16 16.04.

Can anybody please help me figure out what the problem is?

Best regards, Eric

---

### Post by ericjoh on 2018-09-22
Maybe smbspool_krb5_wrapper is not compatible with the Kerberos version  in 18.04. When I "strace -f" the "lpr" command and then grep for "open"  and "krb" I get almost the same lines in both 16.04 and in 18.04 (the  difference is in the beginning of the lines: "open(" vs  "openat(AT_FDCWD, "):

16.04$ grep ^open /tmp/strace.out|grep krb
open("/usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2", O_RDONLY|O_CLOEXEC) = 3
open("/usr/lib/x86_64-linux-gnu/libkrb5.so.3", O_RDONLY|O_CLOEXEC) = 3
open("/usr/lib/x86_64-linux-gnu/libkrb5support.so.0", O_RDONLY|O_CLOEXEC) = 3

18.04$ grep ^open /tmp/strace.out|grep krb
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libkrb5.so.3", O_RDONLY|O_CLOEXEC) = 3
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libkrb5support.so.0", O_RDONLY|O_CLOEXEC) = 3

In 16.04 the three files belongs to libgssapi-krb5-2:amd64,  libkrb5-3:amd64, and libkrb5support0:amd64 which all are version  1.13.2+dfsg-5ubuntu2 while they in 18.04 are version 1.16-2build1.

How can I turn on logging of the Kerberos actions to try figure out the problem? I have tried setting the user environment variable with "export KRB5_TRACE=$HOME/krb5.log" before typing "lpr file.pdf", but I get no log in "$HOME/krb5.log".

---

