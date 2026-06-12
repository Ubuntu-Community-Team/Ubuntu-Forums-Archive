---
title: "[SOLVED] RFMON is enabled?? Help"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by Promaster91 on 2008-03-28
I just updated my wifi drivers to MadWifi. Whenever i try to use aircrack-ng I get this message.
```

stefan@stefan-laptop:~/Desktop$ sudo airodump-ng --channel 8 --write hello 

ath0ioctl(SIOCSIWMODE) failed: Invalid argument
ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig ath0 up; iwconfig ath0 mode Monitor channel <#>'
Sysfs injection support was not found either.

```

My card is in monitor mode but not in this RFMON? Does anybody know how to enable RFMON. Thanks.

---

### Post by Promaster91 on 2008-05-21
bump

---

### Post by Promaster91 on 2008-05-27
Found the answer. I had to download that patched madwifi driver and put my card into monitor mode.
```

airmon-ng start wifi0

```

---

