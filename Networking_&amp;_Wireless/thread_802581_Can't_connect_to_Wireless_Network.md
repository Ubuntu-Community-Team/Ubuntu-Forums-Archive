---
title: "Can't connect to Wireless Network"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by AllFallD0wn on 2008-05-21
Hi. I just installed the latest version of Ubuntu (8.04, I believe) in dual-boot mode on my Acer Aspire 5100 model. I'm having a problem connecting to my wireless network, I have tried typing the name of the network and password, but no luck.

Any advice?

Thanks.

---

### Post by AllFallD0wn on 2008-05-22
Any help?


Also, any help will have to be in 'noob form', as I'm new to this kinda stuff.

---

### Post by Peter09 on 2008-05-22
Open a terminal by

Applications->Accessories->terminal

type in the following and paste the output into the thread.

```
ifconfig
```

PC

---

### Post by AllFallD0wn on 2008-05-22
Ok. I've done that and took a screen shot.

It appears to not be detecting the network adapter which i have in the laptop (not sure who makes it, but I've read something about the acer aspire 5100 model. It simply says "802.11b/g wireless lan" on the laptop sticker with all the specs.


[http://img89.imageshack.us/my.php?image=screenshotnr8.png](http://img89.imageshack.us/my.php?image=screenshotnr8.png)

---

### Post by Peter09 on 2008-05-22
I believe that the only way forward is to use ndiswrapper and the windows drivers.

Might be worth a search on the forums for the method.

PC

---

### Post by AllFallD0wn on 2008-05-22
Is there a simple step-to-step guide that doesn't involve having internet acccess on linux while doing it?

Thanks.

---

### Post by Ayuthia on 2008-05-22
> **AllFallD0wn said:**
> Is there a simple step-to-step guide that doesn't involve having internet acccess on linux while doing it?

Thanks.
Can you post your lspci -nn (from the Terminal)?  It will help us identify your wireless card and point you in a direction.

---

