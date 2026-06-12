---
title: "[SOLVED] problem on network drive file sharing"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by xnostradamusx on 2008-07-20
we got 10 windows xp installed here and a windows 2003 server

we can connect file share and able to mount a network drive fast and easy..

but i installed ubuntu desktop latest in what im using 

when i click the network i am able to see our network server and see other people also connected in the network

but when i open the suppose shared network drive in the server it is empy

but the other computers running windows xp can read/write in the network drive.

does anyone have an idea to fix this

anyway im using here a desktop pc x86

---

### Post by karlos876 on 2008-07-20
I'm having the same problem. Every other computer on my network, including those running Ubuntu 7.10 have no trouble connecting to my server (Windows Server 2003). It shows up when I browse "Network Servers", but when I try to open it it is empty. It doesn't even ask me for my login info.

---

### Post by superprash2003 on 2008-07-20
in the terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine

---

### Post by xnostradamusx on 2008-07-21
thanks for the solution you give but too late i already 

transfered from kubuntu it seems i connected with the network 

more easier using the program called samba it just asked for the 

network password and wallah i was able to connect and see the 

files in the network drive

---

