---
title: "Networkslowing boot/start up."
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by pear-i on 2005-10-13
Just wondering for breezy is there a way to change the priority on which devices are loaded -- cause right now when i boot up my laptop it waits at the waiting for networking devices for a while before moving on..

then when gdm finally rolls along and i login i have to  wait a whilst more just so the silly little networking icons are loaded and setup

---

### Post by adwait on 2005-10-13
I think you can use this:
```
sudo rcconf
```

This will let you edit all the services that are started at start up, so you can turn them off if you want.

---

### Post by trubblemaker on 2006-01-25
you can also edit /etc/networking/interfaces

remove your eth0 entries from this file, it will really speed up your boot time but your wired card won't get an ip and you'll have to use Network Manager, or ifconfig to bring the card up later.  If your on a laptop it's probably using wireless card. 

this really helped me I hope it helps you.

Cheers

Matt

---

