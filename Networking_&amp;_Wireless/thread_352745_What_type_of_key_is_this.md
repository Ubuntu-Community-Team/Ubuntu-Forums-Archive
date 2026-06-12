---
title: "What type of key is this?"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by quirt3 on 2007-02-03
I have a key for a closed ntwrok. Iknow it isn't WEP 128 bit passphrase,any type of WPA key, or a WEP hew code. It's made up of 5 numbers....any ideas???

---

### Post by StFS on 2007-02-04
It's most likely a 40 bit ASCII key (a wep passphrase).

Some more info could help, such as where are you trying to enter this key? 

In KNetworkManager for example, you need to specify WEP 40/104-bit ASCII type in your key and select Shared Key in the "Authentication" drop down box.

In iwconfig, you'd use something like: iwconfig eth1 key s:12345

---

### Post by quirt3 on 2007-02-05
Using the gnome-panel applet.

---

### Post by spd106 on 2007-02-05
If you could open a terminal and type **sudo iwlist eth1 scan**, then post the output along with the essid/name of the network you are trying to connect to.

---

