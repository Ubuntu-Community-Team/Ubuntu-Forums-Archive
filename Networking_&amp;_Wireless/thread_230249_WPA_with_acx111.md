---
title: "WPA with acx111?"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by amp_man on 2006-08-05
I've got a Linksys WPC54G v2 with TI ACX111 chipset that I'm trying to make work for my brother. Afaik, I've gotten the card to work using the built-in acx (madwifi-ng) driver, but it doesn't seem to support WPA (which it does under windoze). Is there any way to get madwifi support (ie does it work with a different version of madwifi or ndiswrapper)? BTW, WEP is not an option, the next door neighbors think it's funny as hell to crack the key and hog all the bandwidth, and they haven't figured out WPA...yet.

---

### Post by amp_man on 2006-08-09
Well, it appears that I didn't know even what I thought I knew. the acx111 driver isn't based off madwifi at all. And, I can't get it to work, even with WPA and WEP disabled (and the card's MAC added to the filter list). I imagine someone must have one of these cards, mine came from Walmart. What I've done so far is remove the simlinks from /lib/firmware/`uname -r`/acx/default/ and replace them with copies of the files from the /1.2.1.34/ directory. After that, all I've done is modprobe the driver. Network manager shows that it's present, shows my ssid, but won't connect. This is what I get from the end of my dmesg, right after attempting to connect:

```
[17332567.828000] acx_i_timer: adev->status=1 (SCANNING)
[17332567.828000] continuing scan (1 sec)
[17332567.852000] acx: unknown EID 42 in mgmt frame at offset 60. IE: 2A 01 00
[17332567.852000] acx: unknown EID 221 in mgmt frame at offset 73. IE: DD 0A 08 00 28 01 01 00 02 00 FF 0F
[17332567.856000] acx: unknown EID 42 in mgmt frame at offset 60. IE: 2A 01 00
[17332567.856000] acx: unknown EID 221 in mgmt frame at offset 73. IE: DD 0A 08 00 28 01 01 00 02 00 FF 0F
[17332567.856000] acx: unknown EID 42 in mgmt frame at offset 60. IE: 2A 01 00
[17332567.856000] acx: unknown EID 221 in mgmt frame at offset 73. IE: DD 0A 08 00 28 01 01 00 02 00 FF 0F
[17332568.828000] acx_i_timer: adev->status=1 (SCANNING)
[17332568.828000] continuing scan (2 sec)
[17332568.980000] scan table: SSID='mynetwork' CH=6 SIR=32 SNR=0
[17332568.980000] peer_cap 0x0461, needed_cap 0x0001
[17332568.980000] ESSID doesn't match! ('mynetwork' station, '' config)
[17332568.980000] no matching station found in range yet
[17332568.980000] acx_set_status(1):SCANNING
[17332568.980000] starting radio scan
```

This message is looped several times, to the point where it fills all I can scroll through in my gnome terminal. Should I be switching over to ndiswrapper? Or is the acx driver the better answer?

---

