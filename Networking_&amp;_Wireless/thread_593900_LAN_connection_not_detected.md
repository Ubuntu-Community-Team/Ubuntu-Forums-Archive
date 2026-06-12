---
title: "LAN connection not detected"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by eekfonky on 2007-10-27
I have just installed ubuntu on a friends computer, however it's not connecting to the PCI LAN card.
I know the card works as it ran under Windows. Please help me get this computer online

The vendor is:
Hangzhou Silan Microelectronics co.

The message in 'Hardware Information' is:
Device unknown (0x2031)

Any ideas?

---

### Post by scrooge_74 on 2007-10-27
You need to give more details on the brand of card he is using

---

### Post by eekfonky on 2007-10-27
sorry that's all I know - I didn't have time to take the cover off and look. Is there a reason ubuntu couldn't find a driver?

---

### Post by scrooge_74 on 2007-10-27
Depends on the type of card, if the card is not supported there will be problems, if the card needs proprietary drivers you need to install  those (if available)

---

### Post by Lambert on 2007-10-27
Open a terminal and run the following commands. Post the output here.

```

sudo lspci -nn

sudo lshw -C network

```

This should give information about the device so you can get more help.

---

### Post by eekfonky on 2007-10-27
Thanks I'll do that ASAP - my friend is 50 miles away and I'll be visiting in the next day or so. Failing that I could always buy a new one they're cheap. What would you recommend?

---

