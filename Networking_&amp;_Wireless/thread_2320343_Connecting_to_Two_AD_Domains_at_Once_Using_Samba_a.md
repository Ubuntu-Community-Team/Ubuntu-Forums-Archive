---
title: "Connecting to Two AD Domains at Once Using Samba and Winbind."
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by andrew292 on 2016-04-13
Dear All.

I am using Ubuntu 15.10 and Samba 4.1.17-Ubuntu.

I am trying to get two 'instances' of Samba and Winbind running together   on the same Ubuntu installation so that I can share common files with   two separate Windows AD domains at once. I cannot get this to work.   Please note that i cannot trust the two AD domains to each other (one is   SBS). 

I am able to use symbolic links to start two smbd, nmbd and winbindd   processes. I have modified the start up scripts appropriately,   everything was going well until i tried to start up two winbindds at   once. This didn't work, i could only have one or the other. So i have   this system working, joined to two domains etc etc, but winbindd only   works if i start one or the other and so i can share files out to only   one AD domain at once. 

for both domains but only using one winbindd at once

wbinfo -u works
wbinfo -g works
getent passwd works
getent group works
kinit administrator works
chhown domain/user diretory works

I suspected that the winbindd socket was the problem. If I use the   winbindd:socket dir = directive in smb.conf, i can move the winbind pipe   to a different directory, and so set up two winbindds using symbolic   links with separate smb.conf files to use separate winbindd pipes. I  have tested this, and when using separate winbindd socket directories i  can get two winbindd s running at once, so this has confirmed that this  is why two would not run at once before when using only one winbindd  socket.

The problem is that once i move the winbindd socket using   winbindd:socket dir = in smb.conf , samba/winbind/nss ? stops working.   I'm confused at to which services need to access the winbindd pipe. Do i   need to tell nss to use the moved socket ? I gather that smbd knows   that the socket has moved as it's in the smb.conf file.

with winbindd:socket dir = xxx set

wbinfo -u not work
wbinfo -g not work
getent passwd not work
getent group not work
kinit administrator works
chhown domain/user diretory not work

Can anyone tell me in nss_switch.conf when i put winbind, how does this   find the winbind service ? how can i point it to the winbind which uses   the moved socket ... ?

Can anyone help with this ? or point me to the right documentation ..

I would love to read an overview of how Samba, Winbind and nss work together but have been unable to find such a thing.

Any help much appreciated.

Andrew.

---

### Post by Irihapeti on 2016-04-13
Please don't keep on posting multiple threads on the same topic.

Closed.

---

