---
title: "How to make a wireless access point?"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by nol1ght on 2008-02-02
I have cable internet connection and want to share it with my laptop wirelessly. but i cant find any info about how to transform my wireless adapter to wireless access point.... Ubuntu 64 7.10...

Plz... help, or give advice where to find. thx.

---

### Post by nol1ght on 2008-02-03
No one?

---

### Post by kegobeer on 2008-02-03
If you have a cable connection, why don't you buy a wireless router?

---

### Post by nol1ght on 2008-02-03
Best solution! thx you!
I have already adsl modem/router without wifi. But i have wifi integrated to my motherboard. So i whant to save some money.
If you cant help, why do you answer?

---

### Post by hahahan on 2008-02-03
Your wificard must support  "mode master" , not all cards do that.
Try: sudo iwconfig ethx mode master (ethx replaced by your nic)
And check if any of your other computers can see it.

Regards.

---

### Post by nol1ght on 2008-02-03
```
sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.

```

But on windows, i can configure my wireless adapter as access point, and share the internet....

Is it a driver problem?

---

### Post by hahahan on 2008-02-04
Yip, it seems that your Linux driver don't support master mode. Sorry for you.

Regards.

---

