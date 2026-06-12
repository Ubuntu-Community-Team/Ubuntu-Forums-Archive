---
title: "Wireless networking - I have to restart network-manager after booting and logging in"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by mike106 on 2015-08-16
For some reason when I first boot I have to restart network-manager to get my wireless working on my machine.  I upgraded from V 14 a week ago and this just started.  I get the following in `dmesg`  when I login:

```
IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

When I do `sudo restart network-manager`, I see:

```
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

Sometimes I have to restart it a couple of times for it to work. 

Here is my system info, let me know what else is needed:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

```

`dmesg | grep wlan0`

```
[   13.189114] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
-- snip --
[  271.965106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  273.219266] wlan0: authenticate with 94:10:3e:77:39:96
[  273.228327] wlan0: send auth to 94:10:3e:77:39:96 (try 1/3)
[  273.229782] wlan0: authenticated
[  273.236074] wlan0: associate with 94:10:3e:77:39:96 (try 1/3)
[  273.239275] wlan0: RX AssocResp from 94:10:3e:77:39:96 (capab=0x411 status=0 aid=1)
[  273.256293] wlan0: associated
[  273.256351] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

```

$ lspci | grep Network
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

```

$ lsmod | grep b
Module                  Size  Used by
binfmt_misc            13140  1 
dcdbas                 14448  1 dell_laptop
nand_bch               13067  1 nand
bch                    17197  1 nand_bch
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb_hcd                12749  0 
b44                    31275  0 
mii                    13654  1 b44
i2c_algo_bit           13197  1 i915
ssb                    51854  3 b43,b44,ssb_hcd

```

```

$ dpkg -l | grep b43
ii  b43-fwcutter                          1:019-2                                    i386         utility for extracting Broadcom 43xx firmware
ii  firmware-b43-installer                1:019-2                                    all          firmware installer for the b43 driver

```

Edited to add:
```

# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---------------------
Thanks,
M.

[http://mikeski.net]("http://mikeski.net/")

---

### Post by mike106 on 2015-08-30
Really?  Nobody has any ideas?

---

