---
title: "Wi-fi hard blocked in ubuntu 18.04 (bionic) on HP laptop. Hardware key doesn't work"
date: 2018-10-18
forum: Networking &amp; Wireless
---

### Post by n0whereman on 2018-10-18
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I recently upgraded ubuntu from16.04 to on my system and found that wi-fi was not working at all because of a hard block.  A quick google search showed this forum [topic]("https://ubuntuforums.org/showthread.php?t=2353227") with same problem, but 
[/COLOR]
```

sudo modprobe -r hp-wireless
sudo modprobe hp-wmi

```


[COLOR=#000000] doesnt solve my problem[/COLOR][COLOR=#000000]. All other special buttons (fn+f1-f11) works correctly. 
[/COLOR][COLOR=#000000]fn+[/COLOR][COLOR=#000000]f12 [/COLOR][COLOR=#000000]light orange and [/COLOR][COLOR=#000000]doesnt switch ito green.

In dmesg i cant see rows of driver uploading firmware wifi device. Somesing like this: 

[/COLOR]```

[   34.885470] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   35.165620] rt2800pci 0000:0a:00.0: Direct firmware load for rt3290.bin failed with error -2
[   35.165628] ieee80211 phy0: rt2x00lib_request_firmware: Error - Failed to request Firmware

```

maybe problem in it?
[COLOR=#000000]
Laptop model HP 250 G1.
[/COLOR][COLOR=#000000]
Any help will be appreciated.[/COLOR]

---

### Post by Autodave on 2018-10-18
I have never found that upgrading gives anything but problems. There are many here that claim that they have no trouble, but I always seem to.  I always backup everything and do clean installs.

Before doing that, try one easy thing:  Disconnect EVERY cord from the machine. (Power down first.) Remove battery and power cord. Leave sit for 10 minutes. Reinstall battery and power cord and power up. See if the wifi works now.

If that doesn't help, get a download of 18.04 and burn it to a DVD or you USB stick. Boot from that and then choose to Try ?buntu.  If the wifi works from the installation medium, then you are probably best off doing a clean install after backing up everything to an external source first.

---

### Post by n0whereman on 2018-10-18
Problem was in died wifi module. Solved.  Thanks to all.

---

