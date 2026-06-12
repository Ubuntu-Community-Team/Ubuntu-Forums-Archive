---
title: "Another Atheros AR928X problem"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by jorenheit on 2016-08-20
There are countless threads troubleshooting connection issues with the Atheros AR928X wireless network adapter under Linux. However, none of those threads describe the exact same problem I'm having, and none of the proposed solutions have worked for me.

The problem is that the internet connection fails, while the network connection remains. That is, the tray icon keeps indicating that there is a (very strong) connection, but loading a website will result in failure as does a simple ping to google. Most of the time, it takes just a few attempts to get going again, but it can still be very frustrating.

Most threads I found, suggest to add some parameters to the ath9k module and store these in /etc/modprobe.d/ath9k.conf. I created this file with the following content:
options ath9k nohwcrypt=1 blink=1 btcoex_enable=1
but it didn't help. I also ran a modprobe command to reload the module with these parameters without success. 

System:
Xubuntu 16.04
Kernel 4.4.0-34-generic

lsmod | grep ath9k:
```

ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211

```

dmesg | tail
```

[   30.404876] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   30.424734] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   30.429840] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   30.441056] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   31.296897] tg3 0000:03:00.0 enp3s0: Link is down
[   31.469323] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[   36.060483] wlp5s0: authenticate with ec:8a:4c:a5:8e:1f
[   36.088632] wlp5s0: send auth to ec:8a:4c:a5:8e:1f (try 1/3)
[   36.090358] wlp5s0: authenticated
[   36.091838] wlp5s0: associate with ec:8a:4c:a5:8e:1f (try 1/3)
[   36.146074] wlp5s0: RX AssocResp from ec:8a:4c:a5:8e:1f (capab=0x411 status=0 aid=4)
[   36.146187] wlp5s0: associated
[   36.146205] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready

```

To the output of dmesg, I should add that these are its contents from boot and nothing is added when the connection drops or is restored, so I'm not sure if this even is of any significance.

---

