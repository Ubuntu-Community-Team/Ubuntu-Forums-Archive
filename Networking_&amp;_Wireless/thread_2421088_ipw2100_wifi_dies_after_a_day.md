---
title: "ipw2100 wifi dies after a day"
date: 2019-06-16
forum: Networking &amp; Wireless
---

### Post by axet2 on 2019-06-16
Hello! I have M3N old notebook with:

01:04.0 Network controller: Intel Corporation PRO/Wireless LAN **2100** 3B Mini PCI Adapter (rev 04)

After a day I got no wifi and have to reboot the machine. dmesg saying:


```
_event_max_sample_rate to 50500
[  854.831374] ipw2100: Fatal interrupt. Scheduling firmware restart.
[11369.911655] perf: interrupt took too long (4943 > 4936), lowering kernel.perf_event_max_sample_rate to 40250
[11414.173675] ipw2100: Fatal interrupt. Scheduling firmware restart.
[12674.408121] ipw2100: Fatal interrupt. Scheduling firmware restart.
[12696.356501] IPv6: ADDRCONF(NETDEV_UP): wlp1s4: link is not ready
[12714.775024] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s4: link becomes ready
[42894.542004] PM: suspend entry (deep)
...

[60361.664075] ipw2100: exit - failed to send CARD_DISABLE command
[60361.664091] ipw2100: exit - failed to send CARD_DISABLE command
[60998.447665] ipw2100: Fatal interrupt. Scheduling firmware restart.
[64162.784086] INFO: task wpa_supplicant:670 blocked for more than 120 seconds.
[64162.784097]       Tainted: G S       C  E    4.15.0-51-generic #55-Ubuntu
[64162.784100] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[64162.784103] wpa_supplicant  D    0   670      1 0x00000000
[64162.784108] Call Trace:
[64162.784125]  __schedule+0x295/0x8d0
[64162.784129]  schedule+0x26/0x70
[64162.784132]  schedule_preempt_disabled+0xd/0x10
...
[64189.132057] ipw2100: wlp1s4: Firmware did not initialize.
[64189.132061] ipw2100: wlp1s4: Failed to start the firmware.

```


Full dmesg at [https://pastebin.com/tsy94Whm](https://pastebin.com/tsy94Whm)

---

