---
title: "switching locations (remote ssh)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by dmizer on 2007-06-19
i have a server which creates a reverse ssh tunnel which i can then use to configure the server from my home when necessary.  i have a dyndns domain pointed to my home ip address, and i have the tunnel set up to connect to my dyndns domain name rather than my home ip address like so:
```
ssh -N -R $REMOTE_PORT:localhost:22 $REMOTE_DYNDNS-HOST
```

the problem is, that now i am moving but i will still need to remotely access this server, and the only way i will have to access the server is by setting up a cron job to establish the reverse tunnel.

currently i do have physical access to the server, but after my move, i will no longer have physical access.

how can i avoid the ssh key conflicts after my move?

---

### Post by Mr. C. on 2007-06-20
How about creating a second dyndns name referring to your new residence's IP?

Alternatively, during your  move, set:

StrictHostKeyChecking No

until you are established and can change back.

MrC

---

### Post by dmizer on 2007-06-20
yes, except i won't have internet at the new address until after i move.

---

### Post by Mr. C. on 2007-06-20
Ah, see my edit above.

---

### Post by dmizer on 2007-06-20
perfect ... thank you.

---

