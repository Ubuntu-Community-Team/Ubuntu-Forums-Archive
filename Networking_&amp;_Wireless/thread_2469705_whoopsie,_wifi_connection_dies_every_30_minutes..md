---
title: "whoopsie, wifi connection dies every 30 minutes."
date: 2021-12-07
forum: Networking &amp; Wireless
---

### Post by Kevitivity on 2021-12-07
My wifi connection dies about every 30 minutes. Connection status icon changes to (?), and the following shows up in syslog...

```
ec  6 23:06:12 Neuron whoopsie[1470]: [23:06:12] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/8
Dec  6 23:06:12 Neuron whoopsie[1470]: [23:06:12] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/8
Dec  6 23:06:12 Neuron whoopsie[1470]: [23:06:12] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/8
Dec  6 23:06:12 Neuron systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec  6 23:06:12 Neuron dbus-daemon[817]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  6 23:06:12 Neuron systemd[1]: Started Network Manager Script Dispatcher Service.
Dec  6 23:06:13 Neuron whoopsie[1470]: [23:06:13] online
```

DISTRIB_DESCRIPTION="Ubuntu 20.04.3 LTS"

wifi dongle uses a 88x2bu chip. Using latest driver from : [https://github.com/cilynx/rtl88x2bu](https://github.com/cilynx/rtl88x2bu)

---

### Post by morrownr on 2021-12-19
Here is a more recent driver that is well maintained and has good documentation to include sections that help you troubleshoot:

[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

---

### Post by Kevitivity on 2022-02-21
Thank you very much! Your driver seems to be performing better. I also appreciate your documentation informing me of the advantage of in-kernel drivers. Ordered a Mediatek dongle.

---

### Post by bertoo on 2022-02-21
The top two here seem to be more active:
[https://github.com/search?q=rtl88x2bu](https://github.com/search?q=rtl88x2bu)

tbh ,i don't know too much about the rincat one ,haven't used it ,but cilynx is the one i see mentioned the most as good for recent kernels.
I've used it with good results on LInuxLite with 5.16 kernel (upgraded myself from earlier kernel).
Though morrownr is great too if it matches your system needs ,seems to be just as active atmo ,(as of Feb.2022).

---

