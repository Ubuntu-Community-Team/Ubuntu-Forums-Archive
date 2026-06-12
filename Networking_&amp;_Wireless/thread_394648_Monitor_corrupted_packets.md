---
title: "Monitor corrupted packets"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by supersan on 2007-03-27
I would like to know if exists a tool that is able to monitor the corrupted packet in a wireless network...packets that are discarded by the link layer!!!
I think that the only possibility is to change the driver of the wireless card in order to avoid the CRC...but if you one simpler mechanism please let me know.
Ciao

---

### Post by supersan on 2007-03-29
If you do not know any other solution...could you tell me how to change the driver of my wireless card in order to avoid the checksum of corrupted packets???

Please!!!

---

### Post by bkeithly on 2007-03-29
you could try to monitor with 

tcpdump

It is a great tool!

you can try to use alternate drivers with 

ndiswrapper.

There are tons of docs on it around here.

---

### Post by Mr. C. on 2007-03-29
For packets discarded at the lnk layer, tcpdump nor the ndiswrapper will ever see them.

The A/P or card driver would have to modified.

MrC

---

