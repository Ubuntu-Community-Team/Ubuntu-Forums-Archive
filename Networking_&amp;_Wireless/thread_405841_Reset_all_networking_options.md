---
title: "Reset all networking options?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by thesheqq on 2007-04-10
I have been having issues trying to get my internet up and running on edgy eft.  I know it recognizes my Broadcom Nextreme 57xx Gigabit Controller, and I know I have the latest module for it Broadcom tg3.  I was wondering if there was anyway to reset all the settings so that it would be like it was after install, and go from there as I might have messed something up initially.

---

### Post by bnuytten on 2007-04-21
I am not away of any way to reset all network settings except maybe :twisted: remove /etc/network/interfaces :twisted: which I do not recommend. Can you describe your problem a little more or post output from the following commands:
```
cat /etc/network/interfaces
ifconfig
route -n

```

---

