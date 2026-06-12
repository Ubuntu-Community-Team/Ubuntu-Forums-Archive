---
title: "[SOLVED] Internal Network Mapper"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-05-07
Is there such thing as an "Internal Network Mapper"?

We're having horrible problems with our network here in the office, and before I'm allowed to tear out the old networking and replace the switches and routers, the boss wants a diagram of the current internal network.

Is there a program in Linux that can sniff every node on the network and return a diagram? ASCII is acceptable (aka: no fancy effects are needed).

A very simple example would be:

```
					192.168.0.1
						|
						|
					192.168.0.100
						|
						|
		---------------------------------
		|				|				|
	192.168.0.101	192.168.0.102	192.168.0.103
						|
					192.168.0.104
```

---

### Post by silverbullet007 on 2007-05-07
Possibly something free like WhatsUp Gold could autodiscover.

---

### Post by altonbr on 2007-05-07
No Linux command-line binary though?

That's be great if it was UML-standard and implemented into OpenOffice.org Draw... but I must be dreaming.

---

### Post by altonbr on 2007-05-08
Sort of like a network diagnostics, or explorer program that can read all the nodes on your network. Does such a program exist?

---

### Post by altonbr on 2007-12-17
I found in Gutsy, a program based on Avahi called 'avahi-discover'. This gives me all the information I need :)

```
sudo aptitude install avahi-discover
```

---

