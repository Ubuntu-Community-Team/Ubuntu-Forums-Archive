---
title: "Help me fix my network and set up samba.   (Slow - increase number of connections?)"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-05
I don't know which is most important, so lets start with what may be easiest to hardest.

1)
When I am uploading a torrent (fedora for example) the upspeed is about 30-40 k.  Everything will be SLOW.  Firefox will spend minutes saying "connecting to www.google.com"..etc.  I never had this problem in Windows.  It would slow down, but not that bad.  In windows I increased the number of connections allowed by using a patched TCPIP.sys.  Is there something similar I can to to ubuntu? 
Some sites, like IMDB, wont even load.
Sometimes when I have a couple tabs open (only one of them loading) it's slow.  For example it took me 45 seconds to open one of the "similar threads" links that's just above this window I'm typing in.  I have no active torrents.  That's about average when compared to uploading.

2)
I can't get samba set up for the life of me!  My windows laptop won't even connect "Network is not accessible" Network is the name of my workgroup.  My other ubuntu laptop doesn't display anything in smb:///

Here is my  smb.conf

> [global]
workgroup = NETWORK
security = share
netbios name = Desktop
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
security = share
restrict anonymous = no
domain master = no
preferred master = no

[home folder]
case sensitive = no
guest ok = yes
path = /home/steve
read only = no

[movies drive]
case sensitive = no
guest ok = yes
path = /media/movies
read only = yes


---

