---
title: "Remote access to another pc"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by badgandalf on 2008-08-10
I've been trying to build a media server (based on Xubuntu) for my content and backups at home but have been facing several problems i cannot resolve and that, i hope, you'll be able to help me with. I've followed Brett Thomas guide ([http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)) and created a home server that works reasonably well. 

My problems, however, relate to the PC I use to access my headless server. Essentially, everything works fine when I use one of my Windows PCs but fails misserably when trying to access from my Kubuntu desktop.

For example, from Kubuntu I can access the server via ssh, but cannot through VNC: it connects and before bringing the first screen back, disconnects. That's where, I believe the problem probably is, because with several applications the same thing happens. The client connects and then keeps waiting for an answer from the server that never comes. Another example is when I try to use the web access to configure some of the applications (([http://restore-backup.com/index.php?option=com_content&view=frontpage&Itemid=1](http://restore-backup.com/index.php?option=com_content&view=frontpage&Itemid=1), MediaTomb, etc...) which I can access from my windows client, but cannot from the Kubuntu one (essentially I fire up Firefox, connect to the configuration URL - Exe: 192.168.1.23/restore - and everything i get is a waiting for server response).

Does this ring a bell on anyones head to help me out? Best regards,

Ignacio

---

### Post by ZootHornRollo on 2008-08-10
using 'remote desktop viewer' i had problems same as yours, still do.  but if i use terminal and type 'vncviewer ip.ip.ip.ip:0' it works fine.

remote desktop viewer used to work but stopped after i installed some updates a few weeks ago.

---

### Post by badgandalf on 2008-08-10
I tried that with the same result...it goes off almost immeately without even showing the same screen. This is the console output I get:

[I]ignacio@atico:~$ vncviewer 192.168.1.36:0
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "VNC sotano@"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using shared memory PutImage
vncviewer: read: Connection reset by peer
ShmCleanup called[/I]

Rgds,

Ignacio

---

