---
title: "problem with wirelless connection"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Chefarov on 2007-07-03
Hello all. I am connecting to internet wirelessly through a router. I have just installed Ubuntu 7.04 and I can't connect to the router. I installed the wireless card's drivers (which were for windows) using ndiswrapper. After that when I am going to administration-windows wireless drivers, it appears : Hardware present: No. What does it mean? Linux doesn't recognise the card? Why since I have installed the drivers?

---

### Post by spd106 on 2007-07-03
Could you please open a terminal and post here the output of this command
```
sudo lshw -class network
```

It should list the interface and which driver it is currently using. If it says unclaimed then you might want to try this command.
```
sudo modprobe ndiswrapper
```

If it still doesn't work then try looking for another driver on the ndiswrapper website.

---

