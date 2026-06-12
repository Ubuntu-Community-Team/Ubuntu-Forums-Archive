---
title: "error authenticating with active directory"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by eltidi on 2007-02-28
I have set up a my ubuntu box so I can authenticate with Active Directory using the following
howto.
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

The problem is everytime i try using su to log on with a domain user I got the following message in 
var/log/auth.log

pam_winbind[17696]: request failed: STATUS_BUFF
ER_OVERFLOW, PAM error was 4, NT error was STATUS_BUFFER_OVERFLOW

Any help would be appreciated

---

