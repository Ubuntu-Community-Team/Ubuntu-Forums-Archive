---
title: "Connecting to a windows domain"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by patty522 on 2006-11-24
right i have a big question here,

i need to be able to do

1. Connect a ubuntu workstation to a windows 2003 domain.
2. Get user profiles from the windows 2003 server. (even if this means creating linux profiles on the windows server)
3. Mount /home to users area on the windows 2003 domain server.
4. also be able to connect to the internet via a proxy server.

right i have number 4 coverd but i have no idea where to start to get 1,2 and 3 rolling:rolleyes:

---

### Post by lordgibbness on 2006-11-24
no3 is quite easy - install samba server (do a search in synaptic after adding all repos) and share the folder.

---

