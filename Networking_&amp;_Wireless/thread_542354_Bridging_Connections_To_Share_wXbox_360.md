---
title: "Bridging Connections To Share w/Xbox 360"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Joeb454 on 2007-09-03
I posted another thread asking how to do this, and after some searching/experimenting, I found that this code works.

```

joe@Joe-Ubuntu:~$ sudo ifconfig eth0 0.0.0.0
joe@Joe-Ubuntu:~$ sudo ifconfig eth1 0.0.0.0
joe@Joe-Ubuntu:~$ sudo brctl addbr br01
joe@Joe-Ubuntu:~$ sudo brctl addif br01 eth0
joe@Joe-Ubuntu:~$ sudo brctl addif br01 eth1
joe@Joe-Ubuntu:~$ sudo dhclient br01

```

Now - What I want to know, is how can I make that into a script that runs every time I boot up?

---

### Post by Joeb454 on 2007-09-03
Anybody know how to make that code into a script to run on start-up?

---

### Post by kronictokr on 2008-03-14
i would seriously be interested in this too

bump

---

