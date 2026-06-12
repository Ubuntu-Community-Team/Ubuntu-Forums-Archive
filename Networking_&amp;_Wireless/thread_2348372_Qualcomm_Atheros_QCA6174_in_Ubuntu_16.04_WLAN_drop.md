---
title: "Qualcomm Atheros QCA6174 in Ubuntu 16.04 WLAN drops randomly"
date: 2017-01-03
forum: Networking &amp; Wireless
---

### Post by litu-litu on 2017-01-03
Hi,

I hope this isn't a duplicate, but I couldn't find a solution anywhere. WLAN drops randomly every hour but WiFi remains connected. In order to get it up again I need to restart the network-manager. My computer is an Acer Aspire V5-591G.

I've tried Kvalo's, [COLOR=#000000][FONT=&amp]FireWalkerX's and a few more ath10k firmwares to no avail.

In attachments you can find the output of the wireless info script.[/FONT][/COLOR][COLOR=#000000]

I'm still rather new to linux, so if I'm missing something let me know!!

Thanks!![/COLOR]

---

### Post by praseodym on 2017-01-03
Lets try deactivating the power management:
```

sudo iwconfig wlp7s0 power off
```

---

### Post by litu-litu on 2017-01-03
I've tried that but the problem persists. The connection dropped less than 30 minutes after I deactivated the power management.

---

### Post by jeremy31 on 2017-01-03
Check ```
iwconfig
```
See if power management hasn't turned back on

---

### Post by litu-litu on 2017-01-04
It did turned itself back on, but I forced it off writing "0" to the /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf file.

Eventually, the connection dropped again.

---

### Post by jeremy31 on 2017-01-09
You need to write 2 to the /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf file to really disable it

See [this answer](http://unix.stackexchange.com/a/330929/102332)

I have seen the source code this is true

---

### Post by litu-litu on 2017-01-10
I did as you said, but the connection keeps dropping. =/

---

### Post by geeksmith on 2017-01-13
Are you sure the problem is on your client? It could be an issue with your access point. Are there other stations on your SSID having issues? Do you own the AP and have you tried rebooting it?

You might also try the suggestions in this sticky post: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by litu-litu on 2017-01-13
I have a dual boot with Windows and it never dropped the connection.

I've tried everything from that post, but nothing worked so far.

---

### Post by geeksmith on 2017-01-13
There are 7 access points within range on channel 1, and your access point is one of them. Switch to any 5GHz channel ASAP. If that's not an option, then try channel 6 (not as bad as 1), channel 11 (almost as bad as 1). You're going to continue to see drops and performance issues in your current setup regardless of what you do on your client.

Windows might not see drops, so the Windows driver must be handling chip resets and problems more effectively.

---

### Post by geeksmith on 2017-01-13
The 2 red lines from your kernel logs indicate:
1. Possible driver bug. It appears to have recovered on its own, at least for a little while.
2. Your client is not happy with this BSS -- very likely due to the interference from other access points.

```
[ 1537.001259] wlp7s0: AP <MAC 'FossaDeiLeoni' [AC1]> changed bandwidth, new config is 2412 MHz, width 2 (2422/0 MHz)
[COLOR="#FF0000"][ 1537.076068] ath10k_pci 0000:07:00.0: firmware crashed! (uuid 0d514f40-5e14-4f4e-b9f6-2fa52a8f3ab5)[/COLOR]
[ 1537.076093] ath10k_pci 0000:07:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[ 1537.076101] ath10k_pci 0000:07:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 1537.077571] ath10k_pci 0000:07:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[ 1537.078258] ath10k_pci 0000:07:00.0: board_file api 2 bmi_id N/A crc32 6fc88fe7
[ 1537.078265] ath10k_pci 0000:07:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[ 1537.080327] ath10k_pci 0000:07:00.0: firmware register dump:
[ 1537.080333] ath10k_pci 0000:07:00.0: [00]: 0x05030000 0x000015B3 0x009860FA 0x00955B31
[ 1537.080339] ath10k_pci 0000:07:00.0: [04]: 0x009860FA 0x00060730 0x00000004 0x0040E8A0
[ 1537.080344] ath10k_pci 0000:07:00.0: [08]: 0x00498110 0x00955A00 0x0000000B 0x00400000
[ 1537.080350] ath10k_pci 0000:07:00.0: [12]: 0x00000009 0x00000000 0x00952CD0 0x00952CE6
[ 1537.080355] ath10k_pci 0000:07:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x0091080D
[ 1537.080360] ath10k_pci 0000:07:00.0: [20]: 0x409860FA 0x0040E7E8 0x00000000 0x0041E0DC
[ 1537.080365] ath10k_pci 0000:07:00.0: [24]: 0x800B5A1D 0x0040E848 0x000FFFFF 0xC09860FA
[ 1537.080370] ath10k_pci 0000:07:00.0: [28]: 0x809B3230 0x0040E948 0x00000018 0x004313B8
[ 1537.080376] ath10k_pci 0000:07:00.0: [32]: 0x809B2992 0x0040E998 0x0040E9C0 0x00429548
[ 1537.080381] ath10k_pci 0000:07:00.0: [36]: 0x8091D252 0x0040E9B8 0x00000000 0x00000002
[ 1537.080386] ath10k_pci 0000:07:00.0: [40]: 0x809FF05D 0x0040EA68 0x0043A380 0x00429C10
[ 1537.080391] ath10k_pci 0000:07:00.0: [44]: 0x809FCFDB 0x0040EA88 0x0043A380 0x00000001
[ 1537.080396] ath10k_pci 0000:07:00.0: [48]: 0x80911210 0x0040EAD8 0x00000010 0x004041D0
[ 1537.080401] ath10k_pci 0000:07:00.0: [52]: 0x80911154 0x0040EB28 0x00400000 0x00000000
[ 1537.080406] ath10k_pci 0000:07:00.0: [56]: 0x8091122D 0x0040EB48 0x00000000 0x00400600
[ 1539.622307] ath10k_pci 0000:07:00.0: device successfully recovered
[COLOR="#FF0000"][ 1624.327056] wlp7s0: deauthenticating from <MAC 'FossaDeiLeoni' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)[/COLOR]
[ 1625.032585] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[ 1625.047073] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[ 1625.061330] r8169 0000:08:00.0 enp8s0: link down
[ 1625.061422] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[ 1625.350874] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[ 1630.131561] wlp7s0: authenticate with <MAC 'FossaDeiLeoni' [AC1]>
[ 1630.197195] wlp7s0: send auth to <MAC 'FossaDeiLeoni' [AC1]> (try 1/3)
[ 1630.200088] wlp7s0: authenticated
[ 1630.202622] wlp7s0: associate with <MAC 'FossaDeiLeoni' [AC1]> (try 1/3)
[ 1630.210360] wlp7s0: RX AssocResp from <MAC 'FossaDeiLeoni' [AC1]> (capab=0x431 status=0 aid=2)
[ 1630.213118] wlp7s0: associated
```

---

