---
title: "NTLMAPS problems on Edgy"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by MouseAT on 2007-01-26
I've had NTLMAPS installed once before on Dapper, but I'm now trying to set it up on a new install of Edgy. I've downloaded the official Edgy .deb from the Ubuntu package site, but it's failing to install with the following error message:
```
athornton@teacher-lt-at:~$ sudo dpkg -i ntlmaps_0.9.9-4_all.deb
Selecting previously deselected package ntlmaps.
(Reading database ... 88032 files and directories currently installed.)
Unpacking ntlmaps (from ntlmaps_0.9.9-4_all.deb) ...
Setting up ntlmaps (0.9.9-4) ...
sed: -e expression #5, char 37: unknown option to `s'
dpkg: error processing ntlmaps (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ntlmaps
```

Anyone know what's going wrong? I'm stuck with an ISA proxy at work, and really need to be able to use APT to install packages from the net.

---

### Post by MouseAT on 2007-02-01
I've found the solution at last - the installer didn't like the special characters in my password. In the end, I left the password field blank, and edited /etc/ntlmaps/server.cfg by hand after installation.

---

