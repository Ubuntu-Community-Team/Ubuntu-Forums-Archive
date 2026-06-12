---
title: "Windows Domain file synchronization question"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by brianwtn on 2008-07-03
Hoping to transition from XP/Vista workstations to Linux, but need to dual-boot for a while. So looking for a little advice prior to setting up an Ubuntu and Vista dual boot laptop on a Windows 2003 AD domain. Currently all users have their files stored on the Win2k3 server, and their 'Documents' directory is redirected to the server share with offline file synchronization. Is there a preferred way to keep the current offline file repository available for both the Vista and Ubuntu partition (i.e. for working with files from either OS while traveling)?

I had thought of either:
(a) a three partition setup - one for each OS and a third for docs. Then set both OSs to sync the docs partition with the server.
(b) having only two partitions, once for each OS, with both set to synchronize with the server

Any recommendations on a or b would be appreciated.

Also, what software would you recommend to accomplish this sync between Ubuntu and Win2k3? Is rsync the best choice, or has anyone had experience with a better (more user friendly) option?

Thanks so much for the help!

---

