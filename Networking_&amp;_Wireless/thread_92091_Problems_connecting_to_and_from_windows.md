---
title: "Problems connecting to and from windows"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by Diod on 2005-11-18
When im trying to connect to/from windows to/from this linux pc, i cannot access it.
I cant access apache, nor samba nor can i checkout my windows network. The workgroup and everything has been entered correctly. There is a router in the "center "of the network.

---

### Post by cwaldbieser on 2005-11-19
[QUOTE=Diod]When im trying to connect to/from windows to/from this linux pc, i cannot access it.
I cant access apache, nor samba nor can i checkout my windows network. The workgroup and everything has been entered correctly. There is a router in the "center "of the network.[/QUOTE]
Can you ping or traceroute from one PC to another?  You may just have a basic connectivity problem.

If you can't ping, try posting the results of these commands:
(Ubuntu)
```

$ ifconfig
$ route

```

(Windows)
```

C:\>ipconfig
C:\>route print

```

---

