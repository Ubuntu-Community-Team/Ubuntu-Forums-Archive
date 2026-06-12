---
title: "Failover IP Question"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by FrostyFlames on 2008-10-09
Hello, I've recently been asked to look into some kind of server failover for a friend. He has 2 servers running LAMP. If the main server dies for whatever reason he wants the other to pick up the load.

What kind of software would allow me to do something like this?

Any other information would also be helpful.

Thanks!

---

### Post by Drezard on 2008-10-09
Ive been looking into this too. Basically you need to mirror the Mysql database to the other server, using RSYNC or something like that so if the main server goes down, the backup server can pick it right up. 

Then google "failover ubuntu lamp".

Daniel

---

### Post by FrostyFlames on 2008-10-09
I believe he has some kind of mirroring already for the MySQL and web data. I think he wanted something more for the Apache side. I'll have to talk specifics with my friend.

---

