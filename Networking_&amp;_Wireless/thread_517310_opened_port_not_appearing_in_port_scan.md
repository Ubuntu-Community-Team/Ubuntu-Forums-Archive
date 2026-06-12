---
title: "opened port not appearing in port scan"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by cameran on 2007-08-04
hello,

i am trying to open a port up for connecting through direct IP to play a game with a friend.  i have opened the port up through firestarter and on my router, but when i do a port scan of my box it never comes up as open.

how can i get the port to open so that i can play with my friend?  the port i need is UDP 2056.

thanks :(

cameran

---

### Post by noob12 on 2007-08-04
Are you doing the scan from another box in your own net or outside your router?  I'd try to separate the issues by first checking within your own net.  Then move to the router.

The following would provide some help diagnosing whether the port is open on your own machine

```

sudo iptables -nL

```

---

