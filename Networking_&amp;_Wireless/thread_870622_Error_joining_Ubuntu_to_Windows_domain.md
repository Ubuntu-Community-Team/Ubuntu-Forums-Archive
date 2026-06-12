---
title: "Error joining Ubuntu to Windows domain"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by hailang on 2008-07-26
Dear all,

I try to join some test computers to existing Windows 2003 domain (follow instruction in [https://help.ubuntu.com/community/ADAuthentication](https://help.ubuntu.com/community/ADAuthentication)). With the first one, I used new name and it is joined successfully. But with the second one, I used it's old name in Windows XP then the following error occur:
```
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Deleted account for 'PC-HCM025' in realm 'TMF.COM'
Failed to join domain: Type or value exists

```

I also checked that the name PC-HCM025 is not exist in domain at the moment. I also checked following files and not typo error in them:
```
/etc/krb5.conf
/etc/samba/smb.conf
/etc/nsswitch.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/hosts
```

I also rename the computer to new name and error still there. Please help me to fix. Thank you.

---

### Post by ivanrengo on 2008-10-31
I have the same problem than you and I can't fix it. Did you or anyone else solved this problem?

Salutes

---

### Post by ivanrengo on 2008-11-03
I solved the problem!

I had the follow message when I made "net ads join -U administrator"

  Using short domain name -- TESTDOMAIN
  Failed to set servicePrincipalNames. Please ensure that
  the DNS domain of this server matches the AD domain,
  Or rejoin with using Domain Admin credentials.
  Disabled account for 'TESTPROXY' in realm 'TESTDOMAIN.TEST'


The error was in /etc/hosts. Where said "192.168.0.1 testproxy" I changed it to "192.168.0.1 testproxy.testdomain.test test" and It works.

---

