---
title: "Asus P5E3 Deluxe WiFi AP@n installation"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by InFront on 2008-03-19
Hi!

I'm a total newbie to ubuntu (and linux in general), but after installation most of my components work surprisingly well out of the box. There is however one issue that has to be solved, my wifi-connection. Since my PC is pretty far from the router I don't have a cable connected to it and it would be good if I could get the wifi up and running.

I have searched around for a solution, but I cant find any. Since I'm such a rookie in the linux-world I would appreciate a detailed description of what I should check out, and even better, how I can install the wifi-connection. My Asus P5E3 Deluxe WiFi AP@n (puh.. long name) Motherboard has integrated wifi, but asus are only (at this point) providing drivers for Windows.

Can someone help me with this?

Tommy

---

### Post by InFront on 2008-03-20
Hi!

I tried to follow kevdog's sticky-guide and typed:
 ```

lshw - C network

```
This is what I've got as a response:
```

tommy@London:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 12
       serial: 00:1d:60:e2:47:8f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:e2:43:74
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```

Is this of any help to any of you to diagnosticate my system?

---

### Post by InFront on 2008-03-23
Don't anyone have any suggestions for me on this one?

---

### Post by InFront on 2008-03-29
Need help.. still..

---

### Post by benner on 2008-05-30
no one could help this person?  i am about to buy a new mobo. i assumed since it has linux onboard that it was well supported for linux. should i buy it? does hardy have the needed drivers?

---

### Post by InFront on 2008-05-30
Hi!

I havn't upgraded to Hardy yet, but I would believe that support for WI-FI now is available for the motherboard.

---

### Post by Winddancer on 2008-06-21
I share your problem. I am running Ubuntu 8.04 LTS in the 64-bit version.

The problem apparently is that somehow the wlan chipset isn't detected at all. 

I followed the installation guide found in the German Ubuntu forums, on how to use the rtl8187 chipset the board contains using Nsidwrapper. However, I get told that the hardware is not present/active.

So, anyone an idea on how to "activate" the chipset, so that the Ndiswrapper can start its work?

Your help would be much appreciated.

---

### Post by lukemack on 2008-06-27
1. check that it is enabled in the bios - there is an option to disable it.
2. Boot into ExpressGate and check that it is working
3. Realise that there is no encryption support and disable it again
4. Buy a separate PCI wireless card

That would be my advice - I have the same board.

---

### Post by lukemack on 2008-06-27
Scrap that - go here:

[ftp://ftp.asus.com/pub/ASUS/mb/socket775/P5E3_Premium/](ftp://ftp.asus.com/pub/ASUS/mb/socket775/P5E3_Premium/)

There are linux wifi drivers!

Please post back your results! I think I am about to wet myself as I just spent a week trying to get a PCI card to work. Argh.

---

### Post by Winddancer on 2008-06-30
First, thanks for the replies. Didn't know that about Express Gate not being able to handle encrypted connections. The wlan chip definately is enabled in the BIOS, especially since in Windows XP x64, it works flawlessly. I currently use a lan cable connection to go online via Linux, but hopefully that will change.

From what I see, it looks like the drivers that come with the board on CD. I didn't get them to work, neither the general Linux ones, nor the Debian ones. When I back home, am currently typing from work, I will post the output I get when I try to use them. Maybe it is just some missing additional Ubuntu software that I am missing.

---

### Post by lukemack on 2008-06-30
you need to do 'sudo apt-get install build-essential' before trying to compile the drivers. This installs the necessary software to compile software from source.

---

### Post by Winddancer on 2008-06-30
Ok, here the output I get when I try to compile the drivers:

Here the output on std_out:
```
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.24-19-generic'

```

Here the output on std_err:

```
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_softmac_scan_wqÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:391: Warnung: ISO-C90 verbietet gemischte Deklarationen und Code
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:412: Warnung: Ãœbergabe des Arguments 2 von Â»queue_delayed_workÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_softmac_stop_scanÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:486: Warnung: Ãœbergabe des Arguments 1 von Â»cancel_delayed_workÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_associate_abortÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:885: Warnung: Ãœbergabe des Arguments 2 von Â»queue_delayed_workÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1360:4: Warnung: #warning CHECK_LOCK_HERE
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1400:2: Warnung: #warning CHECK_LOCK_HERE
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_rx_frame_softmacÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1471: Warnung: ISO-C90 verbietet gemischte Deklarationen und Code
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_stop_protocolÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2060: Warnung: Ãœbergabe des Arguments 1 von Â»cancel_delayed_workÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168:78: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_softmac_initÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: Fehler: Â»INIT_WORKÂ« nicht deklariert (erste Benutzung in dieser Funktion)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgefÃ¼hrt
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: Fehler: fÃ¼r jede Funktion in der er auftritt.)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2169:88: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2170:94: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2171:96: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2172:82: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2173:82: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In Funktion Â»ieee80211_softmac_freeÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2192: Warnung: Ãœbergabe des Arguments 1 von Â»cancel_delayed_workÂ« von inkompatiblem Zeigertyp
make[2]: *** [/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Fehler 1
make[1]: *** [_module_/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/ieee80211] Fehler 2
make: *** [modules] Fehler 2
In Datei, eingefÃ¼gt von /home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:64:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:29:26: Fehler: linux/config.h: No such file or directory
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8180_proc_module_initÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: Fehler: Â»proc_netÂ« nicht deklariert (erste Benutzung in dieser Funktion)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: Fehler: (Jeder nicht deklarierte Bezeichner wird nur einmal aufgefÃ¼hrt
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: Fehler: fÃ¼r jede Funktion in der er auftritt.)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8180_proc_module_removeÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:427: Fehler: Â»proc_netÂ« nicht deklariert (erste Benutzung in dieser Funktion)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8187_rx_urbsubmitÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:700: Warnung: Ãœbergabe des Arguments 6 von Â»usb_fill_bulk_urbÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8180_txÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1428: Warnung: Ãœbergabe des Arguments 6 von Â»usb_fill_bulk_urbÂ« von inkompatiblem Zeigertyp
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625:64: Fehler: dem Makro Â»INIT_WORKÂ« wurden 3 Argumente Ã¼bergeben, aber es nimmt nur 2
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8180_initÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: Fehler: Â»INIT_WORKÂ« nicht deklariert (erste Benutzung in dieser Funktion)
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8180_ioctlÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2298: Warnung: ISO-C90 verbietet gemischte Deklarationen und Code
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In Funktion Â»rtl8187_usb_probeÂ«:
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2403: Fehler: Implizite Deklaration der Funktion Â»SET_MODULE_OWNERÂ«
/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2421: Fehler: Â»struct net_deviceÂ« hat kein Element namens Â»get_wireless_statsÂ«
make[2]: *** [/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Fehler 1
make[1]: *** [_module_/home/nitschke/WLan/rtl8187_linux_26.1010.0622.2006/beta-8187] Fehler 2
make: *** [modules] Fehler 2

```

I tried to run makedrv via sudo, as I otherwise get "operation not allowed" messages.

---

### Post by leptogenesis on 2008-07-01
I'm trying to do this as well, and not having much luck.  Here's the error I'm getting (this is, after renaming the directory containing the generic linux drivers to not have parens in the name):

```

+ tar -zxvf stack.tar.gz
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
+ tar -zxvf drv.tar.gz
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
+ cd ieee80211
+ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
+ make
make -C /lib/modules/2.6.24-19-generic/build M=/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1360:4: warning: #warning CHECK_LOCK_HERE
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1400:2: warning: #warning CHECK_LOCK_HERE
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1471: warning: ISO C90 forbids mixed declarations and code
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2060: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: (Each undeclared identifier is reported only once
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: for each function it appears in.)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2169:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2170:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2171:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2173:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2192: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
make[2]: *** [/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
+ cd ../beta-8187
+ make clean
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
+ make
make -C /lib/modules/2.6.24-19-generic/build M=/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
In file included from /home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:64:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_proc_module_init’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: ‘proc_net’ undeclared (first use in this function)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: (Each undeclared identifier is reported only once
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: for each function it appears in.)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_proc_module_remove’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:427: error: ‘proc_net’ undeclared (first use in this function)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:700: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1428: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_init’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8180_ioctl’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2298: warning: ISO C90 forbids mixed declarations and code
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2403: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2421: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
make[2]: *** [/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/username/asuswifi/LinuxDrivers/WiFi/linux26x-8187/rtl8187_linux_26.1010.0622.2006/beta-8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
+ cd ..

```

Then I noticed in the readme:
> 
Release Date: 2006-01-13, ver 1.1


And in the readme for the debian-specific drivers:
> 
driver for Linux Debian3.1 kernel 2.6.13


That's pretty old to be compiling on a 2.6.24-19 kernel like I have.  I'm not surprised there are errors.

Patches, anyone?

---

### Post by lukemack on 2008-07-02
Hi,

I actually have the premium version of the board so am not 100% sure you guys have the same WLAN chipset but I used the drivers from here in the end:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

The one I am using is [http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0528_RT2870_Linux_STA_v1.3.0.0.tar.bz2)

But obviously make sure that you are using the right driver for your particular hardware.

YOU MUST HAVE build-essential installed though (sudo apt-get install build-essential) before compiling the drivers. The documentation isn't great and make sure you do 'sudo make install' once the drivers have compiled without errors (otherwise you will have to manually add the driver to the kernel every time you reboot.)

I hope this helps.

lukemack.

---

### Post by nickolasemp on 2008-07-08
So let's recap:

First of all I open the terminal(Applications->Accessories->Terminal) and I write:```
sudo apt-get install build-essential
```

I download from [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") the 2870 drivers (we are still talking for the wifi-Ap@n **deluxe** model, right? So rt2870 is our chip...). 

I extract them in a Desktop folder(let's call it fi). There will be a folder inside it that is going to be called 2008_0528_RT2870_Linux_STA_v1.3.0.0. 

There is no need to go to the makefile because chances are you are running in an STA mode and not as an Access Point and you are running Linux(and not UCOS).At least I am...

Now, let's go to the os/linux/config.mk file.
( For those of you that don't understand what we are talking about just writing in terminal: ```
sudo gedit Desktop/fi/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/config.mk
```).Then I just try to find the HAS_WPA_SUPPLICANT=n and change it to HAS_WPA_SUPPLICANT=y. Same goes for the next HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. I close and save the file...

While I am in the Desktop/fi/2008_0528_RT2870_Linux_STA_v1.3.0.0 folder, I type in the terminal: ```
sudo make install
```
There should be no errors...(I check if it says the word errors before it ends and there are none)

Now I am to edit the RT2870STA.dat 
```
sudo gedit Desktop/fi/2008_0528_RT2870_Linux_STA_v1.3.0.0/RT2870STA.dat
``` and i change according to my connection... all well

Next I type this in terminal:
```
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT2870STA
cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
``` as there is no folder in /etc called /Wireless... but still I create one and follow the readme guide.

Now near the end I type in terminal:
```
sudo /sbin/insmod "Desktop/fi/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux/rt2870sta.ko"
```(all goes well)
and then ```
sudo /sbin/ifconfig ra0 inet YOUR_IP up
``` where YOUR_IP is my IP(dah!)....

A big but... The error I get is:
> SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device


I rebooted, but no lspci, lsusb or iwconfig finds anything... Obviously it doesn't find it from the beginning, but when I get in Vista everything works ok...So there is no need to change anything in BIOS and the card works. I'm getting a bit frustrated... Any help?

edit #1:Should I add in /etc/modules the rt2870sta line?
edit #2:Nah, it doesn't change a thing...

---

### Post by chili555 on 2008-07-08
Please try these:```
sudo modprobe rt2870sta
sudo ifconfig ra0 up
ifconfig
```Did ra0 or anything else interesting appear?

As you *modprobe* in one terminal window, you might watch:```
sudo tail -f /var/log/messages
```for anything interesting. Let us know.

---

### Post by nickolasemp on 2008-07-09
I woke up this morning and the 'sudo /sbin/ifconfig ra0 inet YOUR_IP up' works!?! At least I don't get any errors. When I try to connect to my router though through that icon next to the clock, I enter my wireless preferences and then I just can't seem to enter my router @ 192.168.2.1. so what could the problem be?


By the way ifconfig does -finally- give me back an ra0... actually there are two of them so I'm guessing it's the two antennas.

```
nickolas@ubuntu:~$ sudo modprobe rt2870sta
nickolas@ubuntu:~$ sudo ifconfig ra0 up
nickolas@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:b9:e4:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1d:60:b9:d6:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6112341 (5.8 MB)  TX bytes:329312 (321.5 KB)
          Interrupt:16 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100075 (97.7 KB)  TX bytes:100075 (97.7 KB)

ra0       Link encap:Ethernet  HWaddr 00:15:af:3d:b9:c0  
          inet6 addr: fe80::215:afff:fe3d:b9c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1738 (1.6 KB)  TX bytes:7872 (7.6 KB)

ra0:avahi Link encap:Ethernet  HWaddr 00:15:af:3d:b9:c0  
          inet addr:169.254.8.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

edit:OK... So now it works... There are times that it works and some other times it simply doesn't... Well actually at some point it asked whether I wanted an application to use the passphrase and I said no, thats why probably it didn;t work in the morning. Now that I rebooted, it asked me again and I said yes, so now it works... I don;t know if this is it, but we'll se it in my future reboots... Who knows. 

WEP works from Ubuntu itself(I just right-cl;icked the network button -right beside the clock- and I chose edit wireless networks). Ubuntu asked me what  was the sid of my network and what was my WEP passphrase. So now, everything works most of the time. I'll play with it a bit longer and see what exactly is causing the problem. Though I am thrilled that it works; even not all the times.

Thanx everyone..! I hope my little guide above will help any future newbie. 

Off we go to setting -again- Compiz-fusion.

---

### Post by chili555 on 2008-07-09
> 'sudo /sbin/ifconfig ra0 inet YOUR_IP up' works!?! At least I don't get any errors. When I try to connect to my router though through that icon next to the clock, I enter my wireless preferences and then I just can't seem to enter my router @ 192.168.2.1. so what could the problem be?It's not asking for the address of your router; the tutorial assumes you want to specify an IP address; that is, use a static IP address.

Since you and most of us will be better served with a DHCP address, that is, asking the router to automatically assign one, let Network Manager  handle all these details for you.

---

### Post by nickolasemp on 2008-07-09
> It's not asking for the address of your router;I know that. I thought after that part that I would be able to connect to my router, that's all...

SO I am now able to tell how to enable it each time. I use those lines you said chili555:
```
sudo modprobe rt2870sta
sudo ifconfig ra0 up
```
and then I go to that network icon next to the clock, disable network and then re-enable it. It is the only way so far... If only it could be done automatically... Wait; it can!

I am going to search how to do it... If you have any idea, please share it.

Thank you so far: lukemack(that note about build-essential was so "essential" that I had forgotten all about it; as I do with the "cd .." that I mistakenly write "cd.." sometimes) and especially chili555!!!

---

### Post by lukemack on 2008-07-10
I think you are now at the same stage as me. I also have to disable and enable networking in the network manager applet. 'sudo etc/init.d/networking restart' does not have the same effect - otherwise it could be automated.

can you let me know the output of 'iwconfig' after you boot and BEFORE you do anything like ifconfig up etc?

thanks

---

### Post by nickolasemp on 2008-07-10
> **lukemack said:**
> I think you are now at the same stage as me. I also have to disable and enable networking in the network manager applet. 'sudo etc/init.d/networking restart' does not have the same effect - otherwise it could be automated.You are right... Bummer.

> **lukemack said:**
> can you let me know the output of 'iwconfig' after you boot and BEFORE you do anything like ifconfig up etc?

thanks

S'il te plaît.Here you go...```
nickolas@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device ra0 has been compiled with an ancient version
of Wireless Extension, while this program support version 11 and later.
Some things may be broken...

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

edit#1: I'm gonna check in the afternoon if [this]("http://ubuntuforums.org/showpost.php?p=5026306&postcount=34") works for us as well. At least I'm gonna save myself from writing those two lines in the terminal.

---

### Post by lukemack on 2008-07-10
yeah. I did something similar in /etc/rc.local:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig ra0 down
ifconfig ra0 up

exit 0
```

this works but i still have to do the disable / enable. I also get the error from iwconfig:

Warning: Driver for device ra0 has been compiled with an ancient version
of Wireless Extension, while this program support version 11 and later.
Some things may be broken...

I wonder if that has anything to do with it? perhaps chili555 knows?

---

