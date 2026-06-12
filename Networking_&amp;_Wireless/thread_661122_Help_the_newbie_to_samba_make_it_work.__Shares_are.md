---
title: "Help the newbie to samba make it work.  Shares are visable, connecting can not find."
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-07
I've gotten samba set up and finally gotten the shares visible to other Ubuntu machines and my windows machine.  

However when I connect to them I get a classic file not found message in both OSs, however they word it.

I have a sneaking suspicion that this problem is a problem with my permissions on the computer sharing the shares.  However, I don't know if that is correct much less how to remedy.

This is my smb.conf.  The shares in the home folder (Documents, Music, Pictures..etc) are all the linux version of "shortcuts" to the actual directories that exist on /media/data.  I assume I can do that.  What are the linux versions of "shortcuts" called.  (Ex.  Navigating to /home/steve/documents is the same as navigating to /media/data/documents)

> [global]
workgroup = LAN
netbios name = Desktop
restrict anonymous = no
security=share

[Documents]
case sensitive = no
guest ok = yes
path = /home/steve/Documents
read only = no

[Examples]
case sensitive = no
guest ok = yes
path = /home/steve/Examples
read only = no

[Music]
case sensitive = no
guest ok = yes
path = /home/steve/Music
read only = no

[Pictures]
case sensitive = no
guest ok = yes
path = /home/steve/Pictures
read only = no

[Videos]
case sensitive = no
guest ok = yes
path = /home/steve/Videos
read only = no

[Home]
case sensitive = no
guest ok = yes
path = /home/steve
read only = no

[Movies Drive]
case sensitive = no
guest ok = yes
path = /media/movies
read only = no

[Linux Installs]
case sensitive = no
guest ok = yes
path = /media/data/Linux Installs
read only = no

[Windows Installs]
case sensitive = no
guest ok = yes
path = /media/data/Windows Installs
read only = no

---

