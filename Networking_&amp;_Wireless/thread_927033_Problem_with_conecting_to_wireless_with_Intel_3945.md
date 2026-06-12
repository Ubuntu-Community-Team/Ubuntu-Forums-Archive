---
title: "Problem with conecting to wireless with Intel 3945ABG"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by fishercook on 2008-09-22
Hey guys, I've been running ubuntu for a while now and while I'm no guru I think I can handle the *basics*.  I can connect to my wireless router fine in XP but if I boot into ubuntu I see all the available networks(most at full signal) and can't connect to them.  

I'm running Hardy with an Intel PRO/Wireless 3945ABG.  The router I'm attempting to connect to is a Linksys WRT150N Wireless N home router.  

I've searched the forums already and nothing that I can use/understand has come up.  

Any help ya'll can give me would be very appreciated.

Thanks
 Fisher

---

### Post by [kAIOSHIN] on 2008-09-23
I am also having that problem... :(

---

### Post by fishercook on 2008-09-23
Anyone?  I'm stuck using XP at my home because of this and it blows.  

I'd also like to add that I can connect at my university's campus, just not at home.

---

### Post by dimsum_ph on 2008-09-23
after trying out this guide i can now use my intel 3945abg.

[http://linuxexpert.wordpress.com/]("http://linuxexpert.wordpress.com/")

---

### Post by [kAIOSHIN] on 2008-09-24
Still not working... :(

---

### Post by lkraemer on 2008-10-29
KAIOSHIN & fishercook,
Will you please try the following?  I am no expert but I did manage to get my Intel Pro 3945ABG Wifi card working in my Gateway MT6840 using this information.  It was a FRESH Install of Ubuntu 8.04 LTS.  (The Wifi worked GREAT on the Version 7.10 LiveCDR, and on the 7.10 Install.  I even tried to install 7.10, and then upgrade to 8.04 LTS, and the Wifi refused to work.


To get an Intel Pro 3945ABG Wifi Card working with a FRESH INSTALL of Ubuntu 8.04 LTS

ENABLE your Wifi, Turn on your Wifi Switch, or FN F2 (for my Gateway MT6840)

 
OPEN a TERMINAL Window, then cut and paste the following Terminal commands that DO NOT start with a # 

#Create file:	/etc/modprobe.d/iwl3945
sudo gedit /etc/modprobe.d/iwl3945
#that contains:
		alias wlan0 iwl3945
		options iwl3945 disable_hw_scan=1
#then save the file and exit
 
#Edit file:	/etc/udev/rules.d/70-persistent-net.rules
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
#Remove the line (if exists) that contains "ipw3945" and the NEXT LINE of text

#then save the file and exit

#Edit file:	/etc/modprobe.d/blacklist
sudo gedit /etc/modprobe.d/blacklist
#add the following two lines of text at the end of the file
                #Blacklist this Driver
		blacklist ipw3945
#then save the file and exit
 
sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe  iwlwifi_mac80211
sudo modprobe -r iwl3945
sudo modprobe  iwl3945

ifconfig wlan0 up
#reboot your computer

#If your Wifi still doesn't work do the following:

sudo apt-get install linux-backports-modules-hardy-generic

I got my Gateway MT6840 functional after doing the above.
I have a open router and haven't tried encription yet.



Refer to the following for Troubleshooting:


lsmod | grep iwl

ruebelr@ruebelr-laptop:~$ lsmod | grep iwl
iwl3945                96244  0 
lbm_iwl_mac80211      242292  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211
ruebelr@ruebelr-laptop:~$


lshw -C Network

ruebelr@ruebelr-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:eb:7b:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:3f:f8:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.102 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
ruebelr@ruebelr-laptop:~$ 


dmesg | grep -e iwl -e wlan

ruebelr@ruebelr-laptop:~$ dmesg | grep -e iwl -e wlan
[   27.843893] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   27.843897] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   27.900360] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   27.947797] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.948223] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   33.759618] Registered led device: iwl-phy0:radio
[   33.759702] Registered led device: iwl-phy0:assoc
[   33.759747] Registered led device: iwl-phy0:RX
[   33.759783] Registered led device: iwl-phy0:TX
[   56.212433] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.367854] wlan0: Initial auth_alg=0
[   69.367868] wlan0: authenticate with AP 00:0f:66:3d:22:62
[   69.369514] wlan0: RX authentication from 00:0f:66:3d:22:62 (alg=0 transaction=2 status=0)
[   69.369526] wlan0: authenticated
[   69.369532] wlan0: associate with AP 00:0f:66:3d:22:62
[   69.371707] wlan0: RX AssocResp from 00:0f:66:3d:22:62 (capab=0x5 status=0 aid=5)
[   69.371717] wlan0: associated
[   69.376263] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.376392] wlan0: association frame received from 00:0f:66:3d:22:62, but not in associate state - ignored
[   88.022756] wlan0: no IPv6 routers present
ruebelr@ruebelr-laptop:~$


lspci -nn

ruebelr@ruebelr-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
04:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
04:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
04:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
ruebelr@ruebelr-laptop:~$ 


iwconfig

ruebelr@ruebelr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"RUEBEL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:3D:22:62   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ruebelr@ruebelr-laptop:~$ 


iwlist scanning

ruebelr@ruebelr-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:3D:22:62
                    ESSID:"RUEBEL"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=75/100  Signal level:-59 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000eb3d6edf4
                    Extra:Last beacon:116ms ago

ruebelr@ruebelr-laptop:~$

Let me know if it works, or what I need to update in the document.

Good luck!


lkraemer

---

### Post by Everywhere_at_Once on 2008-10-30
does anybody know if this problem is still present in 8.10? 8.04 wouldn't play nice with my 3945, so i find myself booting linux far less than i used to (wired network is more challenging these days).

if 3945 works out of the box, or at least using *only* the repo's contained on the cd, then i'm game, and i'll jump into ubuntu with both feet again.

i appreciate any answer, and i'm hoping somebody pipes up and says "yeah it's worked for forever, where have you been!?" lol

---

### Post by lkraemer on 2008-10-30
Everywhere_at_Once,
It works perfectly on Ubuntu 7.10 (LiveCDR or Installed), but doesn't
work on Ubuntu 8.04LTS (LiveCDR or Installed).  I haven't tried Ubuntu
8.10 yet.  Test computer was a gateway MT6840 Laptop.

I did have success getting 8.04LTS working with the above procedure.

lkraemer

---

### Post by rocketsbay on 2008-10-30
I upgraded today to 8.10 and it doesn't work. I had it working under 8.04 using ndiswrapper, now I can't even seem to activate my wireless interface. 

I tried having my kill switch disabled (wifi on) then power up as suggested in the release notes but it doesn't work, I also tried the reverse with no success. 

My wifi LED is on up until the login screen where for some reason it goes off. Once logged in, doing iwconfig returns no wireless extensions. Can anyone help, this is really annoying.

---

### Post by lkraemer on 2008-11-01
rocketsbay,
It appears that the IPW3945 Drivers have been depreciated, and the new IWL3945 Drivers have been used in Ubuntu 8.04, but there are problems.

Here is a good site that explains how you can go back to the previous drivers for Ubuntu 8.04 LTS.

http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html

One posting said not to blacklist mac8021, as per item #1, but I don't know for sure.  I guess you could try it both ways.

Here is a good site on troubleshooting your problem.

http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html

I searched for hours to get my Gateway MT640 working with the IWL3945.

Good Luck.

lkraemer

---

### Post by fishercook on 2008-11-02
> **lkraemer said:**
> KAIOSHIN & fishercook,
Will you please try the following?  I am no expert but I did manage to get my Intel Pro 3945ABG Wifi card working in my Gateway MT6840 using this information.  It was a FRESH Install of Ubuntu 8.04 LTS.  (The Wifi worked GREAT on the Version 7.10 LiveCDR, and on the 7.10 Install.  I even tried to install 7.10, and then upgrade to 8.04 LTS, and the Wifi refused to work.


To get an Intel Pro 3945ABG Wifi Card working with a FRESH INSTALL of Ubuntu 8.04 LTS

ENABLE your Wifi, Turn on your Wifi Switch, or FN F2 (for my Gateway MT6840)

 
OPEN a TERMINAL Window, then cut and paste the following Terminal commands that DO NOT start with a # 

#Create file:	/etc/modprobe.d/iwl3945
sudo gedit /etc/modprobe.d/iwl3945
#that contains:
		alias wlan0 iwl3945
		options iwl3945 disable_hw_scan=1
#then save the file and exit
 
#Edit file:	/etc/udev/rules.d/70-persistent-net.rules
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
#Remove the line (if exists) that contains "ipw3945" and the NEXT LINE of text

#then save the file and exit

#Edit file:	/etc/modprobe.d/blacklist
sudo gedit /etc/modprobe.d/blacklist
#add the following two lines of text at the end of the file
                #Blacklist this Driver
		blacklist ipw3945
#then save the file and exit
 
sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe  iwlwifi_mac80211
sudo modprobe -r iwl3945
sudo modprobe  iwl3945

ifconfig wlan0 up
#reboot your computer

#If your Wifi still doesn't work do the following:

sudo apt-get install linux-backports-modules-hardy-generic

I got my Gateway MT6840 functional after doing the above.
I have a open router and haven't tried encription yet.



Refer to the following for Troubleshooting:


lsmod | grep iwl

ruebelr@ruebelr-laptop:~$ lsmod | grep iwl
iwl3945                96244  0 
lbm_iwl_mac80211      242292  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211
ruebelr@ruebelr-laptop:~$


lshw -C Network

ruebelr@ruebelr-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:eb:7b:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:3f:f8:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.102 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
ruebelr@ruebelr-laptop:~$ 


dmesg | grep -e iwl -e wlan

ruebelr@ruebelr-laptop:~$ dmesg | grep -e iwl -e wlan
[   27.843893] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   27.843897] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   27.900360] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   27.947797] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.948223] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   33.759618] Registered led device: iwl-phy0:radio
[   33.759702] Registered led device: iwl-phy0:assoc
[   33.759747] Registered led device: iwl-phy0:RX
[   33.759783] Registered led device: iwl-phy0:TX
[   56.212433] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.367854] wlan0: Initial auth_alg=0
[   69.367868] wlan0: authenticate with AP 00:0f:66:3d:22:62
[   69.369514] wlan0: RX authentication from 00:0f:66:3d:22:62 (alg=0 transaction=2 status=0)
[   69.369526] wlan0: authenticated
[   69.369532] wlan0: associate with AP 00:0f:66:3d:22:62
[   69.371707] wlan0: RX AssocResp from 00:0f:66:3d:22:62 (capab=0x5 status=0 aid=5)
[   69.371717] wlan0: associated
[   69.376263] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.376392] wlan0: association frame received from 00:0f:66:3d:22:62, but not in associate state - ignored
[   88.022756] wlan0: no IPv6 routers present
ruebelr@ruebelr-laptop:~$


lspci -nn

ruebelr@ruebelr-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
04:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
04:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
04:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
ruebelr@ruebelr-laptop:~$ 


iwconfig

ruebelr@ruebelr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"RUEBEL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:3D:22:62   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ruebelr@ruebelr-laptop:~$ 


iwlist scanning

ruebelr@ruebelr-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:3D:22:62
                    ESSID:"RUEBEL"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=75/100  Signal level:-59 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000eb3d6edf4
                    Extra:Last beacon:116ms ago

ruebelr@ruebelr-laptop:~$

Let me know if it works, or what I need to update in the document.

Good luck!


lkraemer

Will this work with 8.10?  I hadn't checked this thread before I updated to 8.10 yesterday in the hopes that it will work with my wireless at school.  If it will still work I'll be trying it this week (if intrepid can't handle it.)  

I also don't think that I made it clear that I *can* connect to my wireless at home and on some other networks, just not my college home.

Sorry it took so long to get back to you.  I kind of forgot about this post.

---

### Post by ewschone on 2008-11-02
After upgrading to 8.10 my wireless has stopped working on my Dell Inspiron 6400 which uses this card as well. 

With iscl -v it claims that the driver is loaded, and I seem to have a wmaster0 in my network config, but the connection is not working. 

Tbh, I have no clue what to do next, so any help would be appreciated.

UPDATE: It seems eth1 is my wireless card, but it doesnt connect to anything.

---

### Post by detente on 2008-11-02
> **lkraemer said:**
> KAIOSHIN & fishercook,
Will you please try the following?  I am no expert but I did manage to get my Intel Pro 3945ABG Wifi card working in my Gateway MT6840 using this information.  It was a FRESH Install of Ubuntu 8.04 LTS.  (The Wifi worked GREAT on the Version 7.10 LiveCDR, and on the 7.10 Install.  I even tried to install 7.10, and then upgrade to 8.04 LTS, and the Wifi refused to work.


To get an Intel Pro 3945ABG Wifi Card working with a FRESH INSTALL of Ubuntu 8.04 LTS

ENABLE your Wifi, Turn on your Wifi Switch, or FN F2 (for my Gateway MT6840)

 
OPEN a TERMINAL Window, then cut and paste the following Terminal commands that DO NOT start with a # 

#Create file:	/etc/modprobe.d/iwl3945
sudo gedit /etc/modprobe.d/iwl3945
#that contains:
		alias wlan0 iwl3945
		options iwl3945 disable_hw_scan=1
#then save the file and exit
 
#Edit file:	/etc/udev/rules.d/70-persistent-net.rules
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
#Remove the line (if exists) that contains "ipw3945" and the NEXT LINE of text

#then save the file and exit

#Edit file:	/etc/modprobe.d/blacklist
sudo gedit /etc/modprobe.d/blacklist
#add the following two lines of text at the end of the file
                #Blacklist this Driver
		blacklist ipw3945
#then save the file and exit
 
sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe -r mac80211
sudo modprobe  iwlwifi_mac80211
sudo modprobe -r iwl3945
sudo modprobe  iwl3945

ifconfig wlan0 up
#reboot your computer

#If your Wifi still doesn't work do the following:

sudo apt-get install linux-backports-modules-hardy-generic

I got my Gateway MT6840 functional after doing the above.
I have a open router and haven't tried encription yet.



Refer to the following for Troubleshooting:


lsmod | grep iwl

ruebelr@ruebelr-laptop:~$ lsmod | grep iwl
iwl3945                96244  0 
lbm_iwl_mac80211      242292  1 iwl3945
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211
ruebelr@ruebelr-laptop:~$


lshw -C Network

ruebelr@ruebelr-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:eb:7b:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:3f:f8:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.102 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
ruebelr@ruebelr-laptop:~$ 


dmesg | grep -e iwl -e wlan

ruebelr@ruebelr-laptop:~$ dmesg | grep -e iwl -e wlan
[   27.843893] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   27.843897] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   27.900360] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   27.947797] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.948223] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   33.759618] Registered led device: iwl-phy0:radio
[   33.759702] Registered led device: iwl-phy0:assoc
[   33.759747] Registered led device: iwl-phy0:RX
[   33.759783] Registered led device: iwl-phy0:TX
[   56.212433] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.367854] wlan0: Initial auth_alg=0
[   69.367868] wlan0: authenticate with AP 00:0f:66:3d:22:62
[   69.369514] wlan0: RX authentication from 00:0f:66:3d:22:62 (alg=0 transaction=2 status=0)
[   69.369526] wlan0: authenticated
[   69.369532] wlan0: associate with AP 00:0f:66:3d:22:62
[   69.371707] wlan0: RX AssocResp from 00:0f:66:3d:22:62 (capab=0x5 status=0 aid=5)
[   69.371717] wlan0: associated
[   69.376263] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.376392] wlan0: association frame received from 00:0f:66:3d:22:62, but not in associate state - ignored
[   88.022756] wlan0: no IPv6 routers present
ruebelr@ruebelr-laptop:~$


lspci -nn

ruebelr@ruebelr-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
04:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
04:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
04:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
ruebelr@ruebelr-laptop:~$ 


iwconfig

ruebelr@ruebelr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"RUEBEL"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:3D:22:62   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ruebelr@ruebelr-laptop:~$ 


iwlist scanning

ruebelr@ruebelr-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:3D:22:62
                    ESSID:"RUEBEL"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=75/100  Signal level:-59 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000eb3d6edf4
                    Extra:Last beacon:116ms ago

ruebelr@ruebelr-laptop:~$

Let me know if it works, or what I need to update in the document.

Good luck!


lkraemer

Before I try this, I have a question being that I have the same problem, but not the same specifics, and I don't even know if the driver is the problem. I had been running Mint 5 (which is just a remix of 8.04) and lspci reports the following for my wireless:

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

It had been working beautifully out of the box, even on every live CD I tried when I was playing around with distros. Then about a week ago, I simply lost my connection, and the network manager claims I have no wireless card, though lspci reports it correctly. I tried a couple live CD's just to see if there was a problem with the installed OS, but again, the network managers don't see the wireless chipset.

I'll try the quoted steps if you think it will help, but like I said, it had worked previously so I doubt the problem is necessarily software-related. But lspci sees it, so it may or may not be hardware-related. Your thoughts?

P.S. The laptop model is a Compaq Presario V3000T.

---

### Post by ewschone on 2008-11-02
> **ewschone said:**
> After upgrading to 8.10 my wireless has stopped working on my Dell Inspiron 6400 which uses this card as well. 


After removing the wireless entry in my config and reentering it and rebooting, all is well :).

---

### Post by Arabiest on 2008-11-04
Dear Friends,

My case is no different than most of yours, but the only difference is that mine seems to capture wireless signals of all around that are not intended for Internet sharing (Database servers via wireless for work related) but not free wireless public signals...

Also, when checking whether the driver is loaded, it is and this is the result:

subaiesb@ubuntu:~/Desktop$ lspci | grep Network
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
subaiesb@ubuntu:~/Desktop$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:18:de:77:12:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Please advise

---

### Post by cowboytuna on 2008-11-10
I have the same card.  It works for a couple of minutes and then the connection drops out.  I'll try the suggestion below once I get home later and will post the result here. :)  by the way, when I issue the dmesg command after the connection drops out, the last line is about "disassociation".  I'm not sure what it exactly mean.  It works properly in vista though. :(

---

### Post by edvost2 on 2008-11-15
bla bla bla.  Has :KSno one fixed his problem yet.  Wy?:popcorn:

---

### Post by Everywhere_at_Once on 2008-11-16
> **edvost2 said:**
> bla bla bla.  Has :KSno one fixed his problem yet.  Wy?:popcorn:

if you want to go around posting messages like that, you're gonna find zero help here.

were i you, i would be respectful or leave.

---

### Post by jodef on 2008-11-16
> **ewschone said:**
> After removing the wireless entry in my config and reentering it and rebooting, all is well :).

I have a dell inspiron 9400 with this wireless card not so familiar with networking can you elaborate on what you did thanks?

---

### Post by gemoyeni on 2008-11-23
> **fishercook said:**
> Hey guys, I've been running ubuntu for a while now and while I'm no guru I think I can handle the *basics*.  I can connect to my wireless router fine in XP but if I boot into ubuntu I see all the available networks(most at full signal) and can't connect to them.  

I'm running Hardy with an Intel PRO/Wireless 3945ABG.  The router I'm attempting to connect to is a Linksys WRT150N Wireless N home router.  

I've searched the forums already and nothing that I can use/understand has come up.  

Any help ya'll can give me would be very appreciated.

Thanks
 Fisher

hi guys try wicd ,google it someone posted this,I have tried it and it works great for me

---

### Post by Olivier2371 on 2008-11-23
Read the pages from the link below.

[http://intellinuxwireless.org/?p=iwlwifi]("http://intellinuxwireless.org/?p=iwlwifi")

---

