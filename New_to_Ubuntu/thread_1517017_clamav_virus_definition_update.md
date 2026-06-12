---
title: "clamav virus definition update"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-24
I have updated virus definitions using this command,

 ```
sudo freshclam
```And i got this as output,

```
karthick@Ubuntu-desktop:~$ sudo freshclam
ClamAV update process started at Thu Jun 24 22:26:43 2010
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.96 Recommended version: 0.96.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)
Trying host db.local.clamav.net (61.177.194.226)...
WARNING: getfile: daily-11243.cdiff not found on remote server (IP: 61.177.194.226)
WARNING: getpatch: Can't download daily-11243.cdiff from db.local.clamav.net
Trying host db.local.clamav.net (219.106.242.51)...
Downloading daily-11243.cdiff [100%]
Downloading daily-11244.cdiff [100%]
Downloading daily-11245.cdiff [100%]
Downloading daily-11246.cdiff [100%]
Downloading daily-11247.cdiff [100%]
Downloading daily-11248.cdiff [100%]
Downloading daily-11249.cdiff [100%]
Downloading daily-11250.cdiff [100%]
Downloading daily-11251.cdiff [100%]
Downloading daily-11252.cdiff [100%]
Downloading daily-11253.cdiff [100%]
Downloading daily-11254.cdiff [100%]
Downloading daily-11255.cdiff [100%]
Downloading daily-11256.cdiff [100%]
Downloading daily-11257.cdiff [100%]
daily.cld updated (version: 11257, sigs: 98480, f-level: 51, builder: ccordes)
bytecode.cld is up to date (version: 26, sigs: 3, f-level: 51, builder: nervous)
Database updated (803210 signatures) from db.local.clamav.net (IP: 219.106.242.51)
WARNING:[COLOR=Red] Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl
connect(): No such file or directory[/COLOR]
```

But there is a warning message in it,can anyone say me what it is..?Thanks in advance...

---

### Post by karthick87 on 2010-06-25
Bump for a move..

---

### Post by Sir Jasper on 2010-06-25
Hi,

Firstly, I think it worked using an alternative method which the program itself found.

It is recommending that you update your version from 0.96 to 0.96.1 so read the link [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) you were quoted. However, if the program continues to function properly it may not be a cause for major concern.

I stopped using Clam a while ago so I have no recent direct experience.

My regards

PS Pleased to see your separate OO problem is solved.

---

