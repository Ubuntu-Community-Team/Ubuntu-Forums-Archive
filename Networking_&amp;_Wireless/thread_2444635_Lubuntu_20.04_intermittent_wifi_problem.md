---
title: "Lubuntu 20.04 intermittent wifi problem"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by graeme-thorn on 2020-06-02
I have an issue with the wifi in a HP 15-db0598sa that I've installed lubuntu 20.04 on.


Pinging google.com gives typical output of the form:


```
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=171 ttl=53 time=12.3 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=172 ttl=53 time=96.4 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=175 ttl=53 time=1026 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=176 ttl=53 time=11.2 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=177 ttl=53 time=11.4 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=178 ttl=53 time=10.3 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=179 ttl=53 time=10.5 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=181 ttl=53 time=1035 ms
64 bytes from lhr25s26-in-f14.1e100.net (172.217.169.14): icmp_seq=182 ttl=53 time=22.9 ms
```
where the ping varies from ~10ms (as on my other machines) up to > 1000 ms, with the odd ping (about 24% packet loss) dropped (such as between 172 and 175 and 179 and 181 above).

[COLOR=#242729][FONT=Arial]I have tried [github.com/lwfinger/rtlwifi_new/tree/rtw88]("https://github.com/lwfinger/rtlwifi_new/tree/rtw88"), which are the latest versions (the output of lspci -knn | grep Net -A3 is as follows) and this is still giving me ~25% packet loss and intermittent >1000ms ping times.

[/FONT][/COLOR][FONT=courier new]03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723DE 802.11b/g/n PCIe Adapter [10ec:d723]
        DeviceName: WLAN
        Subsystem: Hewlett-Packard Company RTL8723DE 802.11b/g/n PCIe Adapter [103c:8319]
        Kernel driver in use: rtw_8723de
[/FONT]

[COLOR=#242729][FONT=Arial]Is there anything else I can try?

I do have an older machine running 18.04 which will be in the same location as this machine will eventually be, but the ping there is fine:

```

64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=4 ttl=53 time=12.8 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=5 ttl=53 time=11.6 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=6 ttl=53 time=12.1 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=7 ttl=53 time=11.0 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=8 ttl=53 time=11.0 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=9 ttl=53 time=21.8 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=10 ttl=53 time=11.3 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=11 ttl=53 time=11.5 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=12 ttl=53 time=12.3 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=13 ttl=53 time=13.2 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=14 ttl=53 time=11.6 ms
64 bytes from ams16s21-in-f14.1e100.net (216.58.212.206): icmp_seq=15 ttl=53 time=11.5 ms

```[/FONT][/COLOR]

---

### Post by slickymaster on 2020-06-02
Thread moved to **Networking & Wireless** for a better fit

---

### Post by CelticWarrior on 2020-06-02
Welcome.

Please follow instructions here [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) in order to gather information about the network connection.

---

### Post by graeme-thorn on 2020-06-02
The pastebin from wireless-info.txt is here:
[https://pastebin.com/ZTmRKQ6q](https://pastebin.com/ZTmRKQ6q)

---

### Post by CelticWarrior on 2020-06-02
Two entirely **expected** issues:
[LIST=1]
[*]Mixed mode
[*]TKIP
[/LIST]

This is the worst possible settings for a modern router/AP. Please use WPA2-AES only, no mixed mode and certainly not TKIP.
Yes, I am aware other devices seem to work fine in your network. This doesn't and changing the settings to the proper ones will improve all.

---

### Post by graeme-thorn on 2020-06-02
I have switched the security to AES and WPA2, but I can only guess that "Mixed Mode" means switching only to 2.4GHz or 5GHz and not both (as it is not in the output of the wireless-info that I pasted). For legacy purposes, I've moved to 2.4GHz.

I have rebooted the router, and the ping is still poor:

```

$ ping google.com
PING google.com (216.58.212.238) 56(84) bytes of data.
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=2 ttl=53 time=264 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=3 ttl=53 time=901 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=7 ttl=53 time=1127 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=8 ttl=53 time=827 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=10 ttl=53 time=1030 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=11 ttl=53 time=13.2 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=12 ttl=53 time=13.4 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=13 ttl=53 time=177 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=14 ttl=53 time=14.4 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=16 ttl=53 time=1026 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=17 ttl=53 time=12.9 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=18 ttl=53 time=13.5 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=19 ttl=53 time=13.1 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=20 ttl=53 time=13.6 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=21 ttl=53 time=13.0 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=22 ttl=53 time=13.1 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=23 ttl=53 time=12.7 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=24 ttl=53 time=13.0 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=26 ttl=53 time=1025 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=27 ttl=53 time=13.0 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=29 ttl=53 time=1049 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=31 ttl=53 time=997 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=34 ttl=53 time=1015 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=36 ttl=53 time=1028 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=37 ttl=53 time=14.6 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=38 ttl=53 time=14.4 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=39 ttl=53 time=18.7 ms
64 bytes from ams16s22-in-f14.1e100.net (216.58.212.238): icmp_seq=40 ttl=53 time=15.6 ms
^C
--- google.com ping statistics ---
40 packets transmitted, 28 received, 30% packet loss, time 39340ms
rtt min/avg/max/mdev = 12.662/381.760/1127.068/468.119 ms, pipe 2

```

---

### Post by CelticWarrior on 2020-06-02
No, mixed mode is WPA/WPA2 -> Should be WPA2 only.

---

### Post by graeme-thorn on 2020-06-02
Well, I've done that, and I have as suggested elsewhere tried
```
[COLOR=#242729][FONT=Consolas]sudo modprobe -r rtw_8723de
[/FONT][/COLOR]sudo modprobe rtw_8723de ant_sel=2

```
with the ant_sel being 1 or 2, to select which antenna is used and there's still no change in the ping or in the packet loss.

---

### Post by graeme-thorn on 2020-06-02
Forget this, I've gone back to plain ubuntu to see if I can fix it that way

---

