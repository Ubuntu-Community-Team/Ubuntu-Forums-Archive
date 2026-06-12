---
title: "could not resolve 'localhost'"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by lynx shadow on 2008-08-10
i can get through the internet on my dual-boot laptop (i have win xp and ubuntu gutsy gibbon), but when i try to update some files, i get the message 'could not resolve "localhost"'.

i have '127.0.0.1 localhost' in my /etc/hosts file. i tried '127.0.0.1 localhost:4001' but still got the same message.

i'm not sure i have a file /etc/networks/interfaces

what can i do? please HELP!
:cry:

---

### Post by cariboo on 2008-08-10
What are you trying to do? Is your computer named 4001? your /etc/localhost should look something like this:

```
127.0.0.1	localhost
127.0.1.1	intrepid
```

In your case replace intrepid with your hostname. I you don't know what your host name is, in a terminal type:

```
hostname
```

To see the contents of your /etc/network/interfacces etiher navigate to it from nautilus, double click on File System then double click /etc then network, then double click interfaces, or the fast way , open a terminal and type:

```
cat /etc/network/interfaces
```

It should show you something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

Jim

---

