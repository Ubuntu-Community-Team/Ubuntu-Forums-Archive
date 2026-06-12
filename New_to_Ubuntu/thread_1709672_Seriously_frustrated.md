---
title: "Seriously frustrated"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by hellsbrink on 2011-03-18
[SIZE=2]Hi all.

Ok, have done a new install of Ubuntu Maverick Meerkat and I have a problem which is seriously peeing me off.

I'm using a Sitecom WL-302 wifi dongle, and, for no reason, the connection just disappears and the only way I can get it back is to disable networking, enable networking and then let it reconnect as it will not reconnect "normally". You can guess how annoying this is, especially as it can sometimes be about 1 min when the connection shuts down, and that screws up any updates or anything I am doing.

Anyone have any suggestions on what to do on about this because I'm now at the point of wiping Ubuntu and getting another Linux distro in the hope something as simple as a wifi dongle works properly.

FYI. There has never been an issue with WinXP or Win7, the connection will stay "up" for days with no issues.
[/SIZE]

---

### Post by josephmills on 2011-03-18
Hi there and Welcome to Ubuntu! Have you tried going to network connections? System-->Pref-->network connections . click on your network then see if it connects auto. and also see what the loop back is. Are you using the right driver or are you using "bleeding edge" driver? go to termainal and type in 
```

lspci -vnn | grep 14e4

```
copy and paste that here do we can see what kind of driver that you are using
Also have you updated and upgraded yet?

---

### Post by hellsbrink on 2011-03-18
Joseph

First, that command gave me nothing in reply

Now, my connection. It will autoconnect on startup and after I disable/enable networking but when the connection drops it will not connect at all, it keeps "looping" to the "password" dialogue box for the connection despite that being in the connection preferences. The only way I can connect is to disable and then enable networking.

Updates? The connection won't stay up long enough to update fully.....

Thx

---

### Post by Lateralis on 2011-03-18
Hmmm... that looping to the password dialogue box reminds me of a problem I had with my laptop at a laboratory I worked at last year doing some experiments for work.  I never did fully work out what the problem was, but I believe the problem was with the wireless network infrastructure (the signal was weak and made use of a secure login which was pants) as opposed to my laptop.  

So, first of all, what kind of network are you connecting to, i.e. a home network setup by you or family/housemates or something else?  In either case are there other users on the network that have problems?  Finally, have you tried using the dongle in Windows or another OS?

---

### Post by hellsbrink on 2011-03-18
It's a home network, and the router is on the other side of the room.

Have two other Win7 machines that use the network, and a Wii, and they have no issues. This machine is a dual boot Win7/maverick and there is no issue with the dongle and drops in connections on Win7 or when it was running XP, it's only now I have this "how long will it last" problem and only on Ubuntu.

---

### Post by josephmills on 2011-03-18
> **hellsbrink said:**
> Joseph

First, that command gave me nothing in reply

Now, my connection. It will autoconnect on startup and after I disable/enable networking but when the connection drops it will not connect at all, it keeps "looping" to the "password" dialogue box for the connection despite that being in the connection preferences. The only way I can connect is to disable and then enable networking.

Updates? The connection won't stay up long enough to update fully.....

Thx

sorry about that go back to your termanial and just type in ```
 lspci 
``` and then paste that here

---

### Post by hellsbrink on 2011-03-18
Joseph.

Here's the report, can't see my "dongle" in that list........

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)


---

### Post by josephmills on 2011-03-18
ok plug in your eth0 and update and upgrade 
```
sudo apt-get upgrade
```
```
sudo apt-get update 
```
also when you type in ```
ifconfig
```is your mac address # weird?

---

### Post by hellsbrink on 2011-03-18
No need for that, got updates (eventually) and I ain't in the mood to run a cat5 across to the other side of the room at 2252CET!

But even after first batch of updates, it still drops....

Mac address # is perfect, exactly what it should be (and no mac filtering is turned on on router so it ain't that)

---

### Post by sandyd on 2011-03-18
post output of
```

lsusb
```
lspci only lists pci devices.

---

### Post by hellsbrink on 2011-03-19
Yeah, I figured that out earlier and checked, ID's my wifi dongle perfectly

>  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0df6:002d Sitecom Europe B.V. WL-302 Wireless Network 300N USB dongle 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by hellsbrink on 2011-03-19
> sudo lshw -C network

gives me this


>   *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:0c:f1:a2:09:e8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:feaff000-feafffff ioport:bc00(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:0c:f6:5b:f5:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.102 link=yes multicast=yes wireless=IEEE 802.11bgn

---

### Post by jtarin on 2011-03-19
Check the output of the commands
```
dmesg
```
and
```
tail /var/log/kern.log
```

for any errors related to the rt2800 driver or eth0 device. If you see anything interesting, post it.

---

### Post by hellsbrink on 2011-03-19
First, dmesg. And it's a big one.

[>    19.244161] Registered led device: rt2800usb-phy0::radio
[   19.244224] Registered led device: rt2800usb-phy0::assoc
[   19.244270] Registered led device: rt2800usb-phy0::quality
[   19.244905] usbcore: registered new interface driver rt2800usb
[   19.247315] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.277372] rtusb init --->
[   19.279507] usbcore: registered new interface driver rt2870
[   19.500035] intel8x0_measure_ac97_clock: measured 58220 usecs (2804 samples)
[   19.500041] intel8x0: clocking to 48000
[   20.720319] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   20.765085] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   20.983249] type=1400 audit(1300510219.823:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=888 comm="apparmor_parser"
[   20.984384] type=1400 audit(1300510219.827:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=888 comm="apparmor_parser"
[   21.118782] type=1400 audit(1300510219.959:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=920 comm="apparmor_parser"
[   21.119615] type=1400 audit(1300510219.959:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=920 comm="apparmor_parser"
[   21.120083] type=1400 audit(1300510219.963:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=920 comm="apparmor_parser"
[   21.134201] type=1400 audit(1300510219.975:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=919 comm="apparmor_parser"
[   21.184142] type=1400 audit(1300510220.027:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=988 comm="apparmor_parser"
[   21.513942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.604417] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   21.604450] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   21.604527] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   21.627037] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.215912] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   24.161155] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   35.883491] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[   35.885562] wlan0: authenticated
[   35.886842] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[   35.889544] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[   35.889553] wlan0: associated
[   35.893614] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.192033] wlan0: no IPv6 routers present
[  736.548034] No probe response from AP 00:25:f1:e7:99:aa after 500ms, disconnecting.
[  736.597101] cfg80211: All devices are disconnected, going to restore regulatory settings
[  736.597118] cfg80211: Restoring regulatory settings
[  736.597128] cfg80211: Calling CRDA to update world regulatory domain
[  736.609531] cfg80211: World regulatory domain updated:
[  736.609544]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  736.609551]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  736.609558]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  736.609563]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  736.609568]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  736.609574]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  738.015627] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[  738.212031] wlan0: authenticate with 00:25:f1:e7:99:aa (try 2)
[  738.412039] wlan0: authenticate with 00:25:f1:e7:99:aa (try 3)
[  738.614614] wlan0: authentication with 00:25:f1:e7:99:aa timed out
[  749.358532] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  749.556033] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  749.756034] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  749.957030] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  753.882747] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  754.080035] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  754.280033] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  754.481019] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  765.214712] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  765.412041] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  765.612030] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  765.812030] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  776.539663] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  776.737079] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  776.936022] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  777.136021] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  787.864281] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  788.064041] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  788.264031] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  788.464030] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  799.187061] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[  799.384031] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[  799.584036] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[  799.784041] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[  813.466625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  813.490960] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  816.170727] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[  816.172379] wlan0: authenticated
[  816.173234] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[  816.175603] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[  816.175608] wlan0: associated
[  816.179515] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  826.464018] wlan0: no IPv6 routers present
[ 1476.445105] wlan0: deauthenticated from 00:25:f1:e7:99:aa (Reason: 7)
[ 1476.501242] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1476.501258] cfg80211: Restoring regulatory settings
[ 1476.501267] cfg80211: Calling CRDA to update world regulatory domain
[ 1476.580541] cfg80211: World regulatory domain updated:
[ 1476.580553]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1476.580560]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1476.580566]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1476.580573]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1476.580578]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1476.580586]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1477.951011] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 1477.952735] wlan0: authenticated
[ 1477.953543] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[ 1477.955968] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[ 1477.955978] wlan0: associated
[ 1777.487166] wlan0: deauthenticated from 00:25:f1:e7:99:aa (Reason: 7)
[ 1777.541097] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1777.541115] cfg80211: Restoring regulatory settings
[ 1777.541126] cfg80211: Calling CRDA to update world regulatory domain
[ 1777.550005] cfg80211: World regulatory domain updated:
[ 1777.550011]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1777.550016]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1777.550021]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1777.550025]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1777.550028]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1777.550032]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1778.947090] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 1779.144045] wlan0: authenticate with 00:25:f1:e7:99:aa (try 2)
[ 1779.344022] wlan0: authenticate with 00:25:f1:e7:99:aa (try 3)
[ 1779.544041] wlan0: authentication with 00:25:f1:e7:99:aa timed out
[ 1808.334561] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1808.355061] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1819.737200] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 1819.738874] wlan0: authenticated
[ 1819.739670] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[ 1819.742058] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[ 1819.742063] wlan0: associated
[ 1819.751622] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1830.184022] wlan0: no IPv6 routers present
[ 1873.589946] No probe response from AP 00:25:f1:e7:99:aa after 500ms, disconnecting.
[ 1873.653167] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1873.653182] cfg80211: Restoring regulatory settings
[ 1873.653193] cfg80211: Calling CRDA to update world regulatory domain
[ 1873.689214] cfg80211: World regulatory domain updated:
[ 1873.689222]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1873.689228]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1873.689234]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1873.689239]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1873.689245]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1873.689250]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1875.066986] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 1875.264031] wlan0: authenticate with 00:25:f1:e7:99:aa (try 2)
[ 1875.464031] wlan0: authenticate with 00:25:f1:e7:99:aa (try 3)
[ 1875.664030] wlan0: authentication with 00:25:f1:e7:99:aa timed out
[ 1886.447107] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1886.645119] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1886.845101] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1887.045103] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1890.953591] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1891.152464] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1891.353080] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1891.553107] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1902.329466] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1902.529037] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1902.729036] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1902.929060] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1913.672731] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1913.873530] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1914.072137] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1914.272046] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1924.998276] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1925.196028] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1925.396028] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1925.597051] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1936.324148] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1936.524070] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1936.725087] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1936.925024] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1947.643550] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1947.840036] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1948.041145] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1948.240028] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1953.895642] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1954.093021] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1954.292048] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1954.492032] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1965.215772] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1965.412024] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1965.612023] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1965.812021] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1976.533867] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1976.733029] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1976.932021] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1977.133027] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1987.847778] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1988.044048] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1988.244043] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1988.444032] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 1999.172442] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 1999.373052] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 1999.572370] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 1999.773042] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 2010.494967] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2010.692035] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 2010.892045] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 2011.092042] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 2333.545585] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2333.570933] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2344.910989] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2344.913636] wlan0: direct probe responded
[ 2344.919801] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 2344.921599] wlan0: authenticated
[ 2344.922448] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[ 2344.924830] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[ 2344.924835] wlan0: associated
[ 2344.934244] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2355.873058] wlan0: no IPv6 routers present
[ 2358.585028] No probe response from AP 00:25:f1:e7:99:aa after 500ms, disconnecting.
[ 2358.633114] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2358.633130] cfg80211: Restoring regulatory settings
[ 2358.633140] cfg80211: Calling CRDA to update world regulatory domain
[ 2358.645850] cfg80211: World regulatory domain updated:
[ 2358.645861]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2358.645868]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2358.645874]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2358.645879]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2358.645885]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2358.645891]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2360.046950] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 2360.244041] wlan0: authenticate with 00:25:f1:e7:99:aa (try 2)
[ 2360.444037] wlan0: authenticate with 00:25:f1:e7:99:aa (try 3)
[ 2360.644024] wlan0: authentication with 00:25:f1:e7:99:aa timed out
[ 2371.367662] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2371.564033] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 2371.764030] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 2371.964028] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 2393.398739] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2393.430880] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2394.799095] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2394.997035] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 2394.999619] wlan0: direct probe responded
[ 2395.012136] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 2395.014013] wlan0: authenticated
[ 2395.014951] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[ 2395.018918] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[ 2395.018929] wlan0: associated
[ 2395.028582] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2405.560023] wlan0: no IPv6 routers present
[ 2518.584030] No probe response from AP 00:25:f1:e7:99:aa after 500ms, disconnecting.
[ 2518.636153] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2518.636173] cfg80211: Restoring regulatory settings
[ 2518.636182] cfg80211: Calling CRDA to update world regulatory domain
[ 2518.680394] cfg80211: World regulatory domain updated:
[ 2518.680401]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2518.680406]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2518.680411]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2518.680415]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2518.680419]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2518.680422]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2520.047060] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 2520.244030] wlan0: authenticate with 00:25:f1:e7:99:aa (try 2)
[ 2520.444532] wlan0: authenticate with 00:25:f1:e7:99:aa (try 3)
[ 2520.644968] wlan0: authentication with 00:25:f1:e7:99:aa timed out
[ 2531.389856] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2531.588039] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 2531.788035] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 2531.988046] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 2535.883841] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2536.080038] wlan0: direct probe to 00:25:f1:e7:99:aa (try 2)
[ 2536.280417] wlan0: direct probe to 00:25:f1:e7:99:aa (try 3)
[ 2536.481043] wlan0: direct probe to 00:25:f1:e7:99:aa timed out
[ 2544.390290] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2544.419944] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2555.805933] wlan0: direct probe to 00:25:f1:e7:99:aa (try 1)
[ 2555.808425] wlan0: direct probe responded
[ 2555.817056] wlan0: authenticate with 00:25:f1:e7:99:aa (try 1)
[ 2555.818799] wlan0: authenticated
[ 2555.819535] wlan0: associate with 00:25:f1:e7:99:aa (try 1)
[ 2555.821947] wlan0: RX AssocResp from 00:25:f1:e7:99:aa (capab=0x411 status=0 aid=1)
[ 2555.821953] wlan0: associated
[ 2555.833210] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2565.952221] wlan0: no IPv6 routers present

---

### Post by ~Hinterland on 2011-03-19
I had this trouble, although with a different card. 

Changing the channel in the router from Auto to a specific one sorted the problem for me - it seemed to be WPA2 not re-associating when the channel changed.

---

### Post by hellsbrink on 2011-03-19
Router is set to a specific channel after checking what neighbouring networks are set on so I don't get "interference. It's the first thing I do when I set up one, "auto" is never in use.

Back on Win7 now, this random connection drop every 1-10 mins is beyond my patience.

---

### Post by jtarin on 2011-03-19
According to [Hardware for Linux]("http://hardware4linux.info/component/14976/") this should work out of the box with the e100 module.
Execute the command ```
lsmod
``` in the terminal and see if its listed. If not you might try it and remove the rt2800.

---

### Post by hellsbrink on 2011-03-21
problem is "solved". I wiped out Ubuntu and installed PCLOS instead. There are absolutely no issues with the wifi dongle on PCLOS so it's obvious the problem is with Ububtu.

Obviously that is something that must get sorted out as it isn't a "new" chipset, it isn't something that hasn't caused issues before, they've dropped the ball on compatibility regarding this wifi chipset as something is definitely wrong with the way Ubuntu "works" with this adapter.

---

### Post by jtarin on 2011-03-21
> **hellsbrink said:**
> problem is "solved". I wiped out Ubuntu and installed PCLOS instead. There are absolutely no issues with the wifi dongle on PCLOS so it's obvious the problem is with Ububtu.

Obviously that is something that must get sorted out as it isn't a "new" chipset, it isn't something that hasn't caused issues before, they've dropped the ball on compatibility regarding this wifi chipset as something is definitely wrong with the way Ubuntu "works" with this adapter.I'm curious as to whether you checked the module or not. Best guesses by any OS at what driver it should load are not always optimum.

---

