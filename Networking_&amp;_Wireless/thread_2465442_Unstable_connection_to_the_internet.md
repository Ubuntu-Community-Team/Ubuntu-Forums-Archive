---
title: "Unstable connection to the internet"
date: 2021-08-01
forum: Networking &amp; Wireless
---

### Post by draxdomax on 2021-08-01
I have this annoying issue that I don't know how to investigate, let alone solve. 
I'll try to briefly describe what I think is relevant, as I don't know what is a red herring and what is a smoking gun :)

* Running Ubuntu 20.04.2 LTS with all updates on a Clevo [COLOR=#000000][FONT=Arial]NS50MU ([/FONT][/COLOR]Intel Wi-Fi 6 AX200) that's connected to the internet over wifi.

Most of the time, things work fine!
Sometimes, as I would type in a website to visit (and this can be any website, even stuff I am browsing already on another tab... Even google.com), Chrome hangs in there for what feels like 10 seconds and then returns an error "dns_probe_finished_nxdomain" - which doesn't look right for 'google.com'...

Needless to say, none of my other computers connected to the same network experience anything like this.

Usually what I do is wait about 20 seconds and the error resolves itself and 'google.com' is resolved correctly.

... This may be an unrelated issue but sometimes the video on youtube stops loading midway into the stream. It recovers after about 5 seconds... Again, none of my other computers have such intstability.

- I do not have a physical LAN cable to try like this for a while and see if the problem is around the WIFI.

-------

Please, any ideas how to start figuring what is going on? I have basic scripting abilities and some understanding of networks (sad part is I work for a DNS company but not really an expert on networks!)

Really trying to make Ubuntu my go-to-OS, having exclusively installed it on both personal and work computers... But that networking issue is ruining it for me...

---

### Post by chili555 on 2021-08-02
> Intel Wi-Fi 6 AX200

Awesome! I love Intel devices and particularly the newer AX series. Their tweaks and tricks are, as yet, still being uncovered.

> Really trying to make Ubuntu my go-to-OS, having exclusively installed it on both personal and work computers.

Does the problem exist at both work and home?

I suspect that the problem might be that your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

While at home, may we see:

```
nmcli device wifi list

```
Just show us the access point to which you are coonected, indicated by the asterisk, like this:

```
*       xx:2B:B0:DC:45:xx  GBR5   Infra  149   405 Mbit/s  79 &#9602;&#9604;&#9606;_  WPA2

```
As well, please obfuscate the MAC address as I have done.

---

### Post by draxdomax on 2021-08-03
Actually, I don't currently have both work and home on Ubuntu :)
I've just switched my home laptop and I am also about to start a new job soon and they asked me what set-up I prefer and I asked for an Ubuntu one.

So, I don't have another Ubuntu system to compare to.

Actually it's pretty bad today. Had to wait for it to resolve itself TWICE while trying to answer here :/

Today, it's:
- When the problem first presents itself (can't browse to anything, youtube videos stuck):
DNS_PROBE_STARTED
- When retrying to browse to something:
DNS_PROBE_FINISHED_BAD_CONFIG

And then it starts working about 10 seconds after this...

-------------------

My router was set up as one SSID for both frequencies. I split it and named each differently.
This is my wifi info when connected to the 5 GHz one:
*       **:B0:01:95:60:**  ZwierzNet     Infra  112   540 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2

-------------------

Let's see if splitting the SSID stops this!

---

### Post by draxdomax on 2021-08-05
nope. Still happens :/

---

### Post by chili555 on 2021-08-05
Let's see if we find any other clues in the log:

```
sudo dmesg | grep wl
```

---

### Post by draxdomax on 2021-08-05
I don't see anything that raises a specific alert to me, but then again, I don't even know where the timestamp is :D
Although, it does talk a lot about IPv6, which is still optional and probably not the most tested feature of the OS.

[    5.182162] iwlwifi 0000:35:00.0: enabling device (0000 -> 0002)
[    5.194527] iwlwifi 0000:35:00.0: Direct firmware load for iwlwifi-cc-a0-56.ucode failed with error -2
[    5.196667] iwlwifi 0000:35:00.0: api flags index 2 larger than supported by driver
[    5.196676] iwlwifi 0000:35:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.22
[    5.196680] iwlwifi 0000:35:00.0: Found debug destination: EXTERNAL_DRAM
[    5.196681] iwlwifi 0000:35:00.0: Found debug configuration: 0
[    5.196997] iwlwifi 0000:35:00.0: loaded firmware version 55.d9698065.0 cc-a0-55.ucode op_mode iwlmvm
[    5.197046] iwlwifi 0000:35:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    5.259981] iwlwifi 0000:35:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    5.441647] iwlwifi 0000:35:00.0: base HW address: e0:d4:64:23:84:76
[    5.460227] iwlwifi 0000:35:00.0 wlp53s0: renamed from wlan0
[    9.800840] wlp53s0: authenticate with 22:b0:01:95:60:a1
[    9.802353] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[    9.827573] wlp53s0: authenticated
[    9.835806] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[    9.838278] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=2)
[    9.841734] wlp53s0: associated
[    9.885921] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[   10.010562] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[   54.637328] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[   55.139368] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 3
[   95.180371] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[  119.334018] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[  119.433483] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[  122.989330] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 0
[  128.985157] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[  132.423482] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[  132.646768] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[  133.580179] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[ 1140.344428] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[ 1140.429421] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[48939.306782] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[60941.605198] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 0
[60945.662874] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[60956.653756] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 0
[60961.185805] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[60961.185810] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 0
[60961.185813] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[61761.242880] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[62293.231461] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[62402.649378] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[62858.588129] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 0
[62859.083169] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[63181.135806] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[63181.135809] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 0
[63181.296557] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 3
[63756.880106] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[63757.128353] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 3
[64118.039289] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[64937.930083] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[65341.679228] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[65352.871576] wlp53s0: authenticate with 22:b0:01:95:60:a1
[65352.872993] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[65352.898757] wlp53s0: authenticated
[65352.902601] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[65352.904878] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=2)
[65352.908889] wlp53s0: associated
[65352.929625] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[65353.084994] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[68977.992756] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[69151.042511] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[69407.002682] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[69677.992877] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 3
[69830.783577] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[70521.199588] wlp53s0: deauthenticated from 22:b0:01:95:60:a1 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[70521.295194] wlp53s0: authenticate with 22:b0:01:95:60:a1
[70521.297575] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[70521.326479] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 2/3)
[70521.329524] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 3/3)
[70521.333031] wlp53s0: authentication with 22:b0:01:95:60:a1 timed out
[70524.448696] wlp53s0: authenticate with 22:b0:01:95:60:a1
[70524.451219] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[70524.477187] wlp53s0: authenticated
[70524.481963] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[70524.484934] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=1)
[70524.488978] wlp53s0: associated
[70524.489037] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[72672.902579] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[73040.285700] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 3
[73475.556932] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[73475.562532] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 0
[93707.343126] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[100098.082779] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[101643.606010] wlp53s0: authenticate with 22:b0:01:95:60:a1
[101643.607405] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[101643.632923] wlp53s0: authenticated
[101643.640822] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[101643.643896] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=1)
[101643.647894] wlp53s0: associated
[101643.658097] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[101643.678171] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[101691.410592] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 0
[101772.396386] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[101792.087092] wlp53s0: authenticate with 22:b0:01:95:60:a1
[101792.088361] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[101792.113884] wlp53s0: authenticated
[101792.116753] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[101792.119569] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=1)
[101792.123065] wlp53s0: associated
[101792.140824] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[101792.148216] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[102027.514949] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[129767.582416] wlp53s0: authenticate with 22:b0:01:95:60:a1
[129767.583816] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[129767.609303] wlp53s0: authenticated
[129767.610159] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[129767.612905] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=1)
[129767.616592] wlp53s0: associated
[129767.644823] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[129767.662417] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[129768.218096] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[129768.592828] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[129771.608191] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[129927.130766] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 0
[130363.453608] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 3
[130363.716501] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 0
[131036.107621] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[229505.222610] wlp53s0: authenticate with 22:b0:01:95:60:a1
[229505.225412] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[229505.251761] wlp53s0: authenticated
[229505.255464] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[229505.258170] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=4)
[229505.262723] wlp53s0: associated
[229505.292457] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[229505.316526] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[229507.386921] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[229508.847490] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[229683.991724] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 0
[231499.094351] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[237394.225876] wlp53s0: authenticate with 22:b0:01:95:60:a1
[237394.229597] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[237394.255993] wlp53s0: authenticated
[237394.258533] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[237394.261143] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=4)
[237394.266538] wlp53s0: associated
[237394.296528] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[237394.354595] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[237548.688820] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[237548.793733] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3
[237548.849880] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[237590.866810] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[239277.833940] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[245456.961053] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[245457.014288] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[245636.908882] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 0
[246364.666730] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[246451.889165] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3
[247701.057281] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[248706.194887] wlp53s0: authenticate with 22:b0:01:95:60:a1
[248706.196217] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[248706.221634] wlp53s0: authenticated
[248706.222251] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[248706.224816] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=4)
[248706.228637] wlp53s0: associated
[248706.253886] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[248706.259076] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[249318.673192] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[249318.691745] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[249760.997116] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[249760.997121] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[249917.897869] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[253889.813511] wlp53s0: authenticate with 22:b0:01:95:60:a1
[253889.814920] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[253889.840881] wlp53s0: authenticated
[253889.844339] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[253889.847122] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[253889.851879] wlp53s0: associated
[253889.878478] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[253889.938642] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[253928.825013] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 3
[254188.125603] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[255406.187735] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[255627.465311] wlp53s0: authenticate with 22:b0:01:95:60:a1
[255627.466708] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[255627.493093] wlp53s0: authenticated
[255627.495228] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[255627.497816] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[255627.501757] wlp53s0: associated
[255627.530199] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[255627.594051] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[255637.909829] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 0
[258605.675615] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 0
[258605.906439] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 0
[259273.574436] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[260893.910351] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 3
[260915.533576] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[260920.049636] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3
[261153.444870] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[261153.444874] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[261154.482233] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[261236.085000] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[261238.315473] wlp53s0: authenticate with 22:b0:01:95:60:a1
[261238.318211] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[261238.344730] wlp53s0: authenticated
[261238.352085] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[261238.354503] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[261238.357900] wlp53s0: associated
[261238.387734] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[261238.389424] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[261255.587182] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[261258.172456] wlp53s0: authenticate with 22:b0:01:95:60:a1
[261258.175096] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[261258.201158] wlp53s0: authenticated
[261258.204259] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[261258.206708] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[261258.209854] wlp53s0: associated
[261258.240058] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[261258.255268] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[261258.330601] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[261261.617660] wlp53s0: authenticate with 22:b0:01:95:60:a1
[261261.620293] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[261261.646447] wlp53s0: authenticated
[261261.648279] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[261261.650656] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[261261.653955] wlp53s0: associated
[261261.681734] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[261261.737468] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[261274.207114] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[261276.095517] wlp53s0: authenticate with 22:b0:01:95:60:a1
[261276.098158] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[261276.124121] wlp53s0: authenticated
[261276.124372] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[261276.126996] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[261276.134283] wlp53s0: associated
[261276.158154] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[261276.176636] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[261289.219933] wlp53s0: deauthenticating from 22:b0:01:95:60:a1 by local choice (Reason: 3=DEAUTH_LEAVING)
[261291.357414] wlp53s0: authenticate with 22:b0:01:95:60:a1
[261291.360006] wlp53s0: send auth to 22:b0:01:95:60:a1 (try 1/3)
[261291.386143] wlp53s0: authenticated
[261291.392578] wlp53s0: associate with 22:b0:01:95:60:a1 (try 1/3)
[261291.394918] wlp53s0: RX AssocResp from 22:b0:01:95:60:a1 (capab=0x1011 status=0 aid=3)
[261291.398263] wlp53s0: associated
[261291.424430] IPv6: ADDRCONF(NETDEV_CHANGE): wlp53s0: link becomes ready
[261291.433603] wlp53s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 22:b0:01:95:60:a1
[262692.253903] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 0
[262692.361531] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3
[265904.207014] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 3
[268460.090049] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[268975.042594] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[269069.576592] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 3
[269895.788312] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[270837.892510] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[270963.822836] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 8, stopping BA session on TID 0
[273176.869941] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[273176.934046] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[273288.948367] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 3
[273363.877390] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 0
[273565.956698] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[273704.895727] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[273734.859648] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[273739.236719] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 4, stopping BA session on TID 3
[274106.094723] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[274576.040113] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[277355.694463] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[277380.362210] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 1, stopping BA session on TID 0
[277416.680719] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 5, stopping BA session on TID 3
[277675.512918] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 7, stopping BA session on TID 3
[277798.912850] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[277799.164614] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 2, stopping BA session on TID 3
[278218.904694] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 6, stopping BA session on TID 0
[278696.871187] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3

---

### Post by chili555 on 2021-08-05
```
iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3
```Old Chili doesn't like this one bit!

Let's see what is peculiar about your access point.

Please run:

```
sudo iwlist scan
```There be a number of APs shown; yours has a MAC address of 22:b0:01:95:60:a1. Please show us its details, like this:

Cell 02 - Address: <MAC 'nx2.4' <mac_address_here>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"nx2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bf0a735638
                    Extra: Last beacon: 3932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

> I don't even know where the timestamp isThis is the timestamp:

> [[COLOR="#FF0000"]278696.871187[/COLOR]] iwlwifi 0000:35:00.0: reached 10 old SN frames from 22:b0:01:95:60:a1 on queue 3, stopping BA session on TID 3That is the number of seconds since boot.

More conventional timestamps are in /var/log/syslog (and others):

> [COLOR="#FF0000"]Aug  5 20:10:11[/COLOR] T440p gnome-shell[1909]: Can't update stage views actor dashtodockDashScrollview is on because it needs an allocation.

---

### Post by draxdomax on 2021-08-06
wlp53s0   Scan completed :
          Cell 01 - Address: 22:B0:01:95:60:A1
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ZwierzNet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d97bdd061
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 00095A776965727A4E6574
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 073C4742202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 200100
                    IE: Unknown: 23021600
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050400020000
                    IE: Unknown: 420100
                    IE: Unknown: 46053000000000
                    IE: Unknown: 2D1A6F0017FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D1670070400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500088000400040
                    IE: Unknown: BF0C3268830FAAFF0000AAFF0000
                    IE: Unknown: C005016A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD830050F204104A0001101044000102103B000103104700105CD2C7E7A07D5D4792EB7A21B0144E4610210008566F6461666F6E65102300075448473330303010240007566F78332E30761042000931393237534146364E1054000800060050F204000110110008566F7820332E3076100800020784103C0001031049000600372A000120
                    IE: Unknown: DD0500904C0417
                    IE: Unknown: DD090010180204009C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07506F9A16010100
                    IE: Unknown: 6C027F00

---

### Post by chili555 on 2021-08-06
> Frequency:5.56 GHz (Channel 112)Is this a channel you selected or one that the router autoselected? Fixed and not autoselect is recommended.

How many other routers in your neighborhood are set to 112, possibly interfering?

```
nmcli device wifi list
```

I recommend a channel far away from others in the neighborhood and one, of course, that your device also supports:

```
sudo iw list 
```

---

