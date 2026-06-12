---
title: "4965agn won't connect to 'n' network"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by zackiv31 on 2008-05-06
I have a dual boot system (on an X61 tablet)... Vista and Hardy, 8.04.

In Vista, the system connects great to my new DLINK DGL-4500, at 300Mbps.

In Hardy... it fails to connect to the router.  Umm... what gives?  I've changed the setting to WPA2-Personal AES-CCMP ... which I believe is the same as in Vista/my router configuration.

Any information appreciated :)

If this is any help, ripped from log:
```

May  6 23:23:15 x61u kernel: [  349.095924] wlan0: Initial auth_alg=0
May  6 23:23:15 x61u kernel: [  349.095931] wlan0: authenticate with AP my:ma:ci:dm:ym:ac
May  6 23:23:15 x61u kernel: [  349.097701] wlan0: Initial auth_alg=0
May  6 23:23:15 x61u kernel: [  349.097705] wlan0: authenticate with AP my:ma:ci:dm:ym:ac
May  6 23:23:15 x61u kernel: [  349.097716] wlan0: RX authentication from my:ma:ci:dm:ym:ac (alg=0 transaction=2 status=0)
May  6 23:23:15 x61u kernel: [  349.097720] wlan0: authenticated
May  6 23:23:15 x61u kernel: [  349.097722] wlan0: associate with AP my:ma:ci:dm:ym:ac
May  6 23:23:15 x61u kernel: [  349.097733] wlan0: authentication frame received from my:ma:ci:dm:ym:ac, but not in authenticate state - ignored
May  6 23:23:15 x61u kernel: [  349.098287] wlan0: authentication frame received from my:ma:ci:dm:ym:ac, but not in authenticate state - ignored
May  6 23:23:15 x61u kernel: [  349.098795] wlan0: invalid aid value 0; bits 15:14 not set
May  6 23:23:15 x61u kernel: [  349.098800] wlan0: RX AssocResp from my:ma:ci:dm:ym:ac (capab=0x111 status=10 aid=0)
May  6 23:23:15 x61u kernel: [  349.098803] wlan0: AP denied association (code=10)
May  6 23:23:16 x61u kernel: [  349.296635] wlan0: associate with AP my:ma:ci:dm:ym:ac
May  6 23:23:16 x61u kernel: [  349.297285] wlan0: invalid aid value 0; bits 15:14 not set
May  6 23:23:16 x61u kernel: [  349.297291] wlan0: RX AssocResp from my:ma:ci:dm:ym:ac (capab=0x111 status=10 aid=0)
May  6 23:23:16 x61u kernel: [  349.297294] wlan0: AP denied association (code=10)
May  6 23:23:16 x61u kernel: [  349.494361] wlan0: associate with AP my:ma:ci:dm:ym:ac
May  6 23:23:16 x61u kernel: [  349.495170] wlan0: invalid aid value 0; bits 15:14 not set
May  6 23:23:16 x61u kernel: [  349.495179] wlan0: RX AssocResp from my:ma:ci:dm:ym:ac (capab=0x111 status=10 aid=0)
May  6 23:23:16 x61u kernel: [  349.495184] wlan0: AP denied association (code=10)
May  6 23:23:16 x61u kernel: [  349.694146] wlan0: association with AP my:ma:ci:dm:ym:ac timed out

```

---

