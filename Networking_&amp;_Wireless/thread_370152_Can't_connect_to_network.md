---
title: "Can't connect to network"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by alex_anthony on 2007-02-25
I'm trying to connect to my home network
I have my wireless working fine on windows (dual boot) and wired works fine on ubuntu
On a Dell Inspiron 1300 with the typical broadcom card
i eventually had success installing my driver with ndiswrapper
for some reason now i can't seem to find my network properly
Wifi Radar manages to see the network but can't acquire the IP address
No other program seems to be finding the network

note iwconfig sees my interface as eth1 (not wlan0) - not sure if this is important

---

### Post by solar george on 2007-02-25
Is the network encrypted? If so, how?

---

### Post by alex_anthony on 2007-02-25
Wep

---

### Post by solar george on 2007-02-25
If it is your network try unencrypting it temporarily and try to connect again.

---

### Post by alex_anthony on 2007-02-25
can't quite remember how... can you jog my memory? ubuntu or windows?

---

### Post by solar george on 2007-02-25
OK ignore that,

Try using the default network manager, in the system menu.f

You will have to type in the network name (essid) and the WEP (network password)

---

### Post by alex_anthony on 2007-02-25
have already tried that...
doesn't work
i'll try taking off the encryption tomorrow

---

