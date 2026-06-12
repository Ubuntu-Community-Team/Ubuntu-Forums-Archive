---
title: "rt61 wireless authentication/association timeouts"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by majikshoe on 2008-11-10
Hello all,

After upgrading my desktop to 8.10, my wireless connectivity has gone awry.  Wireless has worked fine for me since Dapper so I don't know why it's an issue now.  My laptop running Hardy works fine, so I know it isn't the router.  Hope someone can help me, because today I can access the network (after a long time trying), whereas yesterday it was complete cactus.

Here is what I have:

Kernel version:
```
jroyals@habanero:~$ uname -r
2.6.27-7-generic

```

lspci:
```
jroyals@habanero:~$ lspci | grep RT
02:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

lsmod:
```
jroyals@habanero:~$ lsmod | grep rt
rt61pci                30208  0 
crc_itu_t              10496  1 rt61pci
rt2x00pci              16256  1 rt61pci
rt2x00lib              40576  2 rt61pci,rt2x00pci
rfkill                 19364  1 rt2x00lib
led_class              13192  1 rt2x00lib
mac80211              253440  2 rt2x00pci,rt2x00lib
cfg80211               37136  2 rt2x00lib,mac80211
eeprom_93cx6           10752  1 rt61pci
```

etc/network/interfaces:
```
jroyals@habanero:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

iwlist:
```
jroyals@habanero:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:19:DB:0E:61:61
                    ESSID:"Fragstealers"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/100  Signal level:-44 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000b4ba810dc
                    Extra: Last beacon: 16ms ago
```


Not sure if I need to provide any more info, iwconfig, ifconfig etc, but since I'm connected now I think its all OK so it must work in some sort of capacity (it just takes it's time getting there)?

Anyway, here is the interesting bit:

dmesg:
```
jroyals@habanero:~$ dmesg | grep wlan0
(trimmed guff)
[  137.429054] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.348088] wlan0: authenticate with AP 00:19:db:0e:61:61
[  138.348123] wlan0: authenticate with AP 00:19:db:0e:61:61
[  138.548046] wlan0: authenticate with AP 00:19:db:0e:61:61
[  138.748038] wlan0: authenticate with AP 00:19:db:0e:61:61
[  138.948046] wlan0: authentication with AP 00:19:db:0e:61:61 timed out
(rinse and repeat, until it actually does authenticate....)
[  170.644075] wlan0: authenticate with AP 00:19:db:0e:61:61
[  170.644201] wlan0: authenticate with AP 00:19:db:0e:61:61
[  170.645428] wlan0: authenticated
[  170.645436] wlan0: associate with AP 00:19:db:0e:61:61
[  170.844039] wlan0: associate with AP 00:19:db:0e:61:61
[  171.048060] wlan0: associate with AP 00:19:db:0e:61:61
[  171.244084] wlan0: association with AP 00:19:db:0e:61:61 timed out
[  181.396088] wlan0: authenticate with AP 00:19:db:0e:61:61
[  181.396576] wlan0: authenticate with AP 00:19:db:0e:61:61
[  181.596039] wlan0: authenticate with AP 00:19:db:0e:61:61
[  181.796060] wlan0: authenticate with AP 00:19:db:0e:61:61
[  181.996061] wlan0: authentication with AP 00:19:db:0e:61:61 timed out
[  187.876363] wlan0: deauthenticated
[  192.140090] wlan0: authenticate with AP 00:19:db:0e:61:61
[  192.140146] wlan0: authenticate with AP 00:19:db:0e:61:61
[  192.340059] wlan0: authenticate with AP 00:19:db:0e:61:61
[  192.540061] wlan0: authenticate with AP 00:19:db:0e:61:61
[  192.744087] wlan0: authentication with AP 00:19:db:0e:61:61 timed out
(and on and on it goes, until finally...)
[  225.500077] wlan0: authenticate with AP 00:19:db:0e:61:61
[  225.700061] wlan0: authenticate with AP 00:19:db:0e:61:61
[  225.818269] wlan0: authenticated
[  225.818279] wlan0: associate with AP 00:19:db:0e:61:61


[  225.826857] wlan0: RX AssocResp from 00:19:db:0e:61:61 (capab=0x411 status=0 aid=2)
[  225.826864] wlan0: associated
[  225.827676] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  236.144014] wlan0: no IPv6 routers present
(and then its all happy)

```

It tries to authenticate first - I'm using WPA-PSK as can be seen in the iwlist output.  It tries and tries but times out most of the time.  Occasionally it does manage to authenticate (170.645428) but then times out at the next step, association (171.244084).  At this stage, I see in my router logs that it does associate with the AP but Ubuntu seems to time out anyway.

The kernel logs show the same pattern on and on, until one of two things happen.  I get sick of waiting and boot to XP, or it magically connects as it did today (225.826864)

I've had this problem since the upgrade.  I decided to replace NetworkManager with wicd to see if that helped, but unfortunately it made no difference.

Has anyone seen this behavior before?  My suspicion is that the timeout figure is too low in the driver.  Can I change the timeout somehow (without recompiling the kernel if at all possible)?

Thanks!
Jason

---

### Post by majikshoe on 2008-11-12
Bump!

Should I raise this as a bug?  Something's busted but I don't know how to fix.

Cheers,
Jason

---

