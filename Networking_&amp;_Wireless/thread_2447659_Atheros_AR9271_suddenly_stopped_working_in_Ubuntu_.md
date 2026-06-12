---
title: "Atheros AR9271 suddenly stopped working in Ubuntu 16.04"
date: 2020-07-23
forum: Networking &amp; Wireless
---

### Post by FrenchyFungus on 2020-07-23
Hi,

WiFi on our desktop has suddenly stopped working. It uses an Atheros AR9271 USB dongle, which shows up when lsusb is run, but no networks are visible in network-manager. There is also no "Enable wireless" option in network-manager. The dongle works fine in other computers.

Everything is up-to-date, as far as I can tell.

Any advice?

Link to wireless-info: [https://pastebin.com/PB0Acf6T](https://pastebin.com/PB0Acf6T)

Thanks.

---

### Post by praseodym on 2020-07-24
Why is ndiswrapper installed?
```

sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Reboot

---

### Post by FrenchyFungus on 2020-07-24
Thanks - I have no recollection of why ndiswrapper was installed.

Upgrading to 18.04 fixed whatever the issue was, and I have removed ndiswrapper now anyway.

---

