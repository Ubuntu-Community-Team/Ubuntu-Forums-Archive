---
title: "How to modify the ip routing table permanently"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by DerridaIsDead on 2007-08-24
When I change the IP routing table in a terminal with the route  add command, I loose the new entry after reboot.
How to modify the IP routing table permanently?
Thanks in advance.

---

### Post by f00buntu on 2007-08-24
Method 1

You can make the route permanent by adding a small script to /etc/network/if-up.d/

```
#!/bin/sh
route add -net X.X.X.X netmask X.X.X.X gw X.X.X.X
```

Save the script as (for example): *staticroutes*

Make it executable:

```
chmod +x ./staticroutes
```


Method 2

Add an *up* command to your preferred network interface in /etc/network/interfaces:


```
auto eth0
iface eth0 inet dhcp
up route add -net X.X.X.X netmask X.X.X.X gw X.X.X.X
```

---

### Post by DerridaIsDead on 2007-08-24
Thanks for the reply.
I have tried both methods but still no new route in my IP routing table after reboot.

Can I not just add the 'route add' command in a login script? If yes, which script? 

Will the new route exist if I put it in /etc/bash.bashrc and for instance, after reboot, connect to the internet with the new network I added to the IP routing table?
Or will the new route only exist from within a bash shell?
...

---

### Post by netztier on 2007-08-24
> **DerridaIsDead said:**
> 
Can I not just add the 'route add' command in a login script? If yes, which script? 


No. Login scripts are made for setting up a user's own environment. Static routes is part of the system's environment and should not be based on a user's login - what if another user on your system would want to do the same, possibly even with a conflicting static route?

Are you sure that you got the right syntax for the route command in the shell script? Did you change the owner/group accordingly and gave it the right mode (executable) for that user?

Is the interface you need the static route for actually managed by /etc/network/interfaces (and not via network-manager?)

best regards

Marc

---

### Post by DerridaIsDead on 2007-08-24
For both trials, user and group were root and files are executable.
Method 1: added route in new file /etc/network/if-up.d/staticroutes 
Method 2: added up statement in /etc/network/interfaces (Did not change owner of file.)
Syntax seems correct.

> **netztier said:**
> 
Is the interface you need the static route for actually managed by /etc/network/interfaces (and not via network-manager?)
Marc
Uhm, how do I know if the interface is managed by /etc/network/interfaces or by the network-manager?

---

### Post by kevdog on 2007-08-24
wasted post

---

### Post by DerridaIsDead on 2007-08-27
Netztier, your were right.
I added the route the /etc/network/interfaces and now it works.
> **netztier said:**
> 
Are you sure that you got the right syntax for the route command in the shell script?

Actually, I didn't. I had "mask" instead of "netmask".
My apologies and thanks for the tip.

---

