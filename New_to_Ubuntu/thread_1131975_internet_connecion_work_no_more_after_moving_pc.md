---
title: "internet connecion work no more after moving pc"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by alan ford on 2009-04-21
hi. i installed ubuntu hardy heron on my bro's pc (dual boot xp), at my home and everything was fine. now at his home, it does not connect anymore to the internet( whereas xp does ). i did not change any settings, it is connected through ethernet cable and set to roaming that i suppose it finds the connection automatically.what can i do?

---

### Post by LowSky on 2009-04-21
the settings comming form his router or cable modem could be an issue.

Could you fill us in on the type of serive and what company, and the type of modem please.

---

### Post by hesjnet on 2009-04-21
Maybe your xp install has a static ip configured? That meaning NOT roaming in xp. Do you know if this is the case?

Technically speaking you have to have DHCP enabled(wich is quite standard on routers) to use roaming.

---

### Post by Iowan on 2009-04-21
Try disabling (unchecking) the Roaming - no guarantees... you can always put it back.

---

### Post by alan ford on 2009-04-22
> **hesjnet said:**
> Maybe your xp install has a static ip configured? That meaning NOT roaming in xp. Do you know if this is the case?

Technically speaking you have to have DHCP enabled(wich is quite standard on routers) to use roaming.

actually xp connects through dhcp.
i run pppoeconf command and the result is that it sees the ethernet interface, but  comes out with a (translated roughly from italian)" access concentrator of the provider does not respond. try if the cables are connected. another reason for the check failure could be another instance of pppoe which is controlling the router"
i am baffled

following the ubuntu pocket guide i connected with static IP although i thought i could not as the other os connects through dhcp. but anyway it works. thank you for your time

---

