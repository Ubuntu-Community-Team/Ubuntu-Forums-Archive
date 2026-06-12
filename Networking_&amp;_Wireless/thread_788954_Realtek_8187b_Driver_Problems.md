---
title: "Realtek 8187b Driver Problems"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Midnightsun on 2008-05-10
Hey guys - posted this in the archive by mistake on an old thread relating to this adapter.  Still having no joy if anyone has any clues?

> **Midnightsun said:**
> I downloaded the modified driver from here: [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/]("http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/") but seem to be falling at the first hurdle.
```
$ sudo ./makedrv
[sudo] password for m1dn1ght: 
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/m1dn1ght/wifi/rtl8187B_linux_24.6.1024.0822.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```

So unless I'm mistaken, it's not compiling correctly? 

I'm running Hardy.  My lsusb output is:
```

7$ lsusb
Bus 003 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Don't know why there's 2 entries there for Realtek.  Under windows it shows as Realtek 8187b.

The sick irony is that the other day I was fiddling around with it so much that I must have inadvertedly fixed it as it worked briefly, but following a reboot I must have changed something and it ceased to work.  The output I get from typing ./wlan0up (even after ./wlan0down) is:

```
$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device

```

I may be missing something blatantly obvious, but can't figure this out.

Thanks in advance for any advice

---

### Post by chili555 on 2008-05-10
You are quite right. If you get errors at 'make,' the module has not compiled correctly and any further steps will be errors, too.

You might check here, specifically post #12: [http://ubuntuforums.org/showthread.php?t=782299&page=2&highlight=jadams](http://ubuntuforums.org/showthread.php?t=782299&page=2&highlight=jadams)

---

### Post by Tom--d on 2008-05-10
Use ndiswrapper and the Windows 98 driver to run your wireless card... 

You've got a nice id, 8189, unlike me.. i have the id of 8197 and it is annoying.. :@

---

### Post by Midnightsun on 2008-05-10
Thanks for the replies guys!

Tom-D: Thanks for the advice!  Unfortunately, this is one of the paths I've been down already without any joy.  

Chili555: Thanks for that link!  That did the trick in getting the driver to compile!

It all seemed to be coming together so well!  I compiled the jadams driver that Chili555 linked me to without too much hassle (needed to chmod the executables +x).  Using "sudo ./wlan0up" I was able to get the wireless card activated! Hoorah!

Unfortunately, I was using WPA encryption and as I've read, this is another problem with this driver.  At this point I was past caring and connected to the router via ethernet and adjusted it to WEP encryption.

I selected my router from the wireless network icon in the top right (I had a similar problem others have reported - the signal strengths of the networks are not showing) and inputted the WEP key.  For whatever reason, this caused my system to **** itself and freeze completely.

No worries - I reboot the system and navigate back to wifi directory.  Now I seem to be back in the situation I mentioned in my earlier post - following reboot I am no longer able to activate the wireless with ./wlan0up.  Typing the command gives no response (as usual) however even after waiting a while, the networks are not being listed under the network icon.  I tried typing typing ./wlan0down and got an error message (see below).  Tried again with ./wlan0up (twice) and got similar results.  However, typing wlan0up without typing wlan0down (despite the error message) first gives the message seen below, so wlan0down does appear to be doing something at least.

Unfortunately, I've got absolutely no idea where to go from here.  It seemed to be working OK at first, then I rebooted following crash (without changing any further settings) and it just seems broken, much like it happened last time.

Would really appreciate some advice!

P.S... just attempted to post this message.  Appears that typing ./wlan0up or down seems to cause some conflict with my wired connection also?  I used wired connection to initially read the forum and then disconnected it to test wireless again (I heard they conflict for some people?)  After having no joy, just reconnected it to post this.  Unable to use any network services despite the icon top-right showing wired network.  Will reboot now and post this (very long-winded) message;

Here's the terminal output: 

> m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0up
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0up
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8187.ko': -1 File exists
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules
m1dn1ght@m1dn1ght:~/wifi/rtl8187b-modified$ 

---

### Post by Midnightsun on 2008-05-12
Sorry to bump, but still getting nowhere with this and would really appreciate any help people can offer!

---

### Post by Midnightsun on 2008-05-15
I know repeated bumping is really bad form - but I'm totally lost with this problem and really need some guidance.  Does anyone have any idea where I should go from here?

I left it 3 days since last post, so hopefully won't upset too many people....

---

### Post by edgeseraph on 2008-05-16
I think I'm having your problem, too. I tried out the jadams driver, because of the compilation issues I was having with the other one (I just upgraded from Gutsy to Hardy, which broke my previous wireless driver installation). Just like what happened to you, when I was doing iwconfig commands to setup the interface (which appeared properly in the terminal). It was going well, so I ran the install script. Suddenly, when I try to set up the key (for WEP however).. Kernel Panic x.x

Because I ran that install script, I boot straight into panic. :P
(even in recovery mode x.x) If anyone has a quick way to fix a malicious driver install, let me know! I figured I'd just try to do the reverse of what the install script did (it's small, so no big deal).

I think I learned my lesson in regards to running shady install scripts, but I'm still interested in seeing this driver work. I'm starting to think I'll have to modify it myself or hope that somebody who knows better what they're doing takes a whack at it. Who would've thought that an updated kernel would invalidate the driver? Or am I mistaken about what's going on here?

---

### Post by cropr on 2008-06-24
I've managed to get the realtek 8187 to work without encryption, by using the J. Adams patch [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-jadams-2-1-2008.tar.gz]("http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-jadams-2-1-2008.tar.gz").  If I try to use WEP, Ubuntu freezes

the dmesg output after ```
wlan0setup
``` is
> [  313.379274] ieee80211_crypt: registered algorithm 'NULL'
[  313.392282] ieee80211_crypt: registered algorithm 'WEP'
[  313.412399] ieee80211_crypt: registered algorithm 'TKIP'
[  313.422428] ieee80211_crypt: registered algorithm 'CCMP'
[  313.503905] [COLOR="Red"]r8187: no version for "ieee80211_reset_queue" found: kernel tainted.[/COLOR]
[  313.508789]
[  313.508792] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
[  313.508800] Copyright (c) 2004-2005, Andrea Merello
[  313.508803] rtl8187: Initializing module
[  313.508807] rtl8187: Wireless extensions version 22
[  313.508811] rtl8187: Initializing proc filesystem
[  313.509472] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[  313.789529] rtl8187: Card MAC address is 00:16:44:c3:a9:32
[  314.133534] rtl8187: WW:Going dooh. >%^||
[  314.133804] rtl8187: PAPE from CONFIG2: 0
[  314.134982] rtl8187: Driver probe completed
[  314.134986]
[  314.135031] usbcore: registered new interface driver rtl8187
[  314.138396] udev: [COLOR="Red"]renamed network interface wlan0 to wlan1[/COLOR]
[  314.365959] rtl8187: Card successfully reset
[  314.365965] This is RTL8187B Reset procedure
[  322.906437] WIRELESS_MODE_G
[  322.914068] [COLOR="Red"]Set chan.call ieee80211_start_bss.in start bss call check.<6>ADDRCONF(NETDEV_UP): wlan1: link is not ready[/COLOR]
[  323.095151] Set chan.call ieee80211_start_bss.in start bss call check.<6>rtl8187: Setting SW wep key


I've marked the ones that look strange to me.

Of course I want to use some encryption.
Any help how to solve this last hurdle

---

### Post by cropr on 2008-07-01
I solved my issues using the recipe from pjasnos in thread [http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by eunuch on 2009-12-05
I read an article about the  RTL8187b  wireless chip set...

"You can choose to upgrade or install to this version in non stable release now. I can tell you that the RTL8187b WORKS OUT OF BOX!!!!"

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

I have a fresh installation of Ubuntu 9.10 (Karmic Koala?) and an USB device with the above chip set.

I don't know much about Linux internals - but, am I close to having it work?  (see below)

This is the syslog - any idea why it doesn't connect me?

It shows my removal and reconnection...

(This is an "out-of-the-box" set-up)

Dec  5 00:47:02 Ubuntu-desktop kernel: [  713.811733] usb 1-1: USB disconnect, address 2
Dec  5 00:47:02 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): now unmanaged
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 36)
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  (wlan0): cleaning up...
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec  5 00:47:02 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0)
Dec  5 00:47:02 Ubuntu-desktop wpa_supplicant[1150]: Failed to disable WPA in the driver.
Dec  5 00:47:02 Ubuntu-desktop NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0 disappeared
Dec  5 00:47:12 Ubuntu-desktop kernel: [  723.816020] usb 1-1: new high speed USB device using ehci_hcd and address 4
Dec  5 00:47:12 Ubuntu-desktop kernel: [  723.955777] usb 1-1: configuration #1 chosen from 1 choice
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.234548] phy1: Selected rate control algorithm 'minstrel'
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.235480] phy1: hwaddr 00:14:d1:5c:32:09, RTL8187BvE V0 + rtl8225z2
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/ieee80211/phy1/rfkill1) (driver <unknown>)
Dec  5 00:47:12 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0)
Dec  5 00:47:12 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
Dec  5 00:47:12 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Dec  5 00:47:12 Ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.2/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8187')
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): now managed
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Dec  5 00:47:12 Ubuntu-desktop NetworkManager: <info>  (wlan0): bringing up device.
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303426] rtl8187: Customer ID is 0x00
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303497] Registered led device: rtl8187-phy1::tx
Dec  5 00:47:12 Ubuntu-desktop kernel: [  724.303522] Registered led device: rtl8187-phy1::rx
Dec  5 00:47:16 Ubuntu-desktop kernel: [  728.086319] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): preparing device.
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Dec  5 00:47:16 Ubuntu-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Dec  5 00:47:19 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:47:24 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:47:44 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 
Dec  5 00:48:14 Ubuntu-desktop wpa_supplicant[1150]: CTRL-EVENT-SCAN-RESULTS 

Thanks,

---

