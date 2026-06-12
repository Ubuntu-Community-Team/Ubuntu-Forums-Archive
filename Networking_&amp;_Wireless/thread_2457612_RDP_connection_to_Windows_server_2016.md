---
title: "RDP connection to Windows server 2016?"
date: 2021-02-05
forum: Networking &amp; Wireless
---

### Post by caraway on 2021-02-05
Fresh install of Ubuntu 20.10 on a raspi.

Trying to make a remote desktop connection to a Windows system using Remmina does not succeed in even the first stages of connecting/authentication. Tried all options (RDP, NLA, SSH).

No solutions found in various forums. Is this hopeless?

---

### Post by QIII on 2021-02-05
Hello.

" ... does not succeed in even the first stages of connecting/authentication." is a bit lacking in detail.

Can you explain exactly what *does* happen?  Images can be invaluable in cases like this.

---

### Post by caraway on 2021-02-06
Update: Remmina relies on FreeRDP for RDP connections. Tried xfreerdp which also fails.

---

### Post by caraway on 2021-02-11
Further research reveals that Windows RDP changed to using udp in 2018, requiring substantial changes in FreeRDP, which so far haven't been implemented, see [https://github.com/FreeRDP/FreeRDP/issues/4978](https://github.com/FreeRDP/FreeRDP/issues/4978)

---

