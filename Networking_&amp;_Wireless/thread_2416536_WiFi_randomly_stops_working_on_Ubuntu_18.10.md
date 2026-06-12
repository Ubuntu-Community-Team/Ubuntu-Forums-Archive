---
title: "WiFi randomly stops working on Ubuntu 18.10"
date: 2019-04-11
forum: Networking &amp; Wireless
---

### Post by liaquore on 2019-04-11
After using my PC for 40 minutes to 2 hours my WiFi randomly loses the ability to scan for networks.

This is iwconfig before (when it's working):

[FONT=Verdana]enp3s0 no wireless extensions. [/FONT]

[FONT=Verdana]wlp6s0 IEEE 802.11 ESSID : "hi" [/FONT]
[FONT=Verdana]Mode:Managed Frequency:2.412 GHz Access Point: C8 : 94 : BB : CC : 34 : 4C [/FONT]
[FONT=Verdana]Bit Rate=144.4 Mb/s Tx-Power=20 dBm [/FONT]
[FONT=Verdana]Retry short limit:7 RTS thr=2347 B Fragment thr : off [/FONT]
[FONT=Verdana]Power Management : off [/FONT]
[FONT=Verdana]Link Quality=62/70 Signal level=-48 dBm [/FONT]
[FONT=Verdana]Rx invalid nwid : 0 Rx invalid crypt:0 Rx invalid frag : 0 [/FONT]
[FONT=Verdana]Tx excessive retries:0 Invalid misc:0 Missed beacon : 0 [/FONT]

[FONT=Verdana]lo no wireless extensions.

This is iwconfig after it stops working:

[/FONT][FONT=Verdana]wlp6s0 IEEE 802.11 ESSID : off/any [/FONT]
[FONT=Verdana]Mode: Managed Access Point: Not-Associated Tx-Power:20 dBm [/FONT]
[FONT=Verdana]Retry short limit:7 RTS thr=2347 B Fragment thr : off [/FONT]
[FONT=Verdana]Power management : off

When it stops working, I get a notification saying "activation of network connection failed". Also, when this happens, both lights on my WiFi card go on (they're both labelled "Link" and "Ttx/Rtx". When my WiFi is working, only "Link" is glowing. How do I fix this?

P.S: installed Wicd did nothing.[/FONT]

---

### Post by kc1di on 2019-04-12
first we need to know which wireless card is in your machine. if your not sure go to a terminal and copy paste this command and post the output.
```
sudo lshw -c network
```

---

