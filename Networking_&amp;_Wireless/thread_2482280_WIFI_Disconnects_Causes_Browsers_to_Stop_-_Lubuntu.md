---
title: "WIFI Disconnects Causes Browsers to Stop? - Lubuntu 22.04"
date: 2022-12-26
forum: Networking &amp; Wireless
---

### Post by mcman56 on 2022-12-26
I have been having browser lock ups with Lubuntu 22.04 on a Chromebook.  This started when I changed from chrome to Lubuntu.  Sometimes reloading the browser corrects and sometimes a reboot is necessary.  I have tried multiple version of Linux and multiple browsers.  I have even tried a different WIFI router.  I do not see anything in the logs about memory issues but do see WIFI issues such as shown below.  I do not understand what it is saying.  Could this be some kind of driver issue?  How could I correct?

Samsung Chromebook 3 (Intel Celeron N3050, Braswell dual core @ 1.6GHz, Memory: 2GB, Wi-Fi: 802.11ac dual band (2.4GHz, 5GHz) 
    

[COLOR=#000000]02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)[/COLOR]


12/26/22 7:12 PM    kernel    ---[ end trace 7f909eaa57787714 ]---
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: iwlwifi transaction failed, dumping registers
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: iwlwifi device config registers:
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000040: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000060: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000080: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 000000a0: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 000000c0: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 000000e0: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000100: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000120: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000140: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: iwlwifi device memory mapped registers:
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: iwlwifi parent port (0000:00:1c.2) config registers:
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000000: 22cc8086 00100507 06040021 00810010 00000000 00000000 00020200 200000f0
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000020: 91209120 0001fff1 00000000 00000000 00000000 00000040 00000000 001303ff
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000040: 01428010 00008000 00100000 03323c11 50110042 0014b200 01080000 00000008
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000060: 00000000 00000817 00000000 00000000 00010001 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000080: 00019005 fee01004 00000025 00000000 0000a00d 72708086 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000000a0: c8030001 00000008 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000000c0: 00000000 00000000 00000000 00000000 01000000 00000842 0911c000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000000e0: 00000300 88aa88aa 00000007 00000000 00000050 0c000040 042d0f1c 03000004
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000100: 20000000 00000000 00000000 00060011 00000000 00002000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000140: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000160: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000180: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000001a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000001c0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 000001e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
12/26/22 7:12 PM    kernel    iwlwifi 0000:00:1c.2: 00000200: 0001001e 0028281f 6003281f
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Queue 11 is active on fifo 2 and stuck for 10000 ms. SW [60, 73] HW [90, 90] FH TRB=0x05a5a5a5a
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:12 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:13 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    systemd-timesyncd    Timed out waiting for reply from 185.125.190.56:123 (ntp.ubuntu.com).
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    systemd-timesyncd    Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    systemd-timesyncd    Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    systemd-timesyncd    Timed out waiting for reply from 185.125.190.58:123 (ntp.ubuntu.com).
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:14 PM    systemd-timesyncd    Timed out waiting for reply from 185.125.190.57:123 (ntp.ubuntu.com).
12/26/22 7:14 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:15 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5
12/26/22 7:15 PM    systemd-resolved    Grace period over, resuming full feature set (UDP+EDNS0) for DNS server 192.168.1.1.
12/26/22 7:15 PM    kernel    iwlwifi 0000:02:00.0: Error sending STATISTICS_CMD: enqueue_hcmd failed: -5

---

