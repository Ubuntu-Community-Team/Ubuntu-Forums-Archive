---
title: "Can't join domain using ads  -  SAMBA"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Kyo Sa Nim Cat on 2008-09-24
Hi all,

I’m trying to change the Windows server to Linux. I’m using Ubuntu 8.04 LTS with Samba 3.02. Security is ads so the server is a domain server. The good thing is I had it working where as windows could see the share files and Ubuntu could see the windows files. 

I started downloading files into the share directory and started setting up permission. I rebooted the server and now I can not join the domain using net ads join. I can join using RPC but share don’t work.

I can see my domain users and groups using wbinfo. I using Windows2k in native mode and Realm is pointing to the domain.

The error is net usershare error 255: net usershare add: cannot convert name "Everyone" to a SID.

I found that Windows 2k and up do not send a SID for group “Everyone”. But something in Samba is asking for that SID (I think). Before win 2k anonymous SID was use (or was there) in group “Everyone”. I think I may have added an additional part of Samba (for putting domain group into the group gui) and reboot that cause this problem.

---

