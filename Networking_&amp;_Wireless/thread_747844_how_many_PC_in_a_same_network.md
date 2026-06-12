---
title: "how many PC in a same network"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by kidsrock on 2008-04-06
Dear all,

I have a question about the way to see other pc in the network. In my case, i have 3 pc 
1- use Ubuntu 7.04
2- Use Window 2003.
3- Use Winxp

Firstly, In Window PC, i use (net view) command to view PC in LAN but  i can not see ubuntu PC although i can ping to Ubuntu PC. ???. In addition, when i login into Ubuntu from Window PC, i fill all data (user, pass) to login --> but it always returns error pass and user ???

Secondly, in Ubuntu PC, i don't know how to see other PC in the same network.


Could you tell me the way to cope with the issues? 

Thanks & best regards,
Kid

---

### Post by tamoneya on 2008-04-07
You need to enable samba

system->admisitration->shared folders
from here you should tell it to install SMB and then click add to add a new shared folder.

---

