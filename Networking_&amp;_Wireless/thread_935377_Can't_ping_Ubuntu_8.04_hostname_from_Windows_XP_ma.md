---
title: "Can't ping Ubuntu 8.04 hostname from Windows XP machine"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by jgambleii on 2008-10-01
Hello everyone,

I have an Ubuntu 8.04 machine (clean install) with all current updates. I can ping my Windows hostname in Ubuntu without an issue. I cannot however, ping my Ubuntu hostname in Windows (I can ping its IP though). The Ubuntu machine is getting an IP via DHCP, as is the Windows machine. They are on the same subnet. The Windows machine is attached to an AD domain, but the Ubuntu machine is not. 

I know this has been asked before, but I'm not able to get a clear answer. What do I have to do to be able to ping my Ubuntu machine, via its hostname in Windows?

Thanks,

jgambleii

---

### Post by Iowan on 2008-10-01
Something to try...
Edit **/etc/dhcp3/dhclient.conf** - find the line```
send host-name "<hostname>";

```If it is commented out (starts with #), uncomment it (delete the #) and insert your hostname in place of <hostname>.  Restart networking with **/etc/init.d/networking restart**
If that doesn't help, installing **winbind** might.

---

