---
title: "Remote Desktop and filesharing"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by gejr on 2007-02-25
When I use microsofts Remote Desktop Connection to connect to a windows machine I have an option to share "local drives" and in that way be able to just drag files from the remote desktop to my local desktop. What's the best way to accomplish something similar with Ubuntu? I'm using it's default Terminal Server to connect to a windows xp machine. It works great, but I'd really love some way to easily share files between the host desktop and the remote.

Hope some of you understand my problem here. :)

Any suggestions?

---

### Post by gradedcheese on 2007-02-25
It's probably just using windows file sharing (handled via Samba in Linux) to do it, and there's no reason why you can't do the same thing.  However if it's doing it over the Internet rather than just the LAN, then it becomes a bit more complicated (and probably a security risk).  What sort of setup do you have, is the Windows terminal server on the same LAN?

---

### Post by gejr on 2007-02-26
Sorry for bumping this.

Well yes, the machines are on the same lan usually. But I travel around with my laptop so sometimes i need this type of access from other places. With Windows XP this thing was so easy to accomplish. I love Ubuntu by now and I really hope this isn't something It'll be unable to do! :)

---

