---
title: "acx - FAILED to free any of the many full tx buffers"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by bazz-dee on 2006-11-02
Im running edgy eft since the beta version, but the problem is pretty new (1 or 2 weeks)


When i boot up ubuntu i get an ip with dhcp, but i cant
do anything over this my wlan interface. after some
time i get following messages:


```

bazzdee@desktop:~$ dmesg | grep wlan0
[17179589.484000] acx v0.3.21: net device wlan0, driver
compiled against wireless extensions 20 and Linux
2.6.17-10-generic
[17179591.592000] wlan0 (WE) : Driver using old
/proc/net/wireless support, please fix driver !
[17179599.536000] wlan0: duplicate address detected!
[17179790.272000] NETDEV WATCHDOG: wlan0: transmit
timed out
[17179790.272000] wlan0: tx timeout!
[17179790.272000] wlan0: recalibrating radio
[17179790.320000] wlan0: successfully recalibrated radio
[17179814.272000] NETDEV WATCHDOG: wlan0: transmit
timed out
[17179814.272000] wlan0: FAILED to free any of the many
full tx buffers. Switching to emergency freeing. Please
report!
[17179814.272000] wlan0: tx timeout!
[17179814.272000] wlan0: less than 5 minutes since last
radio recalibration, not recalibrating (maybe card is
too hot?)

```


The funny thing is, it says the card is too hot even if the computer wasn't running for 2 hours.
In windows the card runs without problems for hours and hours.

Well today i decided to reinstall edgy eft, first the card was running but giving this messages:


```
[17179638.612000] IPv6 over IPv4 tunneling driver
[17180104.264000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17180113.180000] skge eth0: disabling interface
[17180129.296000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17180131.668000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17180133.632000] ICMPv6 NA: someone advertises our address on wlan0!
[17180142.624000] wlan0: no IPv6 routers present
[17180517.276000] wlan0: rx: 394 DUPs in 1537 packets received in 10 secs
[17180527.312000] wlan0: rx: 190 DUPs in 616 packets received in 10 secs
[17180537.396000] wlan0: rx: 135 DUPs in 482 packets received in 10 secs
[17180547.860000] wlan0: rx: 163 DUPs in 541 packets received in 10 secs
[17180557.932000] wlan0: rx: 162 DUPs in 593 packets received in 10 secs
[17180567.940000] wlan0: rx: 134 DUPs in 391 packets received in 10 secs
[17180577.952000] wlan0: rx: 99 DUPs in 343 packets received in 10 secs
[17180588.140000] wlan0: rx: 170 DUPs in 495 packets received in 10 secs
[17180598.432000] wlan0: rx: 198 DUPs in 688 packets received in 10 secs
[17180608.784000] wlan0: rx: 54 DUPs in 125 packets received in 10 secs
[17180618.828000] wlan0: rx: 124 DUPs in 388 packets received in 10 secs
[17180629.048000] wlan0: rx: 68 DUPs in 262 packets received in 10 secs
[17180639.136000] wlan0: rx: 92 DUPs in 248 packets received in 10 secs
[17180649.576000] wlan0: rx: 92 DUPs in 279 packets received in 10 secs
[17182810.284000] wlan0: rx: 71 DUPs in 417 packets received in 10 secs
[17182824.292000] wlan0: rx: 77 DUPs in 469 packets received in 10 secs
[17183055.732000] wlan0: rx: 60 DUPs in 360 packets received in 10 secs 
```



After i was playing some games in windows and going back to linux card wasnt running again. So anybody has some purposes for me?

---

### Post by Thiago Cesar Vieira on 2007-12-17
Hi bazz-dee!

I have the same problems with my Ubuntu.
Had you already fixed? How?

Thanks a lot!

---

### Post by bazz-dee on 2007-12-17
i got a new card now

---

