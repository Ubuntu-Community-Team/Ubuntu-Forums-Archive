---
title: "I can see all the neighbours' WLAN's, not mine"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by MartinGiese on 2008-11-27
Updated to kubuntu 8.10 and iwlist wlan0 scan sees all the neighbours' WLANs but not mine.  Surreal.  Note that this WLAN is visible and works from a Mac, from my mobile phone, and also for my laptop until yesterday.

Removed WPA2 encryption from WLAN, didn't help.

Booting 8.10 with my previous kernel, 2.6.24-21-generic "solves" the problem but this is not the preferred solution of course.

So, here's the complete info...

Machine: HP Compaq 2510p (a laptop)

$ lspci | grep Wireless
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

$ lsusb | grep Wireless
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:37:fd:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-37-FD-B5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig wlan0

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod | grep iwl
iwlagn                 99588  0 
iwlcore                92740  1 iwlagn
rfkill                 17176  2 iwlcore
led_class              12164  1 iwlcore
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211

$ dmesg | grep iwl
[   16.092176] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   16.092182] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   16.092351] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.092390] iwlagn 0000:10:00.0: setting latency timer to 64
[   16.092492] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   16.139334] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[   16.222569] iwlagn 0000:10:00.0: PCI INT A disabled
[   16.223208] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   41.845567] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   41.845688] iwlagn 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   41.846790] firmware: requesting iwlwifi-4965-2.ucode
[   42.325778] Registered led device: iwl-phy0:radio
[   42.325828] Registered led device: iwl-phy0:assoc
[   42.325874] Registered led device: iwl-phy0:RX
[   42.325914] Registered led device: iwl-phy0:TX

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       ...
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:37:fd:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:5b:b7:67:f8:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:78:C5:71:D2
                    ESSID:"Dokken"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/100  Signal level:-72 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000013bdc80ff7
                    Extra: Last beacon: 608ms ago
          Cell 02 - Address: 00:0C:E3:63:A1:26
                    ESSID:"GlobeSurfer"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/100  Signal level:-78 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000001dbd51fce7
                    Extra: Last beacon: 540ms ago

(Note the absence of ESSID "Giese" on Chanel 13...)

$ lsb_release -d
Description:	Ubuntu 8.10

$ uname -a
Linux bittelite 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                       Ignoring unknown interface eth0=eth0.

huh? eth0 unknown?  What am I using now then? Whatever...

Hope somebody has an idea!

Martin

---

### Post by MartinGiese on 2008-11-28
Updated to 2.6.27-9-generic today, and at least I get the university WLAN, which also had problems previously.

We'll see what happens at home...

---

### Post by MartinGiese on 2008-11-28
...nothing happened at home.  I can still see lots of networks except my own.

Tried changing the ESSID of the network just to see whether it has something to do with seening a network it saw before.  No such luck.

---

### Post by MartinGiese on 2008-12-12
Oh, come on. Still no ideas anybody?

---

### Post by MartinGiese on 2009-02-13
Well, things went from bad to worse yesterday:  the iMac and the Nokia couldn't connect any longer.  After some aimless clicking at the WLAN configuration of the router, I tried the button for "automatic channel selection".  

I'd previously used channel 13 because it used to be far from what the neighbours used.  Maybe this has changed.  Whatever. :???:

Anyhow, the network is now on channel 1, and I can use it on all devices, including the laptop under 2.6.27-11-generic.

---

