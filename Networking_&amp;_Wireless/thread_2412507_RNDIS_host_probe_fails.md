---
title: "RNDIS host probe fails"
date: 2019-02-13
forum: Networking &amp; Wireless
---

### Post by daniel.hung on 2019-02-13
Hi All,

[COLOR=#000000][FONT=Arial]Does any one know the root cause of RNDIS host probe failure as below?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The log shows error -110 which is ETIMEDOUT. The possibility of this issue is around 2% during a continuous reboot test.

[/FONT][/COLOR]
Jan 31 00:01:31 ubuntu-arm kernel: [   10.268591] cdc_acm 2-1:1.2: ttyACM0: USB ACM device
Jan 31 00:01:31 ubuntu-arm kernel: [   10.286122] usbcore: registered new interface driver cdc_acm
Jan 31 00:01:31 ubuntu-arm kernel: [   10.286147] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters

Jan 31 00:01:31 ubuntu-arm kernel: [   10.296177] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.323928] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.353893] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.383910] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.413914] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.443907] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.473898] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.503965] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.533912] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.563954] rndis_host 2-1:1.0: rndis media connect
Jan 31 00:01:31 ubuntu-arm kernel: [   10.593721] rndis_host 2-1:1.0: RNDIS_MSG_QUERY(0x01010101) failed, -110
Jan 31 00:01:31 ubuntu-arm kernel: [   10.605622] rndis_host 2-1:1.0: rndis get ethaddr, -110
Jan 31 00:01:31 ubuntu-arm kernel: [   10.641589] rndis_host: probe of 2-1:1.0 failed with error -110
Jan 31 00:01:31 ubuntu-arm kernel: [   10.653730] usbcore: registered new interface driver rndis_host
[COLOR=#000000][FONT=Arial]
I find it can be recovered by reset modem. In other words, the connection will be OK after reloading RNDIS driver.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]It looks like a timing issue between USB device (modem card) & RNDIS host?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Best regards,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Charles[/FONT][/COLOR]

---

