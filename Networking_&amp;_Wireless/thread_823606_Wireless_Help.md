---
title: "Wireless Help"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by mychem54321 on 2008-06-09
I have a built in wireless card and when i had windows it worked, it connected me to the wireless router in my house, but i formated my entire comp and installed ubuntu 7.10 gutsy and now it won't connect wirelessly, it will only connect when i connect it to the ethernet cord. how do i get the wireless to work???

---

### Post by rlzyoner on 2008-06-09
You may find this post helpful

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by superprash2003 on 2008-06-09
check to see if you can install any restricted drivers under System->administration->Restricted drivers (or hardware drivers)

---

### Post by Ayuthia on 2008-06-09
> **mychem54321 said:**
> I have a built in wireless card and when i had windows it worked, it connected me to the wireless router in my house, but i formated my entire comp and installed ubuntu 7.10 gutsy and now it won't connect wirelessly, it will only connect when i connect it to the ethernet cord. how do i get the wireless to work???
Can you go to the Terminal and post the results to:
```
lspci -nn
lshw -C network
```It will list out your PCI cards so that we can tell what card you have.  The second one will help us see what driver your network card is using.

---

