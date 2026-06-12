---
title: "Problem with Samba"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by backupdevice on 2008-07-16
Hi there,

I followed this howto [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605).

I use a dedicated server with ubuntu 8.04 server installed, one ubuntu workstation and one vista computer. 

I made a test config, and the result is that the ubuntu machine and the vista machine see the server, but not the shares.

This is my config.

[Myfiles]

   patch = /media/data/share
   browseable = yes
   readonly = no
   guest ok = no
   create mask = 0644
   directory mask  = 0755
   force user = patrick
   force group = patrick

Can you please help me

---

### Post by Iowan on 2008-07-16
> **backupdevice said:**
> [Myfiles]

   [COLOR="Red"]patch[/COLOR] = /media/data/share
   browseable = yes
   readonly = no
   guest ok = no
   create mask = 0644
   directory mask  = 0755
   force user = patrick
   force group = patrick

I presume this is a typo in the post and not in the config file...

---

