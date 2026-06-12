---
title: "Eth what?"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by Mark C on 2007-05-01
My PC is connected to 2 networks, one is for the internet, the other to another PC which shares the net connection with my PC.

The net connection is shared using firestarter, but every time I start up my PC, the eth number changes so that I have to set up firestarter to the eth number ubuntu chooses at boot. So at 1 time, the PC I share the net connection to becomes eth1 while at another it is eth2, is there a way to fix this problem so that I could give this network a permanent number, like eth1 perhaps? I never had the problem with eth0 though.

Can anybody help? Thank you!

---

### Post by Floppyjoe on 2007-05-01
Maybe edit your /etc/iftab file to assign the interfaces mac address with a permanent designation.
```
sudo gedit /etc/iftab
```

---

