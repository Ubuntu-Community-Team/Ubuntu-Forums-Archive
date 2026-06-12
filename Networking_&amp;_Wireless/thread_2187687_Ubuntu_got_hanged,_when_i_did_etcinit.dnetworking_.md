---
title: "Ubuntu got hanged, when i did /etc/init.d/networking restart"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2013-11-13
Hi All,
I was trying to do 
```

sudo ifconfig eth1 down
sudo ifconfig eth1 up

```

After this , i can see , interfcae is not properly UP. if i do ping, then error message is that, 

connect: Network is not reachable

```

sudo service network-manager restart

```

but the interface didn't come up.

when i did 
```

sudo /etc/init.d/networking restart

```

system got hanged. need a force reboot.

could you please help me on this?

---

