---
title: "Using kerberos with smbclient"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by ecor6633 on 2008-11-04
Hello,

I'm trying to use Kerberos 5 to authenticate using smbclient.

I'm not sure if what i'm doing is possible.

Until now i have kerberos 5 working, kinit ok, klist ok etc.

I installed pam-krb5 and have set /etc/pam.d/samba like that :
```
@include common-auth
@include common-account
@include common-session

auth      sufficient  /lib/security/pam_krb5.so minimum_uid=1000
account   sufficient    /lib/security/pam_krb5.so minimum_uid=1000
password  sufficient  /lib/security/pam_krb5.so use_authtok minimum_uid=1000
session   optional    /lib/security/pam_krb5.so minimum_uid=1000

```

I think samba is using pam and so why would smbclient -k not work ?

It always says :
session setup failed: NT_STATUS_LOGON_FAILURE

---

