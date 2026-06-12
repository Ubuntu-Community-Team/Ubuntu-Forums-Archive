---
title: "finding wireless networks"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by pallaziol on 2009-05-29
installed Ubuntu 9.04 on one laptop, and absolutley delights. Connection to wireless internet was a breeze. But now I'm at the same location, and I've installed the same Ubuntu disc onto another laptop. Installation was complete, but for some reason this time the Ubuntu Networks manager cannot find any of the wireless networks. They don't even show up. The original laptop is connected fine, and both computers connected easily while using Windows XP. Identical Dell Vostro laptops running the same Windows and the same Ubunto. The only difference is that on this second laptop I am trying to keep Windows, whereas on the first computor I deleted Windows during the Ubunto install. What Can I do to let the new laptop find the wireless networks that are here?

---

### Post by DGortze380 on 2009-05-29
> **pallaziol said:**
> installed Ubuntu 9.04 on one laptop, and absolutley delights. Connection to wireless internet was a breeze. But now I'm at the same location, and I've installed the same Ubuntu disc onto another laptop. Installation was complete, but for some reason this time the Ubuntu Networks manager cannot find any of the wireless networks. They don't even show up. The original laptop is connected fine, and both computers connected easily while using Windows XP. Identical Dell Vostro laptops running the same Windows and the same Ubunto. The only difference is that on this second laptop I am trying to keep Windows, whereas on the first computor I deleted Windows during the Ubunto install. What Can I do to let the new laptop find the wireless networks that are here?

Probably a driver issue, please open a terminal (Applications -> Accessories -> Terminal) and post the output of

```

lspci

```

---

### Post by pallaziol on 2009-05-29
I would love to but since I can't connect to the internet on that computer I can post that output, which is quite large. Can you give me a hint as to what I'm supposed to look for? (I'm borrowing someone elses laptop to post these threads)

---

### Post by x33a on 2009-05-29
do both the laptops have the same wireless card?

lspci will list the pci devices attached to your laptop, and with this we can identify the wireless card you have.

also post the output of
```
iwconfig
iwlist scan
```

---

### Post by pallaziol on 2009-05-29
So, is there anyone that can help me here, or is it not possible to find a wireless network with Ubuntu on a machine that also has Windows XP?

---

### Post by pallaziol on 2009-05-30
yes, both laptops were configured identically. The only difference is that Windows was removed from the first when Ubunto was installed, and on the second one I wanted to leave Windows on it. The only difference.

---

### Post by pallaziol on 2009-05-30
By the way, when I jump back to Windows XP, the wireless connection and network locator works perfectly

---

### Post by shizumasa14 on 2009-05-30
What type of wireless card do you have?

---

### Post by DGortze380 on 2009-05-30
we need the output of the above 3 commands to help you.

---

### Post by juancarlospaco on 2009-05-30
Try propietary drivers :(

---

