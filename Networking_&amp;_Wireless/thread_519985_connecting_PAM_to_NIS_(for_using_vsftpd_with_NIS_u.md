---
title: "connecting PAM to NIS (for using vsftpd with NIS users)"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by motionsiren on 2007-08-07
I searched the entire forum, other forums too. Even got to the last page of several google searches.

**Goal:** To ftp into my server (it runs vsftpd) as a user who's account is polled from NIS

I installed vsftpd based on the Ubuntu 6.06.1 LTS Server guide and it works, with local accounts. NIS also works; I can ssh in with NIS based accounts and home directories are mounted via NFS. The problem is PAM talking to NIS, since vsftpd uses PAM for it's authentication - at least how mine is compiled.

I don't believe this has anything to do with the vsftpd.conf, but rather NIS and PAM related files. Only problem is, I have not a clue which files and what to change. I am finding reports of people past this point in configuration via google, but no instructions, or even hints on how to get it glued together.

Can you help?

---

