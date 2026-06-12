---
title: "[SOLVED] Roaming Wireless Connects to Wrong Network"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by lvleph on 2008-02-21
I know this had to have been answered some where, but I cannot find it. I am looking for the config file that saves all networks one has previously connected to, so that I can delete one specific network that my computer connects to all the time. I am using gnome and networkmanager. Can someone give me a clue?

---

### Post by renzokuken on 2008-02-21
do you mean /etc/network/interfaces    ?

---

### Post by lvleph on 2008-02-21
> **renzokuken said:**
> do you mean /etc/network/interfaces    ?
That was the first thing I thought of, but no go.
**interfaces**
```
auto lo
iface lo inet loopback
```

---

### Post by lvleph on 2008-02-21
I figured out a slow way to fix it.
Open up terminal
```
gconf-editor
```
Then when you are in gconf-editor
system>>networking>>wireless>networks
Here you will see a list of network; click the one you want to get rid of and then unset all the keys related to it in the panel on the left. Close gconf-editor and Bob's Your Uncle.

---

