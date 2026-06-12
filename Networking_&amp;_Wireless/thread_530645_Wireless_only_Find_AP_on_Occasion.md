---
title: "Wireless only Find AP on Occasion"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Reaper355 on 2007-08-20
Hi,
I've had linux for a few months and lately I've been having some intermittent wifi connection problems - I have madwifi drivers and my network is in ok range.
To connect to wifi after reboot I run from the prompt:
```

iwconfig ath0 essid "MyNetwork"
iwconfig ath0 key 01:02:03:04:05
dhclient ath0

```

Sometimes that works and I get my AP auto-detected - Great!:

```
ath0      IEEE 802.11g  ESSID:"MyNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:--:--:--   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/70  Signal level=-86 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

When it doesn't work only the ESSID is filled in.
Then I try something like this:
```

wlanconfig ath0 destroy
wlanconfig ath create wlandev wifi0
iwconfig ath0 essid "MyNetwork"
iwconfig ath0 channel 6
iwconfig ath0 key 01:02:03:04:05
wifi0 down
wifi0 up

```

After doing that several times after a reboot wifi sometimes works.  I note that the channel doesn't want to stay put when it's not seeing the AP properly.

I need a better set of commands I can follow so my connection always works. I feel like I'm overlooking something.

Additionally, ath0 is not configured in system/network settings.  I'm thinking that could be part of the problem, but I don't want to lose my connection playing with it!

Any thoughts? :-)

---

