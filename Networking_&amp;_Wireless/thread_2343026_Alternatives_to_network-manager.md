---
title: "Alternatives to network-manager?"
date: 2016-11-12
forum: Networking &amp; Wireless
---

### Post by shersk on 2016-11-12
Are there any alternatives to network-manager? 

I have several issues with it, and if there's an alternative application, I would rather switch to that, than begin investigating why it's not working (though the community probably would prefer to solve the issues).

My issues are about bonding of network interfaces (poorly documented) and configuration of mac addresses messing up things.

---

### Post by ajgreeny on 2016-11-12
Try **wicd**, though I do not know if it will help with your specific problem.

---

### Post by shersk on 2016-11-12
The last problem is with using a Ralink RT2870 usb wireless card and trying to set a specific (cloned) mac address. Whenever I do this (tested against many different routers), the wireless device disconnects, with the error code 3 (which apparently means radio button off). 

When inserting the usb device:
```
[13092.229636] usb 2-2: USB disconnect, device number 3
[13098.869782] usb 2-2: new high-speed USB device number 8 using xhci_hcd
[13099.071148] usb 2-2: New USB device found, idVendor=[COLOR=#ff0000]148f[/COLOR], idProduct=[COLOR=#ff0000]3070[/COLOR]
[13099.071152] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[13099.071155] usb 2-2: Product: 802.11 n WLAN
[13099.071157] usb 2-2: Manufacturer: Ralink
[13099.071159] usb 2-2: SerialNumber: 1.0
[13099.237969] usb 2-2: reset high-speed USB device number 8 using xhci_hcd
[13099.432524] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[13099.442298] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 0005 detected
[13099.442660] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[13100.817417] rt2800usb 2-2:1.0 wlxXXXXXXXXXXXX: renamed from wlan0
[13100.939545] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[13100.939611] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file '[COLOR=#ff0000]rt2870.bin[/COLOR]'
[13101.227402] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[13101.432961] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[13101.469939] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[13181.518348] usb 2-4: reset full-speed USB device number 5 using xhci_hcd



```

When connecting to the access point:
```
[15164.293346] cfg80211: World regulatory domain updated:
[15164.293351] cfg80211:  DFS Master region: unset
[15164.293352] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[15164.293355] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[15164.293357] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[15164.293359] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[15164.293361] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[15164.293363] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[15164.293365] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[15164.293367] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[15164.293368] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[15175.806741] IPv6: ADDRCONF(NETDEV_UP): wlxXXXXXXXXXXXX: link is not ready
[15177.008033] wlxXXXXXXXXXXXX: authenticate with 00:00:00:00:00:00
[15177.042088] wlxXXXXXXXXXXXX: send auth to 00:00:00:00:00:00 (try 1/3)
[15177.046426] wlxXXXXXXXXXXXX: authenticated
[15182.043739] wlxXXXXXXXXXXXX: aborting authentication with 00:00:00:00:00:00 by local choice (Reason: 3=DEAUTH_LEAVING)



```

I have tested and confirmed that I can connect to the same access points with a different wireless device, using the same credentials and same cloned mac address from the same computer. I have also tested connecting to the same access points with the problem device, using the same credentials and the original mac address, and that works too. Empirically, it seems that the problem is connected to setting a cloned mac address with this wireless card and the driver setup provided by ubuntu 16.04.

---

### Post by chili555 on 2016-11-12
> with a different wireless deviceThen why do you think the answer is Network Manager and not the specific Ralink driver and firmware? Network Manager can only do what the hardware and software allow. In this case, based on a few years experience with Linux wireless, it is probably the driver and firmware.

There is one thing you might try, aside from a browse at Amazon. There is an available driver parameter that you might try:```
sudo -i
echo "options rt2800usb nohwcrypt=Y"  >  /etc/modprobe.d/rt2800usb.conf
modprobe -r rt2800usb
modprobe rt2800usb
exit
```Any improvement? It may take a reboot.

---

### Post by shersk on 2016-11-12
No, that didn't work, but thanks for the effort.

The other issue I have with network-manager is connection bonding, which is one of the options to choose from in the menu, but isn't properly documented. Bonding is explained in Ubuntu's general documentation, but the information is outdated and does not involve network-manager. To get it working with wireless, I suppose it's necessary to involve wpa_supplicant, and that might be where I go wrong when I try to guess how to set it up in network-manager.

---

