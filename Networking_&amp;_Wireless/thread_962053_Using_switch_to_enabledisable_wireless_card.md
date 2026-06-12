---
title: "Using switch to enable/disable wireless card"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by substanceD on 2008-10-28
Hello,

This isn't such a major issue, but it comes up frequently enough to bother me sometimes. The problem that I have is after physically switching off my laptop's wireless card (Intel 4965 is the card's model), I can't get it to come back on. Flipping the switch to the "on" position re-enables bluetooth, but alas no wireless networking. I've tried using

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

which outputs

> wlan0: unknown hardware address type 803
wmaster0: unknown hardware address type 801
wlan0: unknown hardware address type 803
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1f:c6:75:e7:ec
Sending on   LPF/eth0/00:1f:c6:75:e7:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of [snip] from [snip]
DHCPREQUEST of [snip] on eth0 to [snip] port 67
DHCPACK of [snip] from [snip]
bound to [snip] -- renewal in 1546 seconds.

Is there some other command I might try? The only time this problem is especially annoying is when I forget to switch on the card before I boot, in which case I look around for an ethernet cable.

Thanks for any help,
substanceD

---

### Post by pytheas22 on 2008-10-28
You could check your BIOS--there may be an option to tell the card to always be on.  You could also create a launcher to run '/etc/init.d/networking restart' so that you can do this more conveniently, since it fixes the issue (right?).  Beyond that, unfortunately, I don't know of any easier way to do this.

---

### Post by substanceD on 2008-10-29
No...unfortunately '/etc/init.d/networking restart' doesn't work. The thing is that I don't necessarily always *want* the card to be on--if I'm not on AC power and I'm not using the Internet I may as well turn off the wireless card to save my battery.

The problem is that there doesn't seem to be a way to re-enable the card once it's off, like I was saying--as if Ubuntu won't recognize it unless it has been plugged in since the computer turned on. On a side note, there is an indicator light for the wireless card, which also remains off when I switch on the card. In Vista (I have a dual-boot) the on-off switch works just fine, and the indicator light comes on whenever the wireless card does.

---

### Post by pytheas22 on 2008-10-29
Sorry, I thought the '/etc/init.d/networking restart' command fixed it...it does look like it's getting you an IP address, so the radio must be working to do that (unless the IP was on the ethernet card).

Does the card turn back on if you run these commands:

```
sudo modprobe -r iwl4965
sudo modprobe iwl4965
```

If not, how about:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn
```

It would also be helpful to see the output of:
```

lshw -C Network
modinfo iwl4965
modinfo iwlagn
```

---

### Post by substanceD on 2008-10-29
Cool! It looks like removing the module (iwl4965) and then adding it again does the trick. I'll put a script on my desktop for easy access.

Thanks for your help,
substanceD

---

### Post by PsyWolf on 2008-11-29
I'm having this problem too, and it is nice to see a workaround, but this didn't happen in Hardy, and despite the awesomeness of the new network manager, I don't expect regressions when i upgrade to the newest ubuntu.

---

### Post by tictactactics on 2008-12-01
I have this same problem right now except replacing iwl4965 and iwlagn does nothing.

lshw -C Network gives me....

```
lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:0b:20:2c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=128.101.185.214 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:36:17:03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:6e:1c:6d:06:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```


It seems to be detecting the wireless just fine, but the box for enabling wireless is greyed-out and I haven't found another way to try to enable it yet.

This is all after booting with the switch on, then switching it off, then back on.

---

### Post by pytheas22 on 2008-12-02
tictactactics: please post the output of these commands, in this order:
```

dmesg | grep -e iwl -e wlan -e adio
sudo ifconfig wlan0 up
lshw -C Network
sudo iwlist scan
sudo rmmod iwl3965
sudo modprobe iwl3965
sudo iwlist scan
```

That should help provide a clue as to what's going on so that we can fix it.

---

### Post by Clancy_s on 2008-12-03
Are you aware this is a known issue?  Per the release notes for intrepid: 

[i]**Cannot reactivate Intel 3945/4965 wireless if booting with killswitch enabled**

On laptops with Intel 3945 or Intel 4965 wireless chipsets and a killswitch for the wireless antenna, starting the system with the killswitch enabled (i.e., with wireless disabled) will prevent re-enabling the wireless by toggling the killswitch. As a workaround, users should boot the system with the killswitch disabled. A future kernel update is expected to address this issue. [/i]

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by mehellra on 2012-12-24
> **pytheas22 said:**
> tictactactics: please post the output of these commands, in this order:
```

dmesg | grep -e iwl -e wlan -e adio
sudo ifconfig wlan0 up
lshw -C Network
sudo iwlist scan
sudo rmmod iwl3965
sudo modprobe iwl3965
sudo iwlist scan
```

That should help provide a clue as to what's going on so that we can fix it.

I have had this problem with my laptop (VGN-SZ740) using Intel 4965 AGN, my prvious version of ubuntu was 9.10 and I have this problem unther that version too.
I have switched to 12.04 and the problem is still there
this link describe the problem related to  Intel 4965AGN and 3945ABG
[http://www.mydigitallife.info/intel-pro-wireless-3945abg-wifi-radio-adapter-shut-off-randomly/](http://www.mydigitallife.info/intel-pro-wireless-3945abg-wifi-radio-adapter-shut-off-randomly/)

recently I have bought a tenda usb wireless adaptor but I had the same problem for that card too, untill accidently I found out If I remove the iwl4965 modole (rmmod iwl4965) the problem will solve and my usb card will work for me!
any way to help you solve the issue for the next version. this is the output of requested commands

************************************************
[COLOR="Red"]**raha@laptop:~$ dmesg | grep -e iwl -e wlan -e adio**[/COLOR]
[   10.938207] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   10.938210] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   10.938265] iwl4965 0000:06:00.0: power state changed by ACPI to D0
[   10.938271] iwl4965 0000:06:00.0: power state changed by ACPI to D0
[   10.938284] iwl4965 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.938292] iwl4965 0000:06:00.0: setting latency timer to 64
[   10.938320] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   10.976831] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   10.977832] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.977920] iwl4965 0000:06:00.0: irq 46 for MSI/MSI-X
[   11.152750] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   11.602276] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   11.618079] Registered led device: rt2800usb-phy1::radio
[   19.408608] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.409430] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.876265] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.877482] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   24.364754] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[   24.366137] wlan1: authenticated
[   24.384024] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[   24.385509] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[   24.385513] wlan1: associated
[   24.393664] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   35.472032] wlan1: no IPv6 routers present
[   74.470997] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 1/3)
[   74.668028] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 2/3)
[   74.868026] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 3/3)
[   75.068026] wlan0: direct probe to 84:c9:b2:c5:15:08 timed out
[  139.910150] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 1/3)
[  140.108061] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 2/3)
[  140.308046] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 3/3)
[  140.512108] wlan0: direct probe to 84:c9:b2:c5:15:08 timed out
[  166.745298] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[  166.776033] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  166.776039] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  166.776042] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  166.780009] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[  166.780009] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[  166.780009] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[  166.780009] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[  167.442719] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[  168.795136] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  169.140727] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  169.426765] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  172.722845] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[  172.724481] wlan1: authenticated
[  172.729351] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[  172.730861] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[  172.730865] wlan1: associated
[  172.739424] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  184.624057] wlan1: no IPv6 routers present
[  224.549793] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 1/3)
[  224.748033] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 2/3)
[  224.948067] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 3/3)
[  225.148062] wlan0: direct probe to 84:c9:b2:c5:15:08 timed out
[  252.072156] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[  252.108039] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  252.108044] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  252.108047] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  252.112008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[  252.112008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[  252.112008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[  252.112008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[  252.441851] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  252.584332] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[  252.824800] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  253.088367] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  256.438091] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[  256.439613] wlan1: authenticated
[  256.456212] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[  256.457723] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[  256.457726] wlan1: associated
[  256.466465] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  266.560034] wlan1: no IPv6 routers present
[  277.461662] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 1/3)
[  277.660075] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 2/3)
[  277.860118] wlan0: direct probe to 84:c9:b2:c5:15:08 (try 3/3)
[  278.060075] wlan0: direct probe to 84:c9:b2:c5:15:08 timed out
[  402.609022] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[  402.632033] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  402.632037] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  402.632040] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  402.639643] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[  402.639643] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[  402.639643] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[  402.639643] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[  402.938964] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  410.778928] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[  411.023848] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  411.296560] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  414.652684] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[  414.654069] wlan1: authenticated
[  414.672072] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[  414.673571] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[  414.673574] wlan1: associated
[  414.681902] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  424.792057] wlan1: no IPv6 routers present
[  668.010938] wlan0: authenticate with 64:16:f0:7a:03:fb (try 1)
[  668.012390] wlan0: authenticated
[  668.012975] wlan0: associate with 64:16:f0:7a:03:fb (try 1)
[  668.015363] wlan0: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=2)
[  668.015372] wlan0: associated
[  668.045334] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  679.240055] wlan0: no IPv6 routers present
[  723.733166] wlan0: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  724.061736] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  796.580121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  796.860653] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  800.190585] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[  800.192102] wlan1: authenticated
[  800.212450] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[  800.213967] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[  800.213975] wlan1: associated
[  800.229351] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  801.344782] wlan0: authenticate with 64:16:f0:7a:03:fb (try 1)
[  801.346238] wlan0: authenticated
[  801.346370] wlan0: associate with 64:16:f0:7a:03:fb (try 1)
[  801.348101] wlan0: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=2)
[  801.348105] wlan0: associated
[  801.378622] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  810.384018] wlan1: no IPv6 routers present
[  812.496057] wlan0: no IPv6 routers present
[  946.691761] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[  946.691902] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.691910] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[  946.691927] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.691934] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  946.691941] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  946.691948] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.691954] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  946.691964] wlan0: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  946.712070] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.712075] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[  946.712079] iwl4965 0000:06:00.0: Error removing station 64:16:f0:7a:03:fb
[  946.712377] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.712380] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[  946.712387] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.712389] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[  946.712406] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.712408] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  946.712410] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  946.720037] iwl4965 0000:06:00.0: Not sending command - RF KILL
[  946.720039] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  946.720041] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[  946.724026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[  946.724026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[  946.724026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[  946.724026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[  946.752410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  947.042287] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[  949.669632] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[  949.905141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  950.176396] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  953.513801] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[  953.515685] wlan1: authenticated
[  953.535651] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[  953.539408] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[  953.539411] wlan1: associated
[  953.547733] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  954.692508] wlan0: authenticate with 64:16:f0:7a:03:fb (try 1)
[  954.693471] wlan0: authenticated
[  954.693609] wlan0: associate with 64:16:f0:7a:03:fb (try 1)
[  954.695295] wlan0: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=2)
[  954.695300] wlan0: associated
[  954.729430] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  963.896027] wlan1: no IPv6 routers present
[  966.384024] wlan0: no IPv6 routers present
[ 1045.096018] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 1045.096155] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.096164] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 1045.096181] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.096188] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 1045.096195] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 1045.096202] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.096208] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 1045.096217] wlan0: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[ 1045.124107] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.124114] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[ 1045.124121] iwl4965 0000:06:00.0: Error removing station 64:16:f0:7a:03:fb
[ 1045.124270] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.124275] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 1045.124285] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.124290] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 1045.124297] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.124301] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 1045.124306] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 1045.132103] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 1045.132108] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 1045.132113] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 1045.136078] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[ 1045.136078] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[ 1045.136078] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[ 1045.136078] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[ 1045.362078] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1045.678695] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[ 1071.017024] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[ 1071.259326] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1071.544628] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1074.885454] wlan1: authenticate with 64:16:f0:7a:03:fb (try 1)
[ 1074.886956] wlan1: authenticated
[ 1074.904314] wlan1: associate with 64:16:f0:7a:03:fb (try 1)
[ 1074.905833] wlan1: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=1)
[ 1074.905836] wlan1: associated
[ 1074.914130] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1076.036870] wlan0: authenticate with 64:16:f0:7a:03:fb (try 1)
[ 1076.039214] wlan0: authenticated
[ 1076.039378] wlan0: associate with 64:16:f0:7a:03:fb (try 1)
[ 1076.041067] wlan0: RX AssocResp from 64:16:f0:7a:03:fb (capab=0x431 status=0 aid=2)
[ 1076.041070] wlan0: associated
[ 1076.068473] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1085.904029] wlan1: no IPv6 routers present
[ 1087.120035] wlan0: no IPv6 routers present
[ 2388.698614] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 2388.698748] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.698757] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 2388.698773] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.698780] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2388.698787] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2388.698793] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.698800] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 2388.698810] wlan0: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[ 2388.720470] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.720480] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[ 2388.720489] iwl4965 0000:06:00.0: Error removing station 64:16:f0:7a:03:fb
[ 2388.728204] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.728214] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 2388.728227] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.728234] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 2388.728246] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.728252] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2388.728259] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2388.736058] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2388.736061] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2388.736064] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2388.740047] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[ 2388.740047] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[ 2388.740047] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[ 2388.740047] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[ 2388.967882] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2389.292776] wlan1: deauthenticating from 64:16:f0:7a:03:fb by local choice (reason=3)
[COLOR="Red"]raha@laptop:~$ sudo ifconfig wlan0 up[/COLOR]
SIOCSIFFLAGS: Operation not possible due to RF-kill
[COLOR="Red"]raha@laptop:~$ lshw -C Network[/COLOR]
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:0b:52:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-29-generic-pae firmware=228.61.2.24 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:1a:80:d2:16:3c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.2.110 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fa000000-fa003fff ioport:4000(size=256) memory:f4000000-f401ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1
       logical name: wlan1
       serial: c8:3a:35:cd:02:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-29-generic-pae firmware=0.29 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
[COLOR="Red"]raha@laptop:~$ sudo iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

[COLOR="Red"]raha@laptop:~$ sudo rmmod iwl4965
raha@laptop:~$ sudo modprobe iwl4965
raha@laptop:~$ sudo iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

*************************************************

---

