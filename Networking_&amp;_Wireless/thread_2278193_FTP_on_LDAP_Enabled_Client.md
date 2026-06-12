---
title: "FTP on LDAP Enabled Client"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by Mike_Cataldo on 2015-05-14
I've successfully installed FTP on a standalone server (read/write/permissions all check out).  I created a local account and was able to read/write files.  I'm now trying to install FTP on an LDAP enabled client and having authentication issues.  I'd like to be able to FTP into the server using LDAP authentication information but this does not work.  I then tried to create a local account but that also fails on FTP authentication.

Can anyone provide guidance on LDAP enabled FTP configuration.  I don't see anything in the /etc/vsftpd.conf file that pertains to LDAP.  I see very little in the /var/log/vsftpd.log file other than "[filetransfer] FAIL LOGIN: Client X.X.X.X".

---

### Post by Mike_Cataldo on 2015-05-14
I do see the following error in syslog but I am able to log into this server with LDAP credentials

PAM unable to dlopen(pam_systemd.so): /lib/security/pam_systemd.so: cannot open shared object file: No such file or directory

---

