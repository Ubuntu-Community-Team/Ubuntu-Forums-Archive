---
title: "[SOLVED] RaLink RT2561/RT61 rev B 802.11g not working with WPA in Xubuntu"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-10-22
Hi I cannot get this card to work with WPA in Xubuntu 7.10.

I have a plain RT61 card in Ubunut 7.10 on another machine and it works fine with WPA to my router.

The only difference in the cards is the rev B in RaLink RT2561/RT61 rev B 802.11g.

This is my interfaces file that I have copied from the one box to the other

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface wlan0 inet static
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk 1d60905f61d5ffeb1c49dacf6dfaeb88a6f05cc24c942d65453b9ab7e652dc9a
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid DALI

auto wlan0
```

However, I have changed the static IP address.

Why would it work with one card but not the other, I don't believe I need to use other drivers as the RT61 is supported as default.

---

### Post by ralphRanger on 2007-10-22
I **think** I have the same card (can't really tell from your post) and am having no luck with it under gutsy, either, although I never tried it under fiesty.  Here are some clues.

> $ lspci -vvnn
04:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
        Subsystem: Linksys WMP54G ver 4.1 [1737:0055]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at fdbf8000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


I started out trying ndiswrapper, but was directed to the [RaLink driver source]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") instead. Grabbed it and ran make, per the README file.

> 
{/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module}$ sudo make all
make -C /lib/modules/2.6.22-14-386/build SUBDIRS=/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-386'
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.o
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c: In function ‘RT61_open’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c:330: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c:330: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c: In function ‘rt61_init_module’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c:900: warning: implicit declaration of function ‘pci_module_init’
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_main.c:229: warning: ‘device’ is used uninitialized in this function
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.o
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘STAMlmePeriodicExec’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:733: warning: unused variable ‘RxSignal’
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘MsgTypeSubst’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:3394: warning: unused variable ‘Return’
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘AsicSetRxAnt’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:5439: warning: ‘R77’ may be used uninitialized in this function
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘RadarDetectionStop’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:5877: warning: ‘R66’ may be used uninitialized in this function
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘AsicSendCommandToMcu’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:5345: warning: ‘i’ may be used uninitialized in this function
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘AsicAdjustTxPower’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:4327: warning: ‘BbpR1’ may be used uninitialized in this function
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c: In function ‘AsicSwitchChannel’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/mlme.c:3647: warning: ‘BbpReg’ may be used uninitialized in this function
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/connect.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/sync.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/assoc.o
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/assoc.c: In function ‘link_status_handler’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/assoc.c:810: warning: embedded ‘\0’ in format
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/assoc.c:834: warning: embedded ‘\0’ in format
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/auth.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/auth_rsp.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.o
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c: In function ‘RTMPHandleRxDoneInterrupt’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c:652: warning: ISO C90 forbids mixed declarations and code
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c:684: warning: ISO C90 forbids mixed declarations and code
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c: In function ‘RTMPSendRTSCTSFrame’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c:1982: warning: unused variable ‘IrqFlags’
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c: In function ‘RTMPHardTransmit’:
/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_data.c:2164: warning: unused variable ‘IrqFlags’
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_init.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/sanity.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_wep.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_info.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/eeprom.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_tkip.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/wpa.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/md5.o
  CC [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rtmp_task.o
  LD [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rt61.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "pci_module_init" [/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rt61.ko] undefined!
  CC      /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rt61.mod.o
  LD [M]  /usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'


Got some warnings, moved on. Well, not so fast.

> 
{/usr/local/src/2007_1003_RT61_Linux_STA_v1.1.1.0/Module}$ sudo /sbin/insmod rt61.ko
insmod: error inserting 'rt61.ko': -1 Unknown symbol in module


This may be related to [an existing bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95343"), so I removed network-manager. Still no luck.

All helps welcome!

---

### Post by ushills on 2007-11-01
Installed the serial monkey drivers and all now works.

---

### Post by christianxxx on 2007-11-22
I'm having a little trouble with Ra2561 as well.
I worked fin out of the box, but gradually became more unstable and difficult to work with.

Tried to install the serial monkey drivers, but it seems I'm still using rt61pci drivers.

Also installed wicd, but with absolutely no sucess. Moved on to Rutilt, and it works ok, but its running as a window, and not what's it called, docked to the panel? The statusbar-thingy? (Obviously a former windows user here.. :)
Since it won't minimize to the panel, I usually close it, but it seems to loose contact with the network once in a while. Could be when DHCP license is up for renewal, but that's no biggy.

How can I tell if I'm running the correct serial monkeys driver? Should I blacklist rt61pci? 
Is there hope for Rutilt? 


Christian

---

### Post by kevdog on 2007-11-22
The rt61pci driver is the built-in driver you want to blacklist -- not the compiled serial monkey driver.

To blacklist the driver:

echo "blacklist rt61pci" | sudo tee -a /etc/modprobe.d/blacklist

Make sure the rt61 driver (your compiled driver) is mentioned in the /etc/modules file to allow it to load at boot time.

---

