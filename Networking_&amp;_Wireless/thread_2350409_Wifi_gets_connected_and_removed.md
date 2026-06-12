---
title: "Wifi gets connected and removed"
date: 2017-01-24
forum: Networking &amp; Wireless
---

### Post by alexander15454 on 2017-01-24
Hey guys.

Today i got my new Alfa AWUS052NH and plugged into my PC.

I can see it for 1-2 seconds in ifconfig under the name wlan1 and then it disappears and pops up again after some time in a endless loop.

Some things from dmesg:

```
  385.526761] usb 3-1: new high-speed USB device number 127 using xhci_hcd[  390.822362] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[  396.421936] usb 3-1: new high-speed USB device number 6 using xhci_hcd
[  401.749530] usb 3-1: new high-speed USB device number 7 using xhci_hcd
[  407.333105] usb 3-1: new high-speed USB device number 9 using xhci_hcd
[  412.628707] usb 3-1: new high-speed USB device number 10 using xhci_hcd
[  417.924295] usb 3-1: new high-speed USB device number 11 using xhci_hcd
[  423.467874] usb 3-1: new high-speed USB device number 13 using xhci_hcd
[  428.763469] usb 3-1: new high-speed USB device number 14 using xhci_hcd
[  434.091070] usb 3-1: new high-speed USB device number 15 using xhci_hcd
[  439.386664] usb 3-1: new high-speed USB device number 16 using xhci_hcd
[  444.682263] usb 3-1: new high-speed USB device number 17 using xhci_hcd
[  450.233838] usb 3-1: new high-speed USB device number 19 using xhci_hcd
[  455.937403] usb 3-1: new high-speed USB device number 21 using xhci_hcd



```

```
[  220.011332] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110[  220.056018] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.056021] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  220.056023] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.081062] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.081067] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  220.081069] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.115404] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  220.179765] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.179770] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  220.179771] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.189169] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.189174] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  220.189175] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.219306] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  220.286256] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.286259] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  220.286261] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.316283] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.316289] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  220.316291] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.323367] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  220.410008] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.410012] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  220.410014] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.427361] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  220.434424] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.434428] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  220.434430] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.531290] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  220.536621] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.536625] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  220.536627] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.563528] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.563532] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  220.563533] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.635345] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  220.664345] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.664349] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  220.664350] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.674937] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.674942] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  220.674943] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.739272] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  220.771454] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.771457] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  220.771458] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.796546] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.796551] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  220.796552] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.843328] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  220.886607] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.886611] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  220.886613] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.897562] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  220.897567] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  220.897568] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  220.947316] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  220.983383] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  220.983388] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  220.983389] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.008432] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  221.008436] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  221.008437] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.051314] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  221.082423] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 78
[  221.082427] evbug: Event. Dev: input4, Type: 1, Code: 78, Value: 1
[  221.082428] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.097052] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  221.097056] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  221.097057] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.131482] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  221.131486] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  221.131488] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.155270] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  221.259301] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  221.283570] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  221.283574] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  221.283576] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.294288] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 78
[  221.294292] evbug: Event. Dev: input4, Type: 1, Code: 78, Value: 0
[  221.294293] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.363288] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  221.467287] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  221.571275] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  221.649800] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  221.649804] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  221.649806] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.675266] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  221.750537] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  221.750541] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  221.750542] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.779263] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  221.883254] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  221.984879] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  221.984883] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  221.984884] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  221.987204] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  222.076292] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  222.076297] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  222.076299] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.091234] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  222.176509] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  222.176514] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  222.176516] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.195227] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  222.265235] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  222.265239] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  222.265241] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.299226] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  222.403214] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  222.507205] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  222.576975] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  222.576979] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  222.576981] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.611192] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  222.684106] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  222.684110] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  222.684111] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.715192] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  222.819182] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  222.867847] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  222.867852] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  222.867853] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  222.923171] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  222.994886] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  222.994891] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  222.994892] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.027165] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  223.054793] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.054798] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  223.054799] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.131155] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  223.178337] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.178342] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  223.178344] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.183692] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.183696] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  223.183698] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.235088] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  223.305775] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.305779] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  223.305780] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.315880] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.315884] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  223.315886] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.339154] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  223.404479] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.404483] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  223.404484] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.424499] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.424503] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  223.424504] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.443090] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  223.531701] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.531705] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  223.531707] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.547124] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  223.548608] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.548612] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  223.548613] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.642294] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  223.642299] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  223.642300] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.651115] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  223.652290] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.652294] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  223.652295] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.755098] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  223.823392] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  223.823396] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 0
[  223.823397] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  223.859102] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  223.963088] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  224.067087] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  224.171078] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  224.275069] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  224.379063] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  224.483058] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  224.587042] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  224.691039] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  224.795036] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  224.899062] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  225.003014] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  225.107006] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  225.210998] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  225.314990] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  225.418985] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  225.522975] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  225.626968] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  225.730955] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  225.834950] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  225.938938] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0580 with error -110
[  226.042940] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -110
[  226.146931] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x059c with error -110
[  226.250929] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0598 with error -110
[  226.354912] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0594 with error -110
[  226.458904] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0590 with error -110
[  226.458911] ieee80211 phy22: rt2x00_set_rf: Info - RF chipset 0009 detected
[  226.562917] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0228 with error -110
[  226.666885] ieee80211 phy22: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0228 with error -110
[  226.667072] ieee80211 phy22: Selected rate control algorithm 'minstrel_ht'
[  226.667605] usb 3-1: USB disconnect, device number 79
[  227.006835] usb 3-1: new high-speed USB device number 80 using xhci_hcd
[  227.206940] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  227.206944] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  227.206946] usb 3-1: Product: 802.11 n WLAN
[  227.206947] usb 3-1: Manufacturer: Ralink
[  227.206948] usb 3-1: SerialNumber: 1.0
[  227.375033] usb 3-1: reset high-speed USB device number 80 using xhci_hcd
[  227.568340] ieee80211 phy23: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  227.578869] ieee80211 phy23: rt2x00_set_rf: Info - RF chipset 0009 detected
[  227.579145] ieee80211 phy23: Selected rate control algorithm 'minstrel_ht'
[  227.610278] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  227.610317] ieee80211 phy23: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  227.610338] ieee80211 phy23: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  227.967548] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  228.005731] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  228.052259] usb 3-1: USB disconnect, device number 80
[  228.478723] usb 3-1: new high-speed USB device number 81 using xhci_hcd
[  228.679012] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  228.679016] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  228.679018] usb 3-1: Product: 802.11 n WLAN
[  228.679019] usb 3-1: Manufacturer: Ralink
[  228.679021] usb 3-1: SerialNumber: 1.0
[  228.846931] usb 3-1: reset high-speed USB device number 81 using xhci_hcd
[  229.040215] ieee80211 phy24: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  229.050698] ieee80211 phy24: rt2x00_set_rf: Info - RF chipset 0009 detected
[  229.050981] ieee80211 phy24: Selected rate control algorithm 'minstrel_ht'
[  229.066402] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  229.066441] ieee80211 phy24: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  229.066462] ieee80211 phy24: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  229.423500] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  229.439205] usb 3-1: USB disconnect, device number 81
[  229.766627] usb 3-1: new high-speed USB device number 82 using xhci_hcd
[  235.062222] usb 3-1: new high-speed USB device number 83 using xhci_hcd
[  240.357818] usb 3-1: new high-speed USB device number 84 using xhci_hcd
[  245.653414] usb 3-1: new high-speed USB device number 85 using xhci_hcd
[  250.949005] usb 3-1: new high-speed USB device number 86 using xhci_hcd
[  256.244608] usb 3-1: new high-speed USB device number 87 using xhci_hcd
[  261.768184] usb 3-1: new high-speed USB device number 89 using xhci_hcd
[  267.095783] usb 3-1: new high-speed USB device number 90 using xhci_hcd
[  272.391375] usb 3-1: new high-speed USB device number 91 using xhci_hcd
[  277.686970] usb 3-1: new high-speed USB device number 92 using xhci_hcd
[  282.982574] usb 3-1: new high-speed USB device number 93 using xhci_hcd
[  288.278169] usb 3-1: new high-speed USB device number 94 using xhci_hcd
[  293.573767] usb 3-1: new high-speed USB device number 95 using xhci_hcd
[  298.869361] usb 3-1: new high-speed USB device number 96 using xhci_hcd
[  299.797271] mce: [Hardware Error]: Machine check events logged
[  304.164961] usb 3-1: new high-speed USB device number 97 using xhci_hcd
[  309.460557] usb 3-1: new high-speed USB device number 98 using xhci_hcd
[  314.756153] usb 3-1: new high-speed USB device number 99 using xhci_hcd
[  320.051709] usb 3-1: new high-speed USB device number 100 using xhci_hcd
[  325.347344] usb 3-1: new high-speed USB device number 101 using xhci_hcd
[  330.642941] usb 3-1: new high-speed USB device number 102 using xhci_hcd
[  335.938539] usb 3-1: new high-speed USB device number 103 using xhci_hcd
[  340.538678] usbcore: deregistering interface driver rt2800usb
[  341.234130] usb 3-1: new high-speed USB device number 104 using xhci_hcd
[  346.529737] usb 3-1: new high-speed USB device number 105 using xhci_hcd
[  351.825330] usb 3-1: new high-speed USB device number 106 using xhci_hcd
[  357.120924] usb 3-1: new high-speed USB device number 107 using xhci_hcd
[  362.416527] usb 3-1: new high-speed USB device number 108 using xhci_hcd
[  362.944482] usb 3-1: new high-speed USB device number 109 using xhci_hcd
[  363.144761] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  363.144764] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  363.144766] usb 3-1: Product: 802.11 n WLAN
[  363.144768] usb 3-1: Manufacturer: Ralink
[  363.144769] usb 3-1: SerialNumber: 1.0
[  363.320544] usb 3-1: reset high-speed USB device number 109 using xhci_hcd
[  363.432395] usb 3-1: USB disconnect, device number 109
[  363.432414] ieee80211 phy25: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1000 with error -19
[  363.432417] ieee80211 phy25: rt2800_probe_rt: Error - Invalid RT chipset 0x0000, rev 0000 detected
[  363.432419] ieee80211 phy25: rt2x00lib_probe_dev: Error - Failed to allocate device
[  363.432550] usbcore: registered new interface driver rt2800usb
[  364.748348] usb 3-1: new high-speed USB device number 110 using xhci_hcd
[  364.948591] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  364.948595] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  364.948597] usb 3-1: Product: 802.11 n WLAN
[  364.948599] usb 3-1: Manufacturer: Ralink
[  364.948600] usb 3-1: SerialNumber: 1.0
[  365.116552] usb 3-1: reset high-speed USB device number 110 using xhci_hcd
[  365.309850] ieee80211 phy26: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  365.320289] ieee80211 phy26: rt2x00_set_rf: Info - RF chipset 0009 detected
[  365.320571] ieee80211 phy26: Selected rate control algorithm 'minstrel_ht'
[  365.333024] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  365.333062] ieee80211 phy26: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  365.333084] ieee80211 phy26: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  365.589542] usb 3-1: USB disconnect, device number 110
[  365.920254] usb 3-1: new high-speed USB device number 111 using xhci_hcd
[  366.120415] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  366.120419] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  366.120421] usb 3-1: Product: 802.11 n WLAN
[  366.120423] usb 3-1: Manufacturer: Ralink
[  366.120424] usb 3-1: SerialNumber: 1.0
[  366.288458] usb 3-1: reset high-speed USB device number 111 using xhci_hcd
[  366.481738] ieee80211 phy27: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  366.492243] ieee80211 phy27: rt2x00_set_rf: Info - RF chipset 0009 detected
[  366.492569] ieee80211 phy27: Selected rate control algorithm 'minstrel_ht'
[  366.508852] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  366.508892] ieee80211 phy27: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  366.508913] ieee80211 phy27: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  366.865136] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  366.899728] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  366.944296] usb 3-1: USB disconnect, device number 111
[  367.396146] usb 3-1: new high-speed USB device number 112 using xhci_hcd
[  367.596448] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  367.596452] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  367.596454] usb 3-1: Product: 802.11 n WLAN
[  367.596455] usb 3-1: Manufacturer: Ralink
[  367.596457] usb 3-1: SerialNumber: 1.0
[  367.764346] usb 3-1: reset high-speed USB device number 112 using xhci_hcd
[  367.957642] ieee80211 phy28: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  367.968090] ieee80211 phy28: rt2x00_set_rf: Info - RF chipset 0009 detected
[  367.968414] ieee80211 phy28: Selected rate control algorithm 'minstrel_ht'
[  367.981748] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  367.981778] ieee80211 phy28: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  367.981795] ieee80211 phy28: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  368.332940] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  368.371683] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  368.420179] usb 3-1: USB disconnect, device number 112
[  368.860035] usb 3-1: new high-speed USB device number 113 using xhci_hcd
[  369.060319] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  369.060323] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  369.060325] usb 3-1: Product: 802.11 n WLAN
[  369.060326] usb 3-1: Manufacturer: Ralink
[  369.060328] usb 3-1: SerialNumber: 1.0
[  369.228235] usb 3-1: reset high-speed USB device number 113 using xhci_hcd
[  369.421536] ieee80211 phy29: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  369.432026] ieee80211 phy29: rt2x00_set_rf: Info - RF chipset 0009 detected
[  369.432306] ieee80211 phy29: Selected rate control algorithm 'minstrel_ht'
[  369.445797] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  369.445840] ieee80211 phy29: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  369.445861] ieee80211 phy29: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  369.804928] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  369.843503] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  369.888065] usb 3-1: USB disconnect, device number 113
[  370.327867] usb 3-1: new high-speed USB device number 114 using xhci_hcd
[  370.527825] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  370.527829] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  370.527831] usb 3-1: Product: 802.11 n WLAN
[  370.527832] usb 3-1: Manufacturer: Ralink
[  370.527833] usb 3-1: SerialNumber: 1.0
[  370.696024] usb 3-1: reset high-speed USB device number 114 using xhci_hcd
[  370.889368] ieee80211 phy30: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  370.899625] ieee80211 phy30: rt2x00_set_rf: Info - RF chipset 0009 detected
[  370.899931] ieee80211 phy30: Selected rate control algorithm 'minstrel_ht'
[  370.911362] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  370.911403] ieee80211 phy30: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  370.911426] ieee80211 phy30: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  371.268641] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  371.307191] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  371.356013] usb 3-1: USB disconnect, device number 114
[  371.819810] usb 3-1: new high-speed USB device number 115 using xhci_hcd
[  372.020120] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  372.020124] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  372.020126] usb 3-1: Product: 802.11 n WLAN
[  372.020128] usb 3-1: Manufacturer: Ralink
[  372.020129] usb 3-1: SerialNumber: 1.0
[  372.188004] usb 3-1: reset high-speed USB device number 115 using xhci_hcd
[  372.381314] ieee80211 phy31: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  372.391842] ieee80211 phy31: rt2x00_set_rf: Info - RF chipset 0009 detected
[  372.392124] ieee80211 phy31: Selected rate control algorithm 'minstrel_ht'
[  372.402555] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  372.402595] ieee80211 phy31: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  372.402617] ieee80211 phy31: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  372.760690] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  372.782874] usb 3-1: USB disconnect, device number 115
[  372.794835] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  373.131706] usb 3-1: new high-speed USB device number 116 using xhci_hcd
[  373.332013] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  373.332017] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  373.332019] usb 3-1: Product: 802.11 n WLAN
[  373.332021] usb 3-1: Manufacturer: Ralink
[  373.332022] usb 3-1: SerialNumber: 1.0
[  373.499789] usb 3-1: reset high-speed USB device number 116 using xhci_hcd
[  373.692815] ieee80211 phy32: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  373.703187] ieee80211 phy32: rt2x00_set_rf: Info - RF chipset 0009 detected
[  373.703492] ieee80211 phy32: Selected rate control algorithm 'minstrel_ht'
[  373.714513] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  373.714554] ieee80211 phy32: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  373.714576] ieee80211 phy32: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  374.043136] usb 3-1: USB disconnect, device number 116
[  374.091671] ieee80211 phy32: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -19
[  374.099665] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  374.471608] usb 3-1: new high-speed USB device number 117 using xhci_hcd
[  374.671897] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  374.671901] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  374.671903] usb 3-1: Product: 802.11 n WLAN
[  374.671904] usb 3-1: Manufacturer: Ralink
[  374.671905] usb 3-1: SerialNumber: 1.0
[  374.839808] usb 3-1: reset high-speed USB device number 117 using xhci_hcd
[  375.033096] ieee80211 phy33: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  375.043576] ieee80211 phy33: rt2x00_set_rf: Info - RF chipset 0009 detected
[  375.043854] ieee80211 phy33: Selected rate control algorithm 'minstrel_ht'
[  375.056443] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  375.056487] ieee80211 phy33: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  375.056510] ieee80211 phy33: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  375.412366] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  375.442854] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  375.489149] usb 3-1: USB disconnect, device number 117
[  375.923494] usb 3-1: new high-speed USB device number 118 using xhci_hcd
[  376.123777] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  376.123781] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  376.123783] usb 3-1: Product: 802.11 n WLAN
[  376.123784] usb 3-1: Manufacturer: Ralink
[  376.123785] usb 3-1: SerialNumber: 1.0
[  376.291698] usb 3-1: reset high-speed USB device number 118 using xhci_hcd
[  376.484976] ieee80211 phy34: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  376.495435] ieee80211 phy34: rt2x00_set_rf: Info - RF chipset 0009 detected
[  376.495708] ieee80211 phy34: Selected rate control algorithm 'minstrel_ht'
[  376.507575] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  376.507614] ieee80211 phy34: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  376.507638] ieee80211 phy34: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  376.868389] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  376.906412] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  376.951562] usb 3-1: USB disconnect, device number 118
[  377.403351] usb 3-1: new high-speed USB device number 119 using xhci_hcd
[  377.603135] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  377.603138] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  377.603140] usb 3-1: Product: 802.11 n WLAN
[  377.603142] usb 3-1: Manufacturer: Ralink
[  377.603143] usb 3-1: SerialNumber: 1.0
[  377.771581] usb 3-1: reset high-speed USB device number 119 using xhci_hcd
[  377.964893] ieee80211 phy35: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  377.975422] ieee80211 phy35: rt2x00_set_rf: Info - RF chipset 0009 detected
[  377.975699] ieee80211 phy35: Selected rate control algorithm 'minstrel_ht'
[  377.990129] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  377.990157] ieee80211 phy35: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  377.990173] ieee80211 phy35: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  378.340265] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  378.376206] usb 3-1: USB disconnect, device number 119
[  378.379287] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  378.711271] usb 3-1: new high-speed USB device number 120 using xhci_hcd
[  379.095255] usb 3-1: new high-speed USB device number 121 using xhci_hcd
[  379.263337] usb 3-1: Device not responding to setup address.
[  379.467245] usb 3-1: Device not responding to setup address.
[  379.671220] usb 3-1: device not accepting address 121, error -71
[  379.967188] usb 3-1: new high-speed USB device number 123 using xhci_hcd
[  380.166943] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  380.166946] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  380.166948] usb 3-1: Product: 802.11 n WLAN
[  380.166950] usb 3-1: Manufacturer: Ralink
[  380.166951] usb 3-1: SerialNumber: 1.0
[  380.335394] usb 3-1: reset high-speed USB device number 123 using xhci_hcd
[  380.528708] ieee80211 phy36: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  380.539143] ieee80211 phy36: rt2x00_set_rf: Info - RF chipset 0009 detected
[  380.539417] ieee80211 phy36: Selected rate control algorithm 'minstrel_ht'
[  380.552204] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  380.552246] ieee80211 phy36: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  380.552269] ieee80211 phy36: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  380.903867] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  380.942731] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  380.988083] usb 3-1: USB disconnect, device number 123
[  381.419098] usb 3-1: new high-speed USB device number 124 using xhci_hcd
[  381.619295] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  381.619299] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  381.619301] usb 3-1: Product: 802.11 n WLAN
[  381.619303] usb 3-1: Manufacturer: Ralink
[  381.619304] usb 3-1: SerialNumber: 1.0
[  381.787282] usb 3-1: reset high-speed USB device number 124 using xhci_hcd
[  381.980570] ieee80211 phy37: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  381.990909] ieee80211 phy37: rt2x00_set_rf: Info - RF chipset 0009 detected
[  381.991201] ieee80211 phy37: Selected rate control algorithm 'minstrel_ht'
[  382.004216] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  382.004258] ieee80211 phy37: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  382.004280] ieee80211 phy37: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  382.355734] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  382.386428] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  382.431131] usb 3-1: USB disconnect, device number 124
[  382.862970] usb 3-1: new high-speed USB device number 125 using xhci_hcd
[  383.063267] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  383.063271] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  383.063272] usb 3-1: Product: 802.11 n WLAN
[  383.063274] usb 3-1: Manufacturer: Ralink
[  383.063275] usb 3-1: SerialNumber: 1.0
[  383.231177] usb 3-1: reset high-speed USB device number 125 using xhci_hcd
[  383.424463] ieee80211 phy38: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  383.434971] ieee80211 phy38: rt2x00_set_rf: Info - RF chipset 0009 detected
[  383.435264] ieee80211 phy38: Selected rate control algorithm 'minstrel_ht'
[  383.448666] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  383.448710] ieee80211 phy38: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  383.448734] ieee80211 phy38: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  383.803249] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  383.833772] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  383.836158] usb 3-1: USB disconnect, device number 125
[  383.886950] ieee80211 phy38: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19
[  384.210867] usb 3-1: new high-speed USB device number 126 using xhci_hcd
[  384.411138] usb 3-1: New USB device found, idVendor=148f, idProduct=3572
[  384.411142] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  384.411144] usb 3-1: Product: 802.11 n WLAN
[  384.411145] usb 3-1: Manufacturer: Ralink
[  384.411147] usb 3-1: SerialNumber: 1.0
[  384.579070] usb 3-1: reset high-speed USB device number 126 using xhci_hcd
[  384.772343] ieee80211 phy39: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[  384.782824] ieee80211 phy39: rt2x00_set_rf: Info - RF chipset 0009 detected
[  384.783102] ieee80211 phy39: Selected rate control algorithm 'minstrel_ht'
[  384.799924] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  384.799953] ieee80211 phy39: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  384.799970] ieee80211 phy39: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[  385.135927] usb 3-1: USB disconnect, device number 126
[  385.186754] ieee80211 phy39: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x021c with error -19
[  385.186923] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready



```

lsmod | grep rt2800usb
rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb


I have no idea whats wrong with the driver , hopefully someone can help me?

---

### Post by Hadaka on 2017-01-24
hi, please post the output of..
```
lsusb
dmesg | grep rt2
```
thanks.

---

### Post by alexander15454 on 2017-01-25
```
[COLOR=#000000]Bus 002 Device 002: ID 8087:8000 Intel Corp. [/COLOR]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1bcf:2c55 Sunplus Innovation Technology Inc. 
Bus 003 Device 002: ID 148f:3572 Ralink Technology, Corp. RT3572 Wireless Adapter
Bus 003 Device 005: ID 04ca:3006 Lite-On Technology Corp.  [COLOR=#000000]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
```

```
[COLOR=#000000][   76.011609] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'[/COLOR][   76.011625] rt2800usb 3-2:1.0: firmware, attempted to load /lib/firmware/rt2870.bin, but failed with error -22
[   76.011627] rt2800usb 3-2:1.0: Direct firmware load for rt2870.bin failed with error -22
[   76.011630] ieee80211 phy1: rt2x00lib_request_firmware: Error - Failed to request Firmware
[   76.011740] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   76.011747] rt2800usb 3-2:1.0: firmware, attempted to load /lib/firmware/rt2870.bin, but failed with error -22
[   76.011749] rt2800usb 3-2:1.0: Direct firmware load for rt2870.bin failed with error -22 [COLOR=#000000][   76.011751] ieee80211 phy1: rt2x00lib_request_firmware: Error - Failed to request Firmware[/COLOR]
```

Placed the .bin from the driver disk it came with.

---

### Post by chili555 on 2017-01-25
> Placed the .bin from the driver disk it came with.Where did you place it?

May we see:```
ls -al /lib/firmware | grep 2870
```We hope we see that the file is present, the correct size and readable by all.

---

### Post by alexander15454 on 2017-01-25
```
[ 5991.330780] usb 3-2: USB disconnect, device number 2[ 5992.723788] usb 3-2: new high-speed USB device number 6 using xhci_hcd
[ 5992.924059] usb 3-2: New USB device found, idVendor=148f, idProduct=3572
[ 5992.924062] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5992.924064] usb 3-2: Product: 802.11 n WLAN
[ 5992.924066] usb 3-2: Manufacturer: Ralink
[ 5992.924067] usb 3-2: SerialNumber: 1.0
[ 5993.091988] usb 3-2: reset high-speed USB device number 6 using xhci_hcd
[ 5993.285294] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[ 5993.295810] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 0009 detected
[ 5993.296158] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[ 5993.310651] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5993.310692] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 5993.310707] rt2800usb 3-2:1.0: firmware, attempted to load /lib/firmware/rt2870.bin, but failed with error -22
[ 5993.310710] rt2800usb 3-2:1.0: Direct firmware load for rt2870.bin failed with error -22
[ 5993.310713] ieee80211 phy2: rt2x00lib_request_firmware: Error - Failed to request Firmware
[ 5993.313933] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 5993.313947] rt2800usb 3-2:1.0: firmware, attempted to load /lib/firmware/rt2870.bin, but failed with error -22
[ 5993.313948] rt2800usb 3-2:1.0: Direct firmware load for rt2870.bin failed with error -22
[ 5993.313950] ieee80211 phy2: rt2x00lib_request_firmware: Error - Failed to request Firmware
[ 5993.314037] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 5993.314044] rt2800usb 3-2:1.0: firmware, attempted to load /lib/firmware/rt2870.bin, but failed with error -22
[ 5993.314045] rt2800usb 3-2:1.0: Direct firmware load for rt2870.bin failed with error -22
[ 5993.314046] ieee80211 phy2: rt2x00lib_request_firmware: Error - Failed to request Firmware



```

Another outpout from dmesg and

```
ls -al /lib/firmware | grep 2870-rwxrwxrwx  1 root root       0 Jan 25 16:17 rt2870.bin



```

Removed that bin and installed the firmware-ralink with apt-get install firmware-ralink

I was able to see it again on ifconfig but after my laptop just froze. Everytime i plug it now in it freezes the laptop.

---

### Post by Hadaka on 2017-01-25
Hi the firmware file you loaded was not needed as the correct firmware is already
part of the kernel.
Your file.
Please delete/remove.
```
ls -al /lib/firmware | grep 2870-rwxrwxrwx  1 root root       0 Jan 25 16:17 rt2870.bin
```

Then from a working wired connection with ALL usb devices removed,please do..
```
sudo apt-get update 
 [http://mirrors.kernel.org/ubuntu/poo..._1.161_all.deb]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb")
sudo dpkg -i linux*.deb
```
REBOOT.
Next before inserting any usb,the internal wifi needs to be blacklisted to prevent it from conflicting
with the external usb. To determine the internal wifi driver please do..
```
lspci -nk |grep 0280 -A2 | sed -n '3p'
```
*Output = [COLOR=#ff0000]driver[/COLOR] *Example..Kernel driver in use:rtl8192se

To blacklist the internal wifi  driver, from the output of above command.. please do..
```
echo '[COLOR=#000000]blacklist [/COLOR][COLOR=#ff0000]driver[/COLOR]' | sudo tee -a /etc/modprobe.d/blacklist/[COLOR=#b22222]driver[/COLOR][COLOR=#000000].conf[/COLOR]
```
Finally, remove wired connection,Insert external wifi usb,BOOT and test wireless.
thanks

---

### Post by chili555 on 2017-01-25
> sudo apt-get update
wget [http://mirrors.kernel.org/ubuntu/poo..._1.161_all.deb](http://mirrors.kernel.org/ubuntu/poo..._1.161_all.deb)
sudo dpkg -i linux*.debThe URL got abbreviated here. I think Hadaka wants you to wget this instead: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb)

Right-click it and select 'copy link address' and then paste it into your terminal.

---

### Post by alexander15454 on 2017-01-26
Did that guys, still not working.

Stuff like this is showing now up in dmesg:

```
[  228.698641] usb 3-2: device descriptor read/all, error -110
[  228.994585] usb 3-2: new high-speed USB device number 12 using xhci_hcd
[  229.194715] usb 3-2: New USB device found, idVendor=148f, idProduct=3572
[  229.194719] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  229.194721] usb 3-2: Product: 802.11 n WLAN
[  229.194723] usb 3-2: Manufacturer: Ralink
[  229.194724] usb 3-2: SerialNumber: 1.0
[  229.362769] usb 3-2: reset high-speed USB device number 12 using xhci_hcd
[  229.474545] ieee80211 phy7: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1000 with error -19
[  229.474549] ieee80211 phy7: rt2800_probe_rt: Error - Invalid RT chipset 0x0000, rev 0000 detected
[  229.474551] ieee80211 phy7: rt2x00lib_probe_dev: Error - Failed to allocate device
[  229.474660] usb 3-2: USB disconnect, device number 12
[  229.746528] usb 3-2: new high-speed USB device number 13 using xhci_hcd
[  230.098500] usb 3-2: new high-speed USB device number 14 using xhci_hcd
[  230.266568] usb 3-2: Device not responding to setup address.
[  230.470498] usb 3-2: Device not responding to setup address.
[  230.666542] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  230.666546] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 1
[  230.666548] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  230.674452] usb 3-2: device not accepting address 14, error -71
[  230.780285] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 200
[  230.780289] evbug: Event. Dev: input4, Type: 1, Code: 103, Value: 0
[  230.780291] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  230.914772] evbug: Event. Dev: input4, Type: 4, Code: 4, Value: 28
[  230.914776] evbug: Event. Dev: input4, Type: 1, Code: 28, Value: 1
[  230.914778] evbug: Event. Dev: input4, Type: 0, Code: 0, Value: 0


```


On my rasperry pi its working fine without any changes, it was just plug & play....

---

### Post by chili555 on 2017-01-26
Is the device plugged in to a USB hub or directly to a USB2 or USB3 connector?

If you drag and drop the rt2870.bin from the CD to your desktop, what is the size?```
ls -al  ~/Desktop/rt2870.bin
```

What are the kernel versions here and on the Pi?```
uname -r
```

---

### Post by alexander15454 on 2017-01-26
Did a live test with Ubuntu Mate like on the pi, same issue on the live version + on Ubuntu 16.04.

Tested on USB 2 and 3, on my laptop both dont work, on the pi 3 i guess its usb 2.

My Windows 10 PC is able to use it without any issues under usb 2 also.

Size on the pi:

-rw-r--r-- 1 root root 8192 Nov 24  2014 /lib/firmware/rt2860.bin
-rw-r--r-- 1 root root 8192 Nov 24  2014 /lib/firmware/rt2870.bin
lrwxrwxrwx 1 root root   10 Nov 24  2014 /lib/firmware/rt3070.bin -> rt2870.bin
lrwxrwxrwx 1 root root   10 Nov 24  2014 /lib/firmware/rt3090.bin -> rt2860.bin

Same size on the laptop.



```
uname -r4.1.19-v7+



```

^Raspberry

On the laptop i downgraded to 4.4.25 since i got graphic issues with the new kernel version.

---

### Post by chili555 on 2017-01-26
> If you drag and drop the rt2870.bin from the CD to your desktop, what is the size?
Code:
ls -al  ~/Desktop/rt2870.binDidn't you tell us there was a firmware file on the install CD? That's what I was asking about.

---

### Post by alexander15454 on 2017-01-26
> **chili555 said:**
> Didn't you tell us there was a firmware file on the install CD? That's what I was asking about.

Its in the laptop from my friend, asked him to check if it works - same issue on his device, i can report back with the file size tomorrow or later in the evening.

---

### Post by alexander15454 on 2017-01-27
Got the CD back, same size.

---

### Post by chili555 on 2017-01-27
I regret that I have but two suggestions left. Since you say it works perfectly on the Pi, you might consider downgrading to a 4.19 kernel version on your Ubuntu desktop.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.19-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.19-wily/) You would need to download and install the linux image and headers matching your architecture:```
arch
```You will need the amd64 files if arch returns x86_64 and i386 if arch returns i686. This is a longshot and a gamble but it can easily be reversed.

The only other suggestion I have is to get a different device.

---

