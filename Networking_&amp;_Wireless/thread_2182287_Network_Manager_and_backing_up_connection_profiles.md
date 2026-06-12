---
title: "Network Manager and backing up connection profiles"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Ranko Kohime on 2013-10-20
I'd like to backup my connection profiles with an application that does not have root access, however Network Manager by default stores them with access only by root.

Is there a way to make NM write them with world-read permissions?  (Security of network passwords is not a great concern, in my case)

---

### Post by papibe on 2013-10-20
Hi Ranko Kohime.

Network-Manager stores config files on /etc/NetworkManager and all the files and subdirectories there have read access to everyone.

Are you referring to other settings or files?

Regards.

---

### Post by Ranko Kohime on 2013-10-21
Ahh, I neglected something.  Specifically the files I mean are in /etc/NetworkManager/system-connections.  NM seems to be writing them all with 600 permissions.

If it makes any difference, I make my connection profiles available to all users so that they come up prior to login.  (in case I need to SSH in)

---

