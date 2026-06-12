---
title: "Huawei EC306-1 (MTS India) dongle not working in Ubuntu 14.04"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by ranjank on 2014-06-22
[COLOR=#282828][FONT=helvetica]My cousin bought MTS (India) MBlaze Ultra modem. Made by Huawei. Model is EC306-1 as per the package. Its not getting connected in Ubuntu 14.04. Here is lsusb output

[/FONT][/COLOR]
```
@JARVIS:~$ lsusb
Bus 002 Device 003: ID 0bda:5606 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[COLOR=#282828][FONT=helvetica]
Its not showing up in the add mobile broadband page in network settings. He tried with an old deactivated MTS dongle. Its getting connected. Any suggestions to fix this thing?[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-06-22
For starters, as usual, I suggest you ignore the brand/model - means nothing - and concentrate on looking up solutions for the real hardware inside: Huawei E1552/E????...
You may want to edit your thread's title in order to better attract the attention of those experts in HSPA/WCDMA USB modems.

---

### Post by ranjank on 2014-06-23
I have added lsusb output and model name mentioned in product package as suggested by Mr.[COLOR=#000000]Vladlenin5000. Any help is appreciated.[/COLOR]

---

### Post by Vladlenin5000 on 2014-06-23
Thank you.

```
ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)
```
is indeed what really matters. The weird thing is this a very common modem and already natively supported (should be at least) for some years now. Are you sure that specific modem isn't SIM locked and you're eventually trying it with a non-authorized SIM card?

---

### Post by ranjank on 2014-06-23
The modem is locked to MTS internet services. I haven't inserted any other SIM to it. Its in stock form.

---

