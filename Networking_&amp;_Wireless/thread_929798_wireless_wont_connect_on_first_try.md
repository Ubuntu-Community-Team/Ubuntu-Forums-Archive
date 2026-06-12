---
title: "wireless wont connect on first try"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by roman5x3 on 2008-09-25
My wireless on my my fresh install of 8.08 and fully updated (using gui update manager), will not connect on my first try.  It always connects on the second. The biggest problem is the main user of this laptop is my mom who is not real knowledgeable of computers and when it asks the second time it erases the hex code (I can not get the password to work at all) and it has to be pasted back in.  This is unacceptable for her.

my lspci
```

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```
Roman5x3

---

### Post by pytheas22 on 2008-09-25
I used to have issues like this on a Ralink card--it only connected on the second try, even though the signal was strong, etc.  I never solved them, just found workarounds...

But one possible solution would be for you to use [wicd]("http://wicd.sourceforge.net") to connect instead of Network Manager.  If the problem is the fault of NM (quite possible), this would help.

If that doesn't work, you could probably write a bash script to connect you automatically when you log in--it could just try twice.  First you'd need to figure out which command connects, you though, so that you could put it into a script and have it run whenever you turn on the computer (or whenever you log into the desktop).  Generally you can connect to WEP networks using a command like:
```

sudo iwconfig wlan0 mode managed channel [channel number] essid [network name, in quotes] key [hex key, in quotes]
sudo dhclient wlan0
```

If that doesn't connect you, please post the output of:

```
sudo iwlist scan
```

---

### Post by willca on 2008-09-26
Sounds like you have WEP enabled?

Try this out if it is WEP.

Edit /etc/network/interfaces

auto wlan0
iface inet wlan0 dhcp
wireless-essid youressid
wireless-key yourkey

Save and do this.
sudo /etc/init.d/networking restart

---

### Post by roman5x3 on 2008-09-26
> **willca said:**
> Sounds like you have WEP enabled?

Try this out if it is WEP.

Edit /etc/network/interfaces

auto wlan0
iface inet wlan0 dhcp
wireless-essid youressid
wireless-key yourkey

Save and do this.
sudo /etc/init.d/networking restart

It tried this and got the following from dmesg (from first sign of wireless from boot:
```

[  211.630626] wifi0: LinkStatus=2 (Disconnected)
[  211.651415] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   62.801439] Bluetooth: Core ver 2.11
[   62.802707] NET: Registered protocol family 31
[   62.802716] Bluetooth: HCI device and connection manager initialized
[   62.802723] Bluetooth: HCI socket layer initialized
[   62.843120] Bluetooth: L2CAP ver 2.9
[   62.843131] Bluetooth: L2CAP socket layer initialized
[   62.882984] Bluetooth: RFCOMM socket layer initialized
[   62.883432] Bluetooth: RFCOMM TTY layer initialized
[   62.883437] Bluetooth: RFCOMM ver 1.8
[  215.188383] wifi0: LinkStatus=1 (Connected)
[  215.189171] wifi0: LinkStatus: BSSID=00:14:bf:1e:49:62
[   64.445350] [drm] Initialized drm 1.1.0 20060810
[   64.558963] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   64.559359] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  220.131442] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  220.132425] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  220.133011] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[  221.431877] [drm] Setting GART location based on new memory map
[  221.431957] [drm] writeback test succeeded in 1 usecs
[  621.381843] NET: Registered protocol family 10
[  621.383486] lo: Disabled Privacy Extensions
[  621.385418] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  189.770300] wlan0: no IPv6 routers present
[  195.728077] NET: Registered protocol family 17
[  196.779268] ieee80211_crypt: registered algorithm 'WEP'
[  197.179575] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[  197.179587] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
[  197.181959] wifi0: LinkStatus=2 (Disconnected)
[  197.182156] wifi0: LinkStatus: BSSID=00:14:bf:1e:49:62
[  197.203840] wifi0: LinkStatus=2 (Disconnected)
[  197.217165] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  197.247072] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  197.599828] wifi0: LinkStatus=1 (Connected)
[  197.600358] wifi0: LinkStatus: BSSID=00:14:bf:1e:49:62

```
and here is the output from running the restart:
```

 * Reconfiguring network interfaces...                                         /etc/network/interfaces:5: unknown address type
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:5: unknown address type
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                        [fail]

```

---

### Post by roman5x3 on 2008-09-26
pytheas22:
How do I install wicd.  What repository do I need to add because I searched for it in synaptic and could not find anything.
Roman5x3

---

### Post by pytheas22 on 2008-09-27
You can find instructions for installing wicd in Ubuntu [here]("http://wicd.sourceforge.net/download.php").  You have to add the wicd repository before you can download it, but it's not hard to do.

Please let us know if wicd helps.  I'm unfortunately travelling right now and probably won't be able to respond again till later tomorrow, but if you still haven't solved the problem by then, we can figure it out.  I do notice from your dmesg output that your computer seems to think at first that the MAC address of your router is 44:44:44:44:44:44, which doesn't seem valid, so I suspect that the problem lies somewhere around there.

---

### Post by roman5x3 on 2008-09-28
Putting the info into the startup script seemed to give it its first attempt at startup and when I login it connects just fine so thanx for the help.

Roman5x3

---

### Post by barracuda9000 on 2011-06-07
I'm having the exact same problem. And if you think Network Manager is bad, wicd is even worse. It won't connect period.

I'm convinced it has something to do with the router security. Does anybody know where i can ask an expert for a solution to this problem?

---

### Post by pytheas22 on 2011-06-08
barracuda9000: I'd be happy to try to help if you provide more information.  It would be helpful to know the details of your problem (what exactly is not working?) and the output of the following commands, so I'll know what kind of hardware you have, etc.:
```

iwconfig
sudo iwlist scan
dmesg | grep wlan
lshw -C Network
lspci -nn
lsusb
```

---

