---
title: "Gigaset 108 wpa verification fails"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by eekie on 2008-08-22
I am running ubuntu 8.04 on a box in my lan too remote for cabled network and connected and installed a gigaset 108 usb adapter for wireless connection to my SpeedTouch CDE530. I installed using ndiswrapper the xp driver ar5523.inf.
Of course I have the problem of having to give the command: modprobe ndiswrapper every start-up in order to see the wireless network(s). But that is a minor flaw. If I try to connect to my wireless network it asks for the WPA key. I give the 10 character key from the backside of my modem, but it fails to connect and asks again for my WPA key. 
In order to enable sending the Dmesg information I have a network cable inserted as well.
Dmesg gives the following information:

[  161.786880] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  161.991202] usb 5-4: reset high speed USB device using ehci_hcd and address 2
[  162.149660] ndiswrapper: driver net5523 (,07/27/2005,1.5.0.102) loaded
[  162.152434] ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
[  162.456186] wlan0: ethernet device 00:01:e3:c1:a8:1d using NDIS driver: net5523, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 129B:160C.F.conf
[  162.516503] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  162.516595] usbcore: registered new interface driver ndiswrapper
[  162.529717] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  201.635105] NET: Registered protocol family 17
[  207.002832] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  217.453366] wlan0: no IPv6 routers present
[  705.687521] PPP generic driver version 2.4.2
[  705.695588] NET: Registered protocol family 24
[  772.954358] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  772.954367] tg3: eth0: Flow control is off for TX and off for RX.
[  772.957045] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  783.452149] eth0: no IPv6 routers present
[  919.573100] eth0: no IPv6 routers present

Contrary to the computer my modem does not see the wifi connection.
The wifi connection works fine under windows xp

Anybody knows how to solve this problem?

---

