---
title: "NFS4 home directory is not mounted with ksu"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by mesh2005 on 2008-01-08
I could successfully install Kerberos, OpenLDAP on my network; I changed the login and SSH to use the Kerberos tickets and this works correctly. Home directories are mounted successfully upon login, however; when ksu to another user I get 'Permission Denied' and I cannot access any home directory. Here is my log:
Jan  8 10:23:30 machine1 rpc.gssd[17142]: ERROR: GSS-API: error in gss_acquire_cred(): Miscellaneous failure - Unknown code krb5 195
Jan  8 10:23:30 machine1 rpc.gssd[17142]: WARNING: Failed to create krb5 context for user with uid 1001 for server nfs-server-machine
Jan  8 10:23:30 machine1 rpc.gssd[17142]: ERROR: GSS-API: error in gss_acquire_cred(): Miscellaneous failure - Unknown code krb5 195
Jan  8 10:23:30 machine1 rpc.gssd[17142]: WARNING: Failed to create krb5 context for user with uid 1001 for server nfs-server-machine

Any help?

Thank you

---

