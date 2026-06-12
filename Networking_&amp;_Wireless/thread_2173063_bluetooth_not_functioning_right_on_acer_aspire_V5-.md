---
title: "bluetooth not functioning right on acer aspire V5-131"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by brandon11 on 2013-09-07
I have an Acer Aspire V5-131 with built-in bluetooth but when i try to pair with a device it does not register.
i have tried multiple bluetooth apps with many different devices but nothing worked. can anyone help me?
i am using Ubuntu 12.04

---

### Post by tgalati4 on 2013-09-07
Open a terminal and post the following:

```
lsusb
lspci
```

---

### Post by brandon11 on 2013-09-07
> **tgalati4 said:**
> Open a terminal and post the following:

```
lsusb
lspci
```
what would i be looking for?

---

### Post by joaomfsantos on 2014-03-29
What worked for me (same laptop - thank you slickymaster):
[INDENT]
[LIST=1]
[*]First of all, check that your wireless devices are unlocked (no rfkill active): Code:
sudo rfkill list

[*]In case bluetooth is 'Soft blocked' you can unblock it: Code:
sudo rfkill unblock all
[/LIST]
[/INDENT]

---

