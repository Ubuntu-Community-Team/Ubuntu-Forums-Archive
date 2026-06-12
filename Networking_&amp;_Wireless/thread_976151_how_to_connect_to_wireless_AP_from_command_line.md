---
title: "how to connect to wireless AP from command line?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by sailershen on 2008-11-09
In ubuntu 8.04, I can connect to wireless AP from GUI, may I connect to wireless AP from command line?

---

### Post by melojo on 2008-11-09
> **sailershen said:**
> In ubuntu 8.04, I can connect to wireless AP from GUI, may I connect to wireless AP from command line?

Thats how I connect to my router.

```
iwlist scan
```
Shows available networks

```
iwconfig wlan0 essid "belkin54g"
iwconfig wlan0 key xxxxxxx
iwconfig wlan0 key open
dhcpcd wlan0
```

---

### Post by nirab on 2011-06-15
or you could create a script .....

open a text editor and 
#! /bin/bash
iwconfig wlan0 essid <AP essid> key <psk for AP>
dhcpcd wlan0

i think by default the key is in hex and if you want to give an ascii key you would have to add "s:" prefix to it.

save the script and make it executable , now every time you need to connect to a particular acess point you just run its script :)

---

### Post by kriss3d on 2011-06-15
Im having a very similar problem. Only here i cant simply use a script which connects with a username and a password. I need somthing to pick up the login info from the user and use that to connect to a wifi network to authenticate the user against an AD server.

---

