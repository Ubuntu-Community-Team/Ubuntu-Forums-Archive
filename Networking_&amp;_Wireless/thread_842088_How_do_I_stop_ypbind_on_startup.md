---
title: "How do I stop ypbind on startup?"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by arguellodw on 2008-06-27
I tried running *[COLOR="Red"]ps -ef | grep ypbind[/COLOR]* and sudo killing the process. This does not stop the machine from trying to bind at each new boot.

--How do I permantly stop ypbind from trying to bind?

---

### Post by Rocket2DMn on 2008-06-27
Try using System->Administration->Services or install boot-up manager
```
sudo apt-get install bum
```
Then find it under System->Administration->Boot-Up Manager (and check the box at the bottom for Advanced, then check the Services tab).

---

### Post by arguellodw on 2008-06-27
Worked like a charm. Thanks.

---

### Post by barisergun on 2012-07-17
On Ubuntu 12.04 if ypbind is installed check your /etc/defaults/nis file and make sure your NIS client mode is false. other wise you will have a respawned ypbind client process.

---

### Post by wildmanne39 on 2012-07-17
Hi, thanks for sharing, the thread has been closed, please do not post in a thread that has been inactive for a year or more.
Thanks

---

