---
title: "How do I find out what wireless network card I have installed?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by janvanmansum on 2008-08-10
Hello group,

I have an Acer Aspire 5100 laptop with a wireless network card. Ubuntu somehow didn't detect it during installation. Now I can't find the documentation of this laptop anymore so I don't know what the exact type of wireless network card is that I have. I have been googling but I can't seem to find anything. Any idea how to find this information?

Thanks for any help,
regards,

Jan van Mansum.

---

### Post by rizitis on 2008-08-10
give to the terminal ```
lspci
```
you will find all  cards there.
"network controller" is your wirelless card.

---

### Post by janvanmansum on 2008-08-10
Thanks! Actually I had not looked wel and Ubuntu did show the name in the window with hardware with limited supported drivers. But this command is useful to remember anyway. Thanks again!

---

