---
title: "running diagnostics on atheros card"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by miesnerd on 2009-03-02
from the output, lspci, i got:
05:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


So that's my hardware. Recently, its been really hard to connect to wifi. In my house, right now, im connected, but i have to be RIGHT BY the router. If im 2 rooms over, i cant connect, even though the signal is 70%. It used to not be this way. How do I go about checking to see if everything is correct?

---

### Post by sandyd on 2009-03-02
> **miesnerd said:**
> from the output, lspci, i got:
05:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


So that's my hardware. Recently, its been really hard to connect to wifi. In my house, right now, im connected, but i have to be RIGHT BY the router. If im 2 rooms over, i cant connect, even though the signal is 70%. It used to not be this way. How do I go about checking to see if everything is correct?

have you tried lowering the bitrate in /etc/rc.local ?

lots of people having connection problems because ubuntu runs the card at the highest bitrate which makes the signal go a little funky

---

### Post by sandyd on 2009-03-02
```

sudo iwconfig

```
shoud tell you connection properties

---

### Post by miesnerd on 2009-03-02
> **carlee said:**
> ```

sudo iwconfig

```
shoud tell you connection properties

hey thanks for your help so far. I dont know anything about lowering the bitrate. Also, i did iwconfig. It doesnt show ath0, but shows wifi0, so clearly there's some problem there, but I forgot how I've dealt with that in the past. Do i have to modprobe something?

---

