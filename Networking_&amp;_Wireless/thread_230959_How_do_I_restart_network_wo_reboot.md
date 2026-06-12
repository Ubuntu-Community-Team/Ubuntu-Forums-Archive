---
title: "How do I restart network w/o reboot?"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by plexi50 on 2006-08-06
Sometimes, the only way to get network manager to work is with a reboot. Is there a clean way to restart the network from the command line without a complete reboot?

---

### Post by stormblue on 2006-08-06
you could always do an 

```
sudo ifconfig <interface> down
sudo ifconfig <interface> up
```

like so:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up

```

---

### Post by Sam Lars on 2006-08-07
Another option is
```
sudo /etc/init.d/networking restart
```

---

### Post by plexi50 on 2006-08-07
Thanks for you help. I wish I could figure out a way to make network manager work the same way everytime, maybe with the next version

---

