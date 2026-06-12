---
title: "network works only when plugged in on startup"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by AlmaTlust on 2007-03-15
Hi,
I'm new to Ubuntu (switched from Suse). I installed Edgy on my laptop which I use in several networks. But I can only access networks when the cable is plugged in during bootup. When not and I plug it in later, it doesn't work. If I go into system settings/network properties and change something, the network settings are reloaded and then it works.
What can I do?
Thank you in advance,
Martin

---

### Post by gradedcheese on 2007-03-15
You can switch to NetworkManager (search the forums for a how-to), which will detect the cable and set things up automatically so it will work like you want it to.

---

### Post by madmaik on 2007-03-15
Actually I think this is the expected behaviour.
I do not know whether there is a solution for ubuntu to get notified when a network cable is plugged in and then bringing up that interface.
You could instead of needing to open the network configurator create a link on your desktop or somewhere else where it executes the command
```
sudo /etc/init.d/networking restart
```

Just an idea


rgds,
   MaDMaik

---

