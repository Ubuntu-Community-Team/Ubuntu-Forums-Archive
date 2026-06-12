---
title: "Can I force WICD to connect without the GUI??"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-06
As explained in this thread ([http://ubuntuforums.org/showthread.php?t=515139](http://ubuntuforums.org/showthread.php?t=515139)), Im having problems with my internet connection dropping, usually after several hours or days when being connected.  Im currently using WICD, however I believe the problems is a windows driver/ndiswrapper problem since the same behavior occurred with network manager.  The only symptom Ive been able to diagnose other than the dropped connection, is that my router settings are appearing twice when I do a iwlist scan

```
Cell 01 - Address: 00:13:10:8E:94:E9
ESSID:"GoHilton.com"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.452 GHz (Channel 9)
Quality:37/100 Signal level:-72 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=1000
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK


Cell 02 - Address: 00:00:00:00:00:00
ESSID:"GoHilton.com"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.452 GHz (Channel 9)
Quality:37/100 Signal level:-72 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=1000
Extra:atim=0
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
```

I used to have to reboot the computer when this happened, but have figured out a way to reset the networking interface by running the following script:
```
#!/bin/bash

sudo ifconfig wlan0 down
sudo /etc/init.d/wicd stop
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo /etc/init.d/wicd start

```

What I was wondering is if there was anyway to add another line to this script to ask wicd to connect to a specified network without having to open up the GUI.  Right now I open up tray.py and connect back to the network this way!

Thanks

---

### Post by imdano on 2007-08-06
Just check the box "Automatically connect to this network" in the entry for your network in the wicd gui.  Click "Connect" so that the setting gets saved, and it should try to automatically connect to the selected network when the daemon restarts.

---

