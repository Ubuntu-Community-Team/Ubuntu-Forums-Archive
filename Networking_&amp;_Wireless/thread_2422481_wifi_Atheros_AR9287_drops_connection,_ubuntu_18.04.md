---
title: "wifi Atheros AR9287 drops connection, ubuntu 18.04"
date: 2019-07-08
forum: Networking &amp; Wireless
---

### Post by fight21 on 2019-07-08
hi, 
I install ubuntu 18.04 in my old acer laptop, but the wifi doesn't work all , It's shows the wifi is  hard blocks.
I have try everything I find in net, but didn't solve it.

```

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. T77H167.00 [105b:e034]
    Kernel driver in use: ath9k

```

rfkill list
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

lsmod | egrep 'wmi | ath9k'
```

wmi_bmof               16384  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              802816  1 ath9k
cfg80211              667648  4 ath9k_common,ath9k,ath,mac80211
video                  45056  2 acer_wmi,i915
wmi                    24576  2 acer_wmi,wmi_bmof
```

---

### Post by praseodym on 2019-07-08
Try resetting your BIOS to default settings

---

### Post by fight21 on 2019-07-09
FIrst I only add blacklist acer_wmi in /etc/modprobe.d/blacklist.conf, but it didn't work.
Then I follow the above. reset the BIOS. and add blacklist acer_wmi in /etc/modprobe.d/blacklist.conf and the wifi work.
I don'st remember when I reset the BIOS, what have changed, but it work.
thanks.

---

