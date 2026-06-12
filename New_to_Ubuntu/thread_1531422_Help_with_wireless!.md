---
title: "Help with wireless!"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Francis0 on 2010-07-15
I have a dell xps m1530 with vista and i recently installed the newest ubuntu, everything seemed fine except my wireless does not work. i have read many other posts about wireless not working, but its very confusing. could someone please guide me through fixing this?

---

### Post by TheBarbee on 2010-07-15
be sure and check the simplest things first. i know it may seem obvious but check it anyway. Whenever i install a fresh ubuntu i always have wireless issues but usually it's that somehow my wifi got disabled or something like that. right click your networking icon and make sure wireless is enabled and also if your comp. has a hardware way to turn it on make sure you do that too

---

### Post by mikewhatever on 2010-07-15
This is most likely the driver problem. In case you have a Broadcom card, the driver is not included by default and must be downloaded and installed. If possible, hook up an ethernet cable, the open System->Admin->Hardware-Drivers.

---

### Post by mapes12 on 2010-07-15
Applications>Accessories>Terminal ```
sudo lshw -C network

```and post the output back here.

---

### Post by widda on 2010-07-16
what wireless modem? is it recognised at all? 
Or, what message do you get?

---

