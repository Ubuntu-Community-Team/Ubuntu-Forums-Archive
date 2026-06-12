---
title: "SSSD error with domain joined 20.04"
date: 2021-01-28
forum: Networking &amp; Wireless
---

### Post by thinkpad770x on 2021-01-28
Hello,
I have added an Ubuntu 20.04 client to a test domain. Network logins work correctly, LDAP groups look to be working and I am able to receive kerberos tickets and create keytab files. However I run into the same error no matter what method I use to join the test machine to the domain. Any help is greatly appreciated



sssd.service - System Security Services Daemon
     Loaded: loaded (/lib/systemd/system/sssd.service; enabled; vendor preset: >
     Active: active (running) since Thu 2021-01-28 14:46:40 PST; 19s ago
   Main PID: 5424 (sssd)
      Tasks: 4 (limit: 2834)
     Memory: 35.4M
     CGroup: /system.slice/sssd.service
             &#9500;&#9472;5424 /usr/sbin/sssd -i --logger=files
             &#9500;&#9472;5425 /usr/libexec/sssd/sssd_be --domain TEST.INC --uid 0 --gid 0>
             &#9500;&#9472;5426 /usr/libexec/sssd/sssd_nss --uid 0 --gid 0 --logger=files
             &#9492;&#9472;5427 /usr/libexec/sssd/sssd_pam --uid 0 --gid 0 --logger=files

Jan 28 14:46:40 UBUNTU5.TEST.INC sssd[5426]: Starting up
Jan 28 14:46:40 UBUNTU5.TEST.INC sssd[5427]: Starting up
Jan 28 14:46:40 UBUNTU5.TEST.INC systemd[1]: Started System Security Services D>
Jan 28 14:46:47 UBUNTU5.TEST.INC sssd[be[5425]: Backend is online
Jan 28 14:46:48 UBUNTU5.TEST.INC sssd[5451]: ; TSIG error with server: tsig ver>
Jan 28 14:46:48 UBUNTU5.TEST.INC sssd[5451]: ; TSIG error with server: tsig ver>
Jan 28 14:46:48 UBUNTU5.TEST.INC sssd[5455]: ; TSIG error with server: tsig ver>
Jan 28 14:46:48 UBUNTU5.TEST.INC sssd[5455]: ; TSIG error with server: tsig ver>
Jan 28 14:46:48 UBUNTU5.TEST.INC sssd[5459]: tkey query failed: GSSAPI error: M>
Jan 28 14:46:49 UBUNTU5.TEST.INC sssd[5459]: tkey query failed: GSSAPI error: M>
~
lines 1-22/22 (END)

---

