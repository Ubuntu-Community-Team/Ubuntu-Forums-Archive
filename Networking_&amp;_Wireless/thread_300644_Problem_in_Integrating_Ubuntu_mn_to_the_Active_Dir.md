---
title: "Problem in Integrating Ubuntu m/n to the Active Directory"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Uday123 on 2006-11-16
I have configured My Ubuntu machine as Active directory member.
When I tried login with my credentials (AD) to my machine,it was throwing the messages in Log file(/var/log/auth.log ,/var/log/user.log, /var/log/syslog etc.)

Yesterday I am able to login with my credentials and it was authenticating across AD.

I am not understanding what the meaning of these messages...Can you please help me in resolving this issue...

Error Messages:
Nov 16 15:28:22 ubuntu-failover sudo: PAM unable to dlopen(/lib/security/pam_windbind.so)
Nov 16 15:28:22 ubuntu-failover sudo: PAM [dlerror: /lib/security/pam_windbind.so: cannot open shared object file: No such file or directory]
Nov 16 15:28:22 ubuntu-failover sudo: PAM adding faulty module: /lib/security/pam_windbind.so

---

