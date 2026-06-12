---
title: "Wireless setup"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by pcostanza on 2007-03-06
I have a small network that someone helped set up and has both wired and wireless computers. However, when I look for the password to setup wireless, I have none, only the very long key.
How can I set up wireless using the key only and not the paraphrase? I don't see how I can get past not having an actual key.
I suppose I could change my wireless key to a paraphrase on the router but then I'd have to go back and change all the others on the network which I'd rather not do.:confused:

---

### Post by pcostanza on 2007-03-06
Sorry for posting twice.  I was having trouble getting my first message posted and obviously sent it twice.

Apologies
:guitar:

---

### Post by chili555 on 2007-03-06
Is your encryption WEP or WPA?

---

### Post by pcostanza on 2007-03-06
WEP-128 bits.

---

### Post by chili555 on 2007-03-06
Then the 26-character key is exactly what you want. sudo gedit /etc/network/interfaces to make the relevant interface entry look like this:```
auto wlan0 
iface wlan0 inet dhcp
wireless-key 93c8530b2df51711bad5596f91  <(whatever your key is)
```
Your interface may be eth1, ath0 or ra0, etc.

Here is more information: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

---

