---
title: "wireless was disabled"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by rhuea on 2009-01-17
hi guys, i just updated my intrepid ibex and found out that my wireless network was disabled. now i cannot detect any wireless connections. i checked the networking icon and there was no wireless connection, only the wired network. what should i do to recover my wireless connections. many thanks in advance.

---

### Post by overdrank on 2009-01-17
> **rhuea said:**
> hi guys, i just updated my intrepid ibex and found out that my wireless network was disabled. now i cannot detect any wireless connections. i checked the networking icon and there was no wireless connection, only the wired network. what should i do to recover my wireless connections. many thanks in advance.

Hi and I would suggest identifying the wireless adapter and then searching for solutions. :)

---

### Post by rhuea on 2009-01-17
How can i do your suggested solution? oh, and i cannot use any headsets or external speakers either. this all happened after i updated.

---

### Post by stevoo on 2009-01-17
Most probably your Hardware Connections were dissabled. 

Check in System->Administration->Hardware Drivers

Is there anything there ?

---

### Post by mjheagle8 on 2009-01-17
what kind of wireless card do you have?

---

### Post by rhuea on 2009-01-17
there was nothing on the hardware drivers. my card is 802.11b/g WLAN

---

### Post by mjheagle8 on 2009-01-17
what make and model?
can you please post the output of 
```
lshw
```and```
lspci
```

---

### Post by rhuea on 2009-01-17
Hi guys, after a while of searching i was finally able to find out what happened. i have already recovered my wireless connection. it involves what mjheagle8's suggestion. Thanks to all of you. now all that is left is to actually try it again on a wireless network.

---

