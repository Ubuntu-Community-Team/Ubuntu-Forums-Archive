---
title: "Wireless Connection no longer Available"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Merk42 on 2008-03-08
There were some problems with my wireless connection. I could connect to the router, but the router couldn't get on the Internet.  I was troubleshooting both the software connection and the hardware involved. I tried reconnecting to the wireless signal and even putting it on Enable Roaming.  Eventually the problem was fixed with a simple restart of the modem and router.  However, now the option for wireless is no longer shown in Network Connections.  The wireless does work, as I'm using the same hardware in Windows right now to post this message.

I'm using a WUSB54GSC USB wireless nub, and had to go through some long walkthough on the SomethingAwful forums to get it to work in the first place.

---

### Post by 1010011010 on 2008-03-08
What drivers were you using?  Ndiswrapper, madwifi, or something else?

---

### Post by Merk42 on 2008-03-08
Ndiswrapper, I'll see if I can find the long tutorial I followed

---

### Post by 1010011010 on 2008-03-08
Did you

```
sudo modprobe ndiswrapper
```

---

### Post by Merk42 on 2008-03-08
That did it, thank you.

---

