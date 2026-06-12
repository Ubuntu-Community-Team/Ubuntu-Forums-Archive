---
title: "No Wireless with TP-LINK TL-WN322G found"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by schuppianer on 2008-07-02
Hi everybody,

I have a Wireless-USB-Stick form TP-LINK that does not work correctly.
The Stick is detected by the system as wlan0
```
wlan0     IEEE 802.11bg  ESSID:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

``` but it does not find any network.
```
iwlist wlan0 scan
wlan0     No scan results 
```
I had many problems with the zd1211 driver and I think that it still doesn't work correctly. I read that it is included in the kernel-version 2.6.18 and higher, but I had a lot of errors if I test it ```
dmesg | grep zd1211
[  230.133895] zd1211rw 1-1:1.0: phy0
[  230.133945] usbcore: registered new interface driver zd1211rw
[  230.451364] zd1211rw 1-1:1.0: RF MAXIM_NEW_RF 0x8 is not supported
[  256.103243] zd1211rw 1-1:1.0: couldn't load firmware. Error number -110 
``` I reinstalled it with that direction (german) [http://wiki.ubuntuusers.de/Baustelle/WLAN-Treiber](http://wiki.ubuntuusers.de/Baustelle/WLAN-Treiber) but no change...
any ideas?

With best regards

Schuppianer

---

### Post by ale3andro on 2008-07-09
Hi,
i bought the same usb wifi adapter today and made it work following the guide from the Greek Ubuntu users forum.
([http://ubuntu.opengr.net/viewtopic.php?f=9&t=408](http://ubuntu.opengr.net/viewtopic.php?f=9&t=408))
It's pretty straightforward, albeit its Greek.If you want any help with the translation let me now! Good luck :)

---

### Post by schuppianer on 2008-07-13
Hi ale3andro,

thanks for your reply, it really helped me and I now made it work with NdisWrapper and the Windows driver.

Many thanks!

---

### Post by ale3andro on 2008-10-19
This is an English translation of the installation guide as shown in the Greek Ubuntu users forum ([http://ubuntu.opengr.net/viewtopic.php?f=9&t=408]("http://ubuntu.opengr.net/viewtopic.php?f=9&t=408"))

**Installation Instructions for the TP-LINK WN322G Wireless USB adapter**

This is a guide for installing the TP-LINK WN322G Wireless USB adapter using ndiswrapper!

Step 01: Plug in you usb wifi adapter in a usb port. Run the command ***sudo apt-get install ndisgtk*** at the terminal.
Step 02: Run the command ***sudo ndisgtk***
Step 03: An new window by the name &#8220;*Wireless Network Drivers*&#8221; pops up. Click on the &#8220;*Install New Driver*&#8221; button. A new window &#8220;*Install Driver*&#8221; pops up and ask us to point to the location of the inf file.
Step 04: Insert the drivers CD that came with the wireless adapter into the CD-ROM and in the select inf file dialog select the file &#8220;***ZD1211BU.INF***&#8221; which resides in the directory &#8220;*\TL-WN322G\Win98_ME_2K_XP_X64\Driver Files\WinXP*&#8221;. Ubuntu finishes the installation.
Step 05: In the NM-APPLET ( the notification area applet for managing your network devices and connections &#8211; the one with the two computers icon) you can select the wireless network that you want to connect to.
That's it! It should work now!

Notes:
(1)If you want to install the drivers in a computer that is not connected to the internet you can download the 3 necessary packages ( **ndisgtk_0.8.3-1_i386.deb** , **ndiswrapper-common_1.50-1ubuntu1_all.deb** , **ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb**) from another computer (that is already connected to the internet) and copy them to the ***/var/cache/apt/archives*** directory. Now you can issue the ***sudo apt-get install ndisgtk*** command in the terminal and the package will be installed without the need of downloading packages from the internet. (Those packages are also available in the Ubuntu DVD)

Many thanks to the guys at the [Ubuntu-gr forum]("http://ubuntu.opengr.net/index.php").

---

### Post by jaygreece on 2009-03-13
Hi, i followed the steps but no luck from me...i still see a greyed out wireless connection.  Anything else to suggest?

---

### Post by ale3andro on 2009-03-15
If you're Greek (as your username suggests) try asking for help in the Greek Ubuntu users forum. I have posted the link for the relevant thread in an earlier post.

---

### Post by gazza487 on 2009-03-22
Right, I'm so confused..........

I had this adapter working on my pc fine(for weeks), got used to ubuntu (I put it on an old hdd so no fear it would destroy anything). Come to dual boot on my big hdd, all hardware the same except the hdd. Same ubuni install disk same driver for the adapter and it refuses to work.

If I leave it plugged in at boot form dmesg:
[  179.732068] usb 2-1: new full speed USB device using ohci_hcd and address 6
[  194.908017] usb 2-1: device descriptor read/64, error -110
[  210.188015] usb 2-1: device descriptor read/64, error -110
[  210.468010] usb 2-1: new full speed USB device using ohci_hcd and address 7
[  225.644022] usb 2-1: device descriptor read/64, error -110
[  240.924016] usb 2-1: device descriptor read/64, error -110
[  241.204015] usb 2-1: new full speed USB device using ohci_hcd and address 8
[  251.344020] usb 2-1: device not accepting address 8, error -62
[  251.400019] hub 2-0:1.0: unable to enumerate USB device on port 1

Replug...
[  257.668014] usb 1-6: new high speed USB device using ehci_hcd and address 6
[  257.808254] usb 1-6: configuration #1 chosen from 1 choice
[  257.875547] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  258.028019] usb 1-6: reset high speed USB device using ehci_hcd and address 6
[  258.186392] ndiswrapper: driver zd1211bu (TP-LINK,06/25/2007,6.22.0.0) loaded
[  258.528264] wlan0: ethernet device 00:21:27:ca:65:6d using NDIS driver: zd1211bu, version: 0x6160000, NDIS version: 0x501, vendor: '802.11 b+g Wireless LAN', 0ACE:1215.F.conf
[  258.535036] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  258.535120] usbcore: registered new interface driver ndiswrapper
[  262.576843] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Still not working, really dont understand, fed up too - think I may throw the towel in. At least windows consistently doesn't work - this is madness

---

### Post by gazza487 on 2009-03-22
Well, sorry for the post and blaming linux, back on a dozey box - the adapter itself is dead - windows will say hi to it and thats it, it does nothing else....

So lesson learned - stay away! Any recommendations of what to replace it with that works ?

---

### Post by ale3andro on 2009-03-22
In the past months I have read many things about the new linux drivers for Atheros based wifi cards. I guess an Atheros chipset based wifi adapter would work natively (without ndiswrapper).
Check out the compatibility list [http://madwifi.org/]("http://madwifi.org/")

---

### Post by gazza487 on 2009-03-23
> **ale3andro said:**
> In the past months I have read many things about the new linux drivers for Atheros based wifi cards. I guess an Atheros chipset based wifi adapter would work natively (without ndiswrapper).
Check out the compatibility list [http://madwifi.org/]("http://madwifi.org/")

Thankyou-it had been a long day, indeed yes I shall look. Have compiled and got madwifi working on my acer (before it bricked itself)

Any lists of which sticks have which chipset? I know alot of companies seem almost random in what chipset they useeven on the same models

---

### Post by ale3andro on 2009-03-23
A quick search on the internet for a vendor-chipset list of usb wifi adapters didn't return something useful.
I suggest you visit your hardware supplier (store or e-shop) make a list of the available models and search their vendor's website for technical specifications...

---

