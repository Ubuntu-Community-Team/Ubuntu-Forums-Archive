---
title: "Modify network adapter protocols"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by matt_b on 2007-04-10
Hi all,

I wish to remove TCP/IP binding from my eth0 network adapter to isolate my ubuntu host from the internet whilst still allowing vmware server to bridge to it, to give my virtual machines internet access.

Can someone point me in the right direction? I assume there's a config file somewhere that requires some commenting.

Thanks
matt_b

---

### Post by dbott67 on 2007-04-10
I'm not sure if this is what you're looking for, but the protocols & settings are stored in the /etc/network/interfaces file:

```

dbott@feisty:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 [COLOR=Red]**inet**[/COLOR] dhcp
```Just replace [COLOR=Red]**inet**[/COLOR] with[COLOR=Red] **ipx** [/COLOR]or [COLOR=Red]**inet6 **[/COLOR]or whatever protocol you desire.

From [COLOR=Red]man interfaces[/COLOR]:
> 
Stanzas defining logical interfaces start with a line consisting of the word  "iface" followed by the name of the logical interface.  In simple configurations without mapping stanzas this name should simply  be  the name  of  the  physical  interface  to which it is to be applied.  (The default mapping script is, in effect, the echo command.)  The interface name  is  followed by the name of the address family that the interface uses.  This will be "inet" for TCP/IP networking,  but  there  is  also some support for IPX networking ("ipx"), and IPv6 networking ("inet6").

Following that is the name of the method used to configure  the  interface.-Dave

---

### Post by matt_b on 2007-04-11
Fantastic, thanks for your help!

---

