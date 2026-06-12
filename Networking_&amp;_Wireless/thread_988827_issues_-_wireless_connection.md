---
title: "issues - wireless connection"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by sved on 2008-11-20
Hi

Someone help me whats going wrong wid my wireless connection.

everytime when i boot to my comp (fresh) (I have installed ubuntu 8.10) the wireless connection icon i the tray indicates that its connected.
When i right click on the icon and select connection information it displays all the information correct along with an IP address obtained from my router.

However when i try to ping the router it fails - zero packets received. hence obviously when i try t oaccess interenet through mozilla no joy.

then i have to left click on the icon and click on hte wireless connection once again to re-establish the connection. after this happens i am able to access interenet.

Why does this happen. why am i not able to access interenet the moment i log in to my computer though it says that connection to the router is established.


anybody......



thanks

---

### Post by iponeverything on 2008-11-20
Check to see if you have any firewall rules that are getting in the way:

```
sudo iptables -L -n
```

---

### Post by gusto5 on 2008-11-21
I have the same problem. Killing networkmanager through terminal then restarting it, will allow it to reconnect to the router. Eventually it will once again fail to work.

etc/network/interfaces only contains this

```
auto lo
iface lo inet loopback
```

Im at a loss. I read 'something' about 2.6.27-7 kernel and iwl3945, though i am not sure what to make of it.

---

### Post by superprash2003 on 2008-11-21
try switchin to static ip , that may help

---

