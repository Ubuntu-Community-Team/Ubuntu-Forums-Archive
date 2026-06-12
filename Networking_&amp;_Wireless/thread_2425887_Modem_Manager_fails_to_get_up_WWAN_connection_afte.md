---
title: "Modem Manager fails to get up WWAN connection after update to 18.04"
date: 2019-09-01
forum: Networking &amp; Wireless
---

### Post by rienesl on 2019-09-01
Hi,
Yesterday I upgraded from 14.04 to 16.04 and after that immediately to 18.04. Now I have the problem, that my WWAN connection is not working any more. The provider is shown and the connections as well, but when I try to connect, it tells me [Preparing mobile broadband connection "Metphone"...], but nothing happens.

journalctl -u NetworkManager
pulls out the following:
 ```

Sep 01 20:45:27 HP700 NetworkManager[767]: <info>  [1567345527.3141] device (cdc-wdm0): Activation: starting connection 'Metfone' (b09d1abb-c3a7-4bc4-855c-65de03e0d590)
Sep 01 20:45:27 HP700 NetworkManager[767]: <info>  [1567345527.3185] audit: op="connection-activate" uuid="b09d1abb-c3a7-4bc4-855c-65de03e0d590" name="Metfone" pid=1362 uid=1000 result="success"
Sep 01 20:45:27 HP700 NetworkManager[767]: <info>  [1567345527.3228] device (cdc-wdm0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Sep 01 20:45:27 HP700 NetworkManager[767]: <info>  [1567345527.3307] manager: NetworkManager state is now CONNECTING
Sep 01 20:45:27 HP700 NetworkManager[767]: <info>  [1567345527.3721] modem["cdc-wdm0"]: modem state changed, 'registered' --> 'connecting' (reason: user-requested)
Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.2815] modem["cdc-wdm0"]: modem state changed, 'connecting' --> 'connected' (reason: user-requested)
[B]Sep 01 20:45:29 HP700 NetworkManager[767]: <warn>  [1567345529.2970] modem-broadband[cdc-wdm0]: failed to connect modem: invalid bearer IP configuration
[/B]Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.2972] device (cdc-wdm0): state change: prepare -> failed (reason 'config-failed', sys-iface-state: 'managed')
Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.2986] manager: NetworkManager state is now DISCONNECTED
**Sep 01 20:45:29 HP700 NetworkManager[767]: <warn>  [1567345529.3011] device (cdc-wdm0): Activation: failed for connection 'Metfone'**
Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.3302] device (cdc-wdm0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.3803] modem["cdc-wdm0"]: modem state changed, 'connected' --> 'disconnecting' (reason: user-requested)
Sep 01 20:45:29 HP700 NetworkManager[767]: <info>  [1567345529.3973] modem["cdc-wdm0"]: modem state changed, 'disconnecting' --> 'registered' (reason: user-requested)

```

Unfortunately Google pulls out nothing useful at all. Anybody any idea where to start?

---

### Post by rienesl on 2019-09-02
Tried to revert to 14.04 (using disk image backup) -> now the modem is deactivated. This is a well known issue for the Compaq Mini 700, you must have WindowsXP and the special HP software to activate the modem. Once it is activated, you can use it under Linux as well, but due to I don't have XP any more, this is now a devastating situation. Due to the hopeless situation under 14.04 I went back to 18.04 now (using disk image backup again), but I'm still not able to get the modem work (same error messages). Anybody out there, who has a glimpse what to do to make the WWAN come up?
By the way: this is what the modem tells me using ati
```

Manufacturer: QUALCOMM INCORPORATED
Model: 88
Revision: D1020-SUUAASFA-4352  1
IMEI: 35235402347XXXX
+GCAP: +CGSM,+DS,+ES
```
(In fact it uses a Qualcomm MDM1000 chipset, sold from HP as Gobi un2400)

---

### Post by mörgæs on 2019-09-02
Have you considered a clean install of 18.04.3 without using the back-ups?

---

### Post by rienesl on 2019-09-02
It was more or less by accident, that I stumbled across the Bug #1592514. This bug was created and confirmed more than 3 years ago, but it isn't solved yet. In short: If you have an IPv4 only provider, you will not be able to get the connection up using Modem Manager or Network Manager by any means. The only way is a workaround with a script, which has to be run on elevated rights.
In my case it works with those modifications:
```

#!/bin/bash
mmcli -m 0 -b 0 --connect
ifconfig wwan0 up
mmcli -m 0 -b 0
dhclient -d wwan0 &
echo "nameserver 8.8.8.8" >> /etc/resolv.conf

```

---

