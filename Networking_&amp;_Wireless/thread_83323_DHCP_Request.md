---
title: "DHCP Request"
date: 2005-10-28
forum: Networking &amp; Wireless
---

### Post by lexor on 2005-10-28
I was looking at the system logs and noticed that it is asking the DHCP on the server fo a IP every 5mins on port 67.

The DHCP that I access gives a lease for 2 days so why does the system keep asking for a IP from the DHCP. 

Should this not just happen on system reoot or If i reconfig the network card ? 

Its not a major problem I could set it to a static IP if I wish, the question is just purely out of interest.

---

### Post by Kyral on 2005-10-28
This...might be normal..I dunno. Mind if I check my own logs when I get home and get back to you?

---

### Post by mlomker on 2005-10-28
My home DHCP server did until I changed the lease period because the default was crazy short.  If you are sure that it is 2 days then that shouldn't be happening.

---

### Post by lexor on 2005-10-29
Its the o/s system thats asking the DHCP server the DHCP server will only give out a IP if its asked to do so I am sure.

I set it to static myself as I only have 2 clients and 1 server, but if I had a bigger network then I reckon it would be something to look more into.

---

### Post by finnjimm on 2005-10-29
On my Kubuntu 5.10 dhclient makes a request every 30 seconds or so.

My /var/log/daemon is full of this, over and over again:

```
Oct 29 22:14:27 localhost dhclient: DHCPREQUEST on eth0 to 192.168.10.1 port 67
Oct 29 22:14:27 localhost dhclient: DHCPACK from 192.168.10.1
Oct 29 22:14:27 localhost dhclient: can't create /var/run/dhclient.eth0.leases: Permission denied
Oct 29 22:14:27 localhost dhclient: bound to 192.168.10.64 -- renewal in 25 seconds.
```

The network works fine, but I guess there's something wrong with my dhclient anyway?

---

### Post by mlomker on 2005-10-29
[QUOTE=finnjimm]The network works fine, but I guess there's something wrong with my dhclient anyway?[/QUOTE]

Did you run it with **sudo**?

---

### Post by finnjimm on 2005-10-29
[QUOTE=mlomker]Did you run it with **sudo**?[/QUOTE]
I haven't touched it (knowingly), it's running there how the installer left it.

---

### Post by mlomker on 2005-10-29
[QUOTE=finnjimm]I haven't touched it (knowingly), it's running there how the installer left it.[/QUOTE]

That log indicates that there's something wrong with the permissions of the file that the lease information is saved to.  I'd **sudo dhclient eth0** and see if you get the same result.  You might have to find a way to delete that file if that doesn't resolve it.

---

### Post by finnjimm on 2005-10-29
Running **sudo dhclient eth0** outputs

```
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.10.1
```

Removing (renaming) the /var/run/dhclient.eth0.leases doesn't help. The dhclient3, started during boot, is owned by user "dhcp".

This wouldn't be such a PITA if it did not occur every 30 seconds.

---

