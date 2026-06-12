---
title: "Mouse Pointer &amp; Text Cursor Lags Then Wifi/Network Disconnects"
date: 2024-10-05
forum: Networking &amp; Wireless
---

### Post by wyattwhiteeagle on 2024-10-05
Lubuntu 24.04
Acer Aspire E1-532

What do I need to do in order to find out why this happens and how to correct and prevent it?

Everything seems normal then after 20 to 30 minutes or so, it happens.
Rebooting seems to correct and then the lags and disconnects happen at about 20 to 30 minutes or so after reboot.

This didn't happen on 22.04.

---

### Post by &amp;KyT$0P# on 2024-10-06
Does
```
journalctl -b
```
show any related messages around the time this happens?

---

### Post by wyattwhiteeagle on 2024-10-07
> **halogen2 said:**
> Does
```
journalctl -b
```
show any related messages around the time this happens?
That's a quite lengthy output.
I see dates and times, I can narrow it down to an "around that time".
I reinstalled fresh, I'll gather that info the next time it happens.
If using this in a script, is there a way to have the date and time when the info is gathered into the output text file?
And since rebooting seems to temporarily correct, is there a way to show info from the previous session?

Anyway, here's some of the output from a file I saved before re-installing fresh...

```


Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179027.3081] platform-linux: event-notification: RTM_NEWLINK, flags 0, seq 0: ignore
Oct 05 21:43:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:43:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179027.3140] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: no (plain property)
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179027.3141] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: no
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179027.3141] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: scanning-state: idle (notify last-scan)
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179027.3143] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: don't scan (rate limited for another 0.199 sec after previous scan)
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179027.3143] device[475d094c2e0d08f6] (wlp2s0): add_pending_action (2): 'autoactivate'
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179027.3143] device[475d094c2e0d08f6] (wlp2s0): remove_pending_action (1): 'wifi-scan'
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179027.3144] device[475d094c2e0d08f6] (wlp2s0): remove_pending_action (0): 'autoactivate'
Oct 05 21:43:47 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:43:47 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179027.5137] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: don't scan (periodic scan waiting for another 113.497 sec, schedule timeout)
Oct 05 21:43:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:43:51 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:43:52 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:43:52 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:43:53 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:43:53 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:43:53 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:43:58 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:43:58 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:43:58 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:02 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:02 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:02 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:04 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:04 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:04 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:09 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:10 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:10 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:12 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:12 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:12 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:15 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:15 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:15 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:20 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:20 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:20 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:22 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:22 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:22 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:26 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:26 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:26 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:31 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:32 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:32 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:32 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:34 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:34 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:35 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:35 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:35 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:36 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:36 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:36 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:37 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:38 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:38 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:38 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:39 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:39 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:39 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:42 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:42 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:42 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:48 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:48 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:49 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:50 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:50 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:53 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:54 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:54 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:44:59 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:44:59 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:44:59 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:00 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:00 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:00 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:01 wyatt-aspiree1532 CRON[6830]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 05 21:45:01 wyatt-aspiree1532 CRON[6831]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 05 21:45:01 wyatt-aspiree1532 CRON[6830]: pam_unix(cron:session): session closed for user root
Oct 05 21:45:04 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:04 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:04 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:10 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:10 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:10 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:15 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:16 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:16 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:20 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:20 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:20 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:21 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:21 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:21 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:27 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:27 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:27 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:30 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:31 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:31 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:32 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:33 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:33 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:37 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:38 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:38 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:41 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:41 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:41 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179142.0664] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: start periodic scan (0 SSIDs to probe scan)
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.0665] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: periodic scan starting (next scan is scheduled in 120.000 sec)
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.0666] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: request-scan: request scanning (0 ssids)...
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179142.0668] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: scanning-state: scanning
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179142.0668] device[475d094c2e0d08f6] (wlp2s0): add_pending_action (1): 'wifi-scan'
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.0669] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: don't scan (has scan_request_cancellable)
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.0692] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: request-scan: request scanning success
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.0693] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: scan request completed (D-Bus request)
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.4505] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: yes (plain property)
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.4506] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: yes
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:42 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179142.6349] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: scan request completed (after extra delay)
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:42 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:43 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:45 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:46 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:47 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179148.5490] platform-linux: event-notification: RTM_NEWLINK, flags 0, seq 0: ignore
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179148.5548] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: no (plain property)
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179148.5549] sup-iface[3d2f793ba0ab1281,0,wlp2s0]: scanning: no
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179148.5549] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: scanning-state: idle (notify last-scan)
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179148.5551] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: don't scan (rate limited for another 0.200 sec after previous scan)
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179148.5551] device[475d094c2e0d08f6] (wlp2s0): add_pending_action (2): 'autoactivate'
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179148.5551] device[475d094c2e0d08f6] (wlp2s0): remove_pending_action (1): 'wifi-scan'
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <debug> [1728179148.5552] device[475d094c2e0d08f6] (wlp2s0): remove_pending_action (0): 'autoactivate'
Oct 05 21:45:48 wyatt-aspiree1532 NetworkManager[714]: <trace> [1728179148.7555] device[475d094c2e0d08f6] (wlp2s0): wifi-scan: kickoff: don't scan (periodic scan waiting for another 113.311 sec, schedule timeout)
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:49 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:49 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:49 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:51 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:51 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:51 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:54 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:45:55 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:45:55 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:45:59 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:00 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:00 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:01 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:02 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:02 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:03 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:03 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:03 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:04 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:05 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:06 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:06 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:07 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:07 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:07 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:08 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:08 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:11 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:11 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:11 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:16 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:17 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:17 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:17 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:18 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:18 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:22 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:22 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:22 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:27 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:27 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:27 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:28 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:28 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:28 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:33 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:33 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:33 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:38 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:38 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:38 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:38 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:39 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:39 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:44 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:44 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:44 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:48 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:48 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:48 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:49 wyatt-aspiree1532 kernel: ath: phy0: Failed to wakeup in 500us
Oct 05 21:46:49 wyatt-aspiree1532 kernel: ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
Oct 05 21:46:49 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 05 21:46:52 wyatt-aspiree1532 sudo[6866]:    wyatt : TTY=pts/0 ; PWD=/home/wyatt ; USER=root ; COMMAND=/usr/bin/journalctl
Oct 05 21:46:52 wyatt-aspiree1532 sudo[6866]: pam_unix(sudo:session): session opened for user root(uid=0) by wyatt(uid=1000)

```

---

### Post by wyattwhiteeagle on 2024-10-07
[COLOR=#000000]If using ```
journalctl -b
``` in a script, is there a way to have the date and time of when the "info-script" is ran and have it inserted into the output text file?[/COLOR]

It just happened again.
This is a basic portion of the output.
Let me know if you need more.
UbuntuForums mentioned a security issue when trying to post the full report
```


Oct 07 11:07:14 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: WPA: Group rekeying completed with fc:2b:b2:73:9d:83 [GTK=CCMP]
Oct 07 11:10:03 wyatt-aspiree1532 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
Oct 07 11:10:03 wyatt-aspiree1532 systemd[1]: sysstat-collect.service: Deactivated successfully.
Oct 07 11:10:03 wyatt-aspiree1532 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
Oct 07 11:15:01 wyatt-aspiree1532 CRON[14453]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 07 11:15:01 wyatt-aspiree1532 CRON[14454]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 07 11:15:01 wyatt-aspiree1532 CRON[14453]: pam_unix(cron:session): session closed for user root
Oct 07 11:17:01 wyatt-aspiree1532 CRON[14497]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 07 11:17:01 wyatt-aspiree1532 CRON[14498]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Oct 07 11:17:01 wyatt-aspiree1532 CRON[14497]: pam_unix(cron:session): session closed for user root
Oct 07 11:20:03 wyatt-aspiree1532 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
Oct 07 11:20:03 wyatt-aspiree1532 systemd[1]: sysstat-collect.service: Deactivated successfully.
Oct 07 11:20:03 wyatt-aspiree1532 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
Oct 07 11:25:01 wyatt-aspiree1532 CRON[14721]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 07 11:25:01 wyatt-aspiree1532 CRON[14722]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 07 11:25:01 wyatt-aspiree1532 CRON[14721]: pam_unix(cron:session): session closed for user root
Oct 07 11:30:00 wyatt-aspiree1532 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
Oct 07 11:30:00 wyatt-aspiree1532 systemd[1]: sysstat-collect.service: Deactivated successfully.
Oct 07 11:30:00 wyatt-aspiree1532 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
Oct 07 11:30:01 wyatt-aspiree1532 CRON[14854]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 07 11:30:01 wyatt-aspiree1532 CRON[14855]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Oct 07 11:30:01 wyatt-aspiree1532 CRON[14854]: pam_unix(cron:session): session closed for user root
Oct 07 11:31:45 wyatt-aspiree1532 systemd[1]: Started anacron.service - Run anacron jobs.
Oct 07 11:31:45 wyatt-aspiree1532 anacron[14879]: Anacron 2.3 started on 2024-10-07
Oct 07 11:31:45 wyatt-aspiree1532 anacron[14879]: Normal exit (0 jobs run)
Oct 07 11:31:45 wyatt-aspiree1532 systemd[1]: anacron.service: Deactivated successfully.
Oct 07 11:35:01 wyatt-aspiree1532 CRON[14964]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Oct 07 11:35:01 wyatt-aspiree1532 CRON[14965]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 07 11:35:01 wyatt-aspiree1532 CRON[14964]: pam_unix(cron:session): session closed for user root
Oct 07 11:40:03 wyatt-aspiree1532 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
Oct 07 11:40:03 wyatt-aspiree1532 systemd[1]: sysstat-collect.service: Deactivated successfully.
Oct 07 11:40:03 wyatt-aspiree1532 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
Oct 07 11:40:48 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: CTRL-EVENT-BEACON-LOSS
Oct 07 11:40:49 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:40:50 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=fc:2b:b2:73:9d:83 reason=4 locally_generated=1
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:40:50 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:40:50 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
```

---

### Post by wyattwhiteeagle on 2024-10-07
[COLOR=#000000]If using [/COLOR]```
[COLOR=#000000][FONT=&amp]journalctl -b[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp] in a script, is there a way to have the date and time of when the "info-script" is ran and have it inserted into the output text file?[/FONT][/COLOR][COLOR=#000000]
[/COLOR]
How do I proceed?
I looked more closely at the output.
It looks like what is happening is in this little bit of the report.
```
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <warn>  [1728315666.1485] device (wlp2s0): link timed out.
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1501] device (wlp2s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1506] manager: NetworkManager state is now DISCONNECTED
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <warn>  [1728315666.1510] device (wlp2s0): Activation: failed for connection 'WIN_201145'
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1562] device (wlp2s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Oct 07 11:41:06 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: Reject scan trigger since one is already pending
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Withdrawing address record for fe80::ba52:3c3e:3393:f9d0 on wlp2s0.
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1578] dhcp4 (wlp2s0): canceled DHCP transaction
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::ba52:3c3e:3393:f9d0.
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1578] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
Oct 07 11:41:06 wyatt-aspiree1532 dbus-daemon[651]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.14' (uid=0 pid=735 comm="/usr/sbin/NetworkManager --no-daemon" label="unconfined")
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1578] dhcp4 (wlp2s0): state changed no lease
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Withdrawing address record for 192.168.254.66 on wlp2s0.
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.254.66.
Oct 07 11:41:06 wyatt-aspiree1532 avahi-daemon[647]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Oct 07 11:41:06 wyatt-aspiree1532 systemd-resolved[578]: wlp2s0: Bus client reset search domain list.
Oct 07 11:41:06 wyatt-aspiree1532 systemd-resolved[578]: wlp2s0: Bus client set default route setting: no
Oct 07 11:41:06 wyatt-aspiree1532 systemd-resolved[578]: wlp2s0: Bus client reset DNS server list.
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:41:06 wyatt-aspiree1532 systemd[1]: Starting NetworkManager-dispatcher.service - Network Manager Script Dispatcher Service...
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Unable to reset channel, reset status -22
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Oct 07 11:41:06 wyatt-aspiree1532 kernel: ath: phy0: Chip reset failed
```

---

### Post by wyattwhiteeagle on 2024-10-07
just a hunch here...
The device named 'lo' may be a device not inside my house.
Specific things in my neighborhood is pointing to one neighbor on one side of me having set up an access point for another neighbor on the other side of me and my pc detecting that device.
I need to find out if anyone inside my four walls has this 'lo' device.

Any suggestions on dealing with a neighbor's device trying to use my computer or my internet to "boost" a connection to the other neighbors access point?

I'm not on communication terms with these two neighbors due to certain happenings in the past.
I don't know if it's like this everywhere, but here where I live..."internet jumping" is actually illegal.
So these 2 neighbors aren't gonna be willing to talk to "others", including me, about anything illegal that they may have going on.

---

### Post by &amp;KyT$0P# on 2024-10-07
Not sure how much more I can help here, but if I were troubleshooting this I would investigate those [FONT=monospace]kernel: ath: phy0[/FONT] messages.  Do you recall if you had those in 22.04 (or can you find out from a backup of /var/log/syslog from your old 22.04 install)?  Do you see them in a live USB of 22.04 that didn't previously have this issue?

Are you able to try a different kernel version?

> **wyattwhiteeagle said:**
> The device named 'lo' may be a device not inside my house.

The [FONT=monospace]lo[/FONT] network interface is the **lo**opback interface, it's a virtual interface the OS uses to network only with itself internally (e.g. sending requests for DNS lookups to [FONT=monospace]systemd-resolved[/FONT]).  It's a normal part of an Ubuntu system and has nothing to do with Wi-Fi.

> **wyattwhiteeagle said:**
> [COLOR=#000000]If using [/COLOR]```
[COLOR=#000000][FONT=&amp]journalctl -b[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp] in a script, is there a way to have the date and time of when the "info-script" is ran and have it inserted into the output text file?[/FONT][/COLOR]

If using bash, something like this -
```
echo "
Script ran at: $(date)" >> [COLOR="#FF0000"]THE_OUTPUT_FILE[/COLOR]
```
replace [COLOR="#FF0000"]THE_OUTPUT_FILE[/COLOR] with however you're referencing the output file in your script

---

### Post by wyattwhiteeagle on 2024-10-08
> **halogen2 said:**
> Not sure how much more I can help here, but if I were troubleshooting this I would investigate those kernel: ath: phy0 messages.
Do you recall if you had those in 22.04 (or can you find out from a backup of /var/log/syslog from your old 22.04 install)?
Thank you
I'll check and see if I can find any of those, but that's a good idea.


> **halogen2 said:**
> Do you see them in a live USB of 22.04 that didn't previously have this issue?
I no longer have my 22.04 Live USB.
I don't believe I saved the iso file for it, and I've ovewritten the usb key with 24.04.


> **halogen2 said:**
> Are you able to try a different kernel version?
Do you mean Xubuntu or something not *buntu based?


> **halogen2 said:**
> The lo network interface is the loopback interface, it's a virtual interface the OS uses to network only with itself internally (e.g. sending requests for DNS lookups to systemd-resolved). It's a normal part of an Ubuntu system and has nothing to do with Wi-Fi.


Ok, so 'lo' isn't something outside of my living quarters.


> **halogen2 said:**
> If using bash, something like this -
```
echo "
Script ran at: $(date)" >> THE_OUTPUT_FILE
```
replace THE_OUTPUT_FILE with however you're referencing the output file in your script


Thank you
Will come in handy.


So what about the part of the report which say's, "device (wlp2s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')"
What, ssid not found?
I feel like this needs to be corrected.
In that same report it says this is going to happen at every hour if not more frequent.
```
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1501] device (wlp2s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1506] manager: NetworkManager state is now DISCONNECTED
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <warn>  [1728315666.1510] device (wlp2s0): Activation: failed for connection 'WIN_201145'
Oct 07 11:41:06 wyatt-aspiree1532 NetworkManager[735]: <info>  [1728315666.1562] device (wlp2s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Oct 07 11:41:06 wyatt-aspiree1532 wpa_supplicant[740]: wlp2s0: Reject scan trigger since one is already pending
```

---

### Post by &amp;KyT$0P# on 2024-10-08
> **wyattwhiteeagle said:**
> Do you mean Xubuntu or something not *buntu based?

I mean [this]("https://packages.ubuntu.com/noble-updates/linux-generic").  22.04 comes with 5.15.x kernel series (unless you were using the HWE kernels), 24.04 comes with 6.8.x kernel series.

You can see your current kernel version if you run
```
uname -a
```

> what about the part of the report which say's, "device (wlp2s0): state change: activated -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')"
What, ssid not found?
I feel like this needs to be corrected.

That message is relevant but unlikely to be pointing at the problem.  To me your journalctl messages looks like NetworkManager is trying to scan for the SSID but can't due to a lower level issue.

---

### Post by wyattwhiteeagle on 2024-10-08
> **halogen2 said:**
> I mean this. 22.04 comes with 5.15.x kernel series (unless you were using the HWE kernels), 24.04 comes with 6.8.x kernel series.


[https://packages.ubuntu.com/noble-updates/linux-generic](https://packages.ubuntu.com/noble-updates/linux-generic)
That's completely new to me.
Look's like I'm coming in very late.
I don't know how to use any of those.
Any suggestions?


> **halogen2 said:**
> You can see your current kernel version if you run
```
uname -a
```
```
Linux wyatt-aspiree1532 6.8.0-45-generic #45-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug 30 12:02:04 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```


> **halogen2 said:**
> That message is relevant but unlikely to be pointing at the problem. To me your journalctl messages looks like NetworkManager is trying to scan for the SSID but can't due to a lower level issue.
Relevant indeed and though not pointing at the problem, most likely it points to other clue's.
That relevant message give's one or more clue's.
Though some may not be an actual clue, it gives a list as a starting point.


1. device (wlp2s0):
2. state change: activated -> failed
3. reason 'ssid-not-found'
4. sys-iface-state: 'managed'


What all can cause the ssid to not be found?

---

### Post by wyattwhiteeagle on 2024-10-19
```
kernel: ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
```
 
This is a suspected bug in arch linux and a similar bug was reported for previous *buntu's.
Could this be a bug in Lubuntu 24.04?


Bug in arch linux
[https://bbs.archlinux.org/viewtopic.php?id=276110](https://bbs.archlinux.org/viewtopic.php?id=276110)


Similar bug in previous *buntu
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171)

---

### Post by wyattwhiteeagle on 2024-11-19
***UPDATE***

This has led to other threads being started...

Re:
[https://ubuntuforums.org/showthread.php?t=2502561](https://ubuntuforums.org/showthread.php?t=2502561) (most recent in Hardware Forum)
[https://ubuntuforums.org/showthread.php?t=2502489](https://ubuntuforums.org/showthread.php?t=2502489)

---

