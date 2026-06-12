---
title: "simple mail relay for home server"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by rippunzel on 2007-09-20
G'day all,

Looking for suggestions for a simple mail relay setup for my headless Dapper server.  All I really want is to be able to forward admin-type mail (like the ones from backuppc) to my work mail or ISP address so that I can 'keep an eye' on my machine without having to access it remotely.  

Won't bother with trying to recieve/collate  mail with the box - just want to be able to be notified at work when a backup (with BackupPc) fails, or the kids 'accidently' reboot the server  etc etc

Seems like a myriad of ways of doing this - but way overkill for what I need . .. 

Any ideas?

---

### Post by dcstar on 2007-09-20
> **rippunzel said:**
> G'day all,

Looking for suggestions for a simple mail relay setup for my headless Dapper server.  All I really want is to be able to forward admin-type mail (like the ones from backuppc) to my work mail or ISP address so that I can 'keep an eye' on my machine without having to access it remotely.  

Won't bother with trying to recieve/collate  mail with the box - just want to be able to be notified at work when a backup (with BackupPc) fails, or the kids 'accidently' reboot the server  etc etc

Seems like a myriad of ways of doing this - but way overkill for what I need . .. 

Any ideas?

Just install Postfix and it will send out all e-mails passed to it (either directly or via your ISPs SMTP server).

---

