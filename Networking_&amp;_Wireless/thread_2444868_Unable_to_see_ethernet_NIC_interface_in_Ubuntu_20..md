---
title: "Unable to see ethernet NIC interface in Ubuntu 20.04 even though NIC is present and h"
date: 2020-06-05
forum: Networking &amp; Wireless
---

### Post by midnightengineer on 2020-06-05
[COLOR=#242729][FONT=Arial]I am unable to see my ethernet card ports in the OS (Ubuntu 20.04) by doing ***ip a***. I can see the card in ***lspci*** and also under ***lshw***. I know (from BIOS menu) that a port in the Card is also connected.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How do I see the network interface actually link up in the OS? Is this a bug with Ubuntu? I have physically verified that the Port on the card is up and blinking.

[ATTACH=CONFIG]286099[/ATTACH]

[ATTACH=CONFIG]286100[/ATTACH]

---

### Post by slickymaster on 2020-06-05
Thread moved to **Networking & Wireless** for a better fit

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by chili555 on 2020-06-05
Please run and post:

```
lspci -nnk | grep 0200 -A3
sudo modprobe tg3
dmesg | grep tg3
```

---

