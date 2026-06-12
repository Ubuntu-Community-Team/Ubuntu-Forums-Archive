---
title: "Ubuntu 9.04 Internet connection"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by jcojr72 on 2010-01-17
Hi,
I have just installed Ubuntu 9.04 with the alternate install disk on an old Gateway Solo 9500.  Previously the computer was running windows XP, and I could connect to my cable modem through the ethernet port.  I have a wireless card which would not connect to my wireless modem while running XP.  I am trying to connect to the internet through the ethernet port, but can't.  When I plug the cable in, the orange lights that used to flash while running XP do not flash, as if the port is not recognized.  Also, if I look under the menu System-Administration I only have a network tools option, from what I have read there should also be a Network configuration option. 
As for the wireless card, I have a wireless icon in the upper right hand corner, but it can't seem to find my wireless network.  Again this did not work on XP so I may need a new card, but all the lights are flashing on the card.

Any help would be appreciated.

Thanks,
Jeremiah

---

### Post by zvacet on 2010-01-18
Applications>accessories>terminal and type

```
lspci | grep Network
```

Post output here and someone will help you.

---

### Post by jcojr72 on 2010-01-18
I am not too sure what I did, but both the wireless and ethernet port are now working.   I appreciate the help offered in this forum, I am sure I will be back.

Thanks.

---

