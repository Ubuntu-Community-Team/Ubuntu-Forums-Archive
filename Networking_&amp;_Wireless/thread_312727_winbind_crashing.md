---
title: "winbind crashing"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by defenestrator on 2006-12-04
ive been tring to get my Ubuntu workstation to Authenticate against a 2000 domain server and Winbindd keeps crashing every time i start it and i have no idea what is causing it ](*,) 

the only entres in the log is
```
[2006/12/05 14:59:23, 1] nsswitch/winbindd.c:main(978)
  winbindd version 3.0.22 started.
  Copyright The Samba Team 2000-2004
[2006/12/05 14:59:23, 0] nsswitch/winbindd.c:main(1071)
  unable to initalize domain list

```

anyone have any ideas?

---

### Post by o517375 on 2007-02-22
My samba Version 3.0.22 crashed also on start with the same error message (except I am using a W2k3 domain) and did not ever figure out why it did that, but I did fix it with these steps:

1) Download source samba and compile with --prefix=/usr/local/samba
2) copy configuration files to /usr/local/samba/lib
3) start samba /usr/local/samba/sbin/smbd -D and nmbd -D and winbindd
4) Join the windows domain with net ads join -U <uname@domain>
5) Now kill smbd, nmbd, winbindd and restart samba and winbind using the ubuntu binaries.
with /etc/init.d/samba start and /etc/init.d/winbind start

Now wbinfo -t should show good trust.

Craig

---

