---
title: "non-functional wifi USB adapter Tenda model W311Mi"
date: 2023-01-20
forum: Networking &amp; Wireless
---

### Post by radimp on 2023-01-20
Hello there, 



Please could you help me with this issue.
I recently bought this wireless USB adapter Tenda model W311Mi. I need to use this USB adapter for
OS Linux Ubuntu 22.04 Debian version. My local seller advised me to download this driver for Linux users
on this website:
**[https://www.tendacn.com/us/download/detail-2646.html]("https://www.tenda.cz/article/tenda-w311mi-wireless-n-pico-usb-adapter")**


I managed to download and extract file for Linux environment however that was as far as I could get.
Then I came across your website here: **[https://www.tendacn.com/faq/3084.html](https://www.tendacn.com/faq/3084.html)**
But unfortunatelyfor me, I got stuck at the point where you advise clients to enter command in the terminal:
''sh install.sh''
This command does not work out for me at all and Terminal says:

**cannot open install.sh**

Would you be so kind and anyone please advise me what to do at this point?

---

### Post by MAFoElffen on 2023-01-21
To execute scripts...
```

chmod +x ./install.sh
sh ./install.sh

```

---

### Post by jeremy31 on 2023-01-21
With the adapter plugged in post results from terminal for
```
lsusb
```

Moved to Networking & Wireless

---

