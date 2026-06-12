---
title: "Intel PRO/WIreless 3945ABG not working on Satellite 105 after installing ubuntu 14.04"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by fernandojosecabral on 2014-05-06
After installing ubuntu 14.04 for good in my old Toshiba Satellite 105 the wireless connection stopped working. I say it stopped, because it worked with live CD. In fact, I used it to download ubuntu 14.04 piece by piece (*). But, after finishing the installation and rebooting, it did not work any more.
File wireless-info.txt (output from "wireless_script"  follows):
```

    ########## wireless info START ########## 

##### release ##### 

Distributor ID:	Ubuntu Description:	Ubuntu 14.04 LTS Release:	14.04 Codename:	trusty 

##### kernel ##### 

Linux ubuntu 3.13.0-24-generic #47-Ubuntu SMP
Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux 

##### lspci ##### 

02:00.0 Ethernet controller [0200]: Intel
Corporation 82573L Gigabit Ethernet Controller [8086:109a] 	Subsystem: Toshiba America Info Systems
PRO/1000 PL [1179:ff10] 	Kernel driver in use: e1000e 05:00.0 Network controller [0280]: Intel
Corporation PRO/Wireless 3945ABG [Golan] Network Connection
[8086:4222] (rev 02) 	Subsystem: Intel Corporation Device [8086:1040] 	Kernel driver in use: iwl3945 

##### lsusb ##### 

Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 002 Device 002: ID 0483:2016
STMicroelectronics Fingerprint Reader Bus 002 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub 

##### PCMCIA Card Info ##### 

PRODID_1="" PRODID_2="" PRODID_3="" PRODID_4="" MANFID=0000,0000 FUNCID=255 

##### rfkill ##### 

0: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no 

##### iw reg get ##### 

country 00: 	(2402 - 2472 @ 40), (3, 20) 	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS 	(2474 - 2494 @ 20), (3, 20), NO-OFDM,
PASSIVE-SCAN, NO-IBSS 	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS 	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS 

##### interfaces ##### 

# interfaces(5) file used by ifup(8) and
ifdown(8) # Include files from /etc/network/interfaces.d: source-directory /etc/network/interfaces.d auto eth0 iface eth0 inet dhcp auto lo iface lo inet loopback auto wlan0 iface wlan0 inet dhcp 

##### iwconfig ##### 

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point:
Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off  
Fragment thr:off           Power Management:off           


##### route ##### 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 0.0.0.0         192.168.2.1     0.0.0.0        
UG    0      0        0 eth0 169.254.0.0     0.0.0.0         255.255.0.0    
U     1000   0        0 eth0 192.168.2.0     0.0.0.0         255.255.255.0  
U     0      0        0 eth0 

##### resolv.conf ##### 

nameserver 192.168.2.1 search FernandoCabral nameserver 127.0.1.1 search FernandoCabral 

##### nm-tool ##### 

NetworkManager Tool 

State: unknown 

##### NetworkManager.state ##### 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ##### 

[main] plugins=ifupdown,keyfile,ofono dns=dnsmasq 

[ifupdown] managed=true 

##### iwlist ##### 

##### iwlist channel ##### 

wlan0     24 channels in total; available
frequencies :           Channel 01 : 2.412 GHz           Channel 02 : 2.417 GHz           Channel 03 : 2.422 GHz           Channel 04 : 2.427 GHz           Channel 05 : 2.432 GHz           Channel 06 : 2.437 GHz           Channel 07 : 2.442 GHz           Channel 08 : 2.447 GHz           Channel 09 : 2.452 GHz           Channel 10 : 2.457 GHz           Channel 11 : 2.462 GHz           Channel 36 : 5.18 GHz           Channel 40 : 5.2 GHz           Channel 44 : 5.22 GHz           Channel 48 : 5.24 GHz           Channel 52 : 5.26 GHz           Channel 56 : 5.28 GHz           Channel 60 : 5.3 GHz           Channel 64 : 5.32 GHz           Channel 149 : 5.745 GHz           Channel 153 : 5.765 GHz           Channel 157 : 5.785 GHz           Channel 161 : 5.805 GHz           Channel 165 : 5.825 GHz 

##### lsmod ##### 

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945 mac80211              545990  2 iwl3945,iwlegacy cfg80211              409394  3
iwl3945,iwlegacy,mac80211 

##### modinfo ##### 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko firmware:       iwlwifi-3945-2.ucode license:        GPL author:         Copyright(c) 2003-2011 Intel
Corporation <ilw@linux.intel.com> version:        in-tree:s description:    Intel(R) PRO/Wireless 3945ABG/BG
Network Connection driver for Linux srcversion:     C93C31FCEBBAE1F376E495F alias:         
pci:v00008086d00004227sv*sd*bc*sc*i* alias:         
pci:v00008086d00004222sv*sd*bc*sc*i* alias:         
pci:v00008086d00004227sv*sd00001014bc*sc*i* alias:         
pci:v00008086d00004222sv*sd00001044bc*sc*i* alias:         
pci:v00008086d00004222sv*sd00001034bc*sc*i* alias:         
pci:v00008086d00004222sv*sd00001005bc*sc*i* depends:        iwlegacy,cfg80211,mac80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 686 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF sig_hashalgo:   sha512 parm:           antenna:select antenna (1=Main,
2=Aux, default 0 [both]) (int) parm:           swcrypto:using software crypto
(default 1 [software]) (int) parm:           disable_hw_scan:disable hardware
scanning (default 1) (int) parm:           fw_restart:restart firmware in
case of error (int) 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko license:        GPL author:         Copyright(c) 2003-2011 Intel
Corporation <ilw@linux.intel.com> version:        in-tree: description:    iwl-legacy: common functions for
3945 and 4965 srcversion:     400F302BE5C25B3C98A6CE8 depends:        mac80211,cfg80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 686 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF sig_hashalgo:   sha512 parm:           led_mode:0=system default,
1=On(RF On)/Off(RF Off), 2=blinking (int) parm:           bt_coex_active:enable
wifi/bluetooth co-exist (bool) 

##### modules ##### 

##### blacklist ##### 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac 

[/etc/modprobe.d/fbdev-blacklist.conf] blacklist arkfb blacklist aty128fb blacklist atyfb blacklist radeonfb blacklist cirrusfb blacklist cyber2000fb blacklist gx1fb blacklist gxfb blacklist kyrofb blacklist matroxfb_base blacklist mb862xxfb blacklist neofb blacklist nvidiafb blacklist pm2fb blacklist pm3fb blacklist s3fb blacklist savagefb blacklist sisfb blacklist tdfxfb blacklist tridentfb blacklist viafb blacklist vt8623fb 

##### udev rules ##### 

# PCI device 0x8086:0x109a (e1000e) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address
removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" 

# PCI device 0x8086:0x4222 (iwl3945) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address
removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="wlan*", NAME="wlan0" 

##### dmesg ##### 

[   22.703144] iwl3945: Intel(R) PRO/Wireless
3945ABG/BG Network Connection driver for Linux, in-tree:s [   22.703150] iwl3945: Copyright(c) 2003-2011
Intel Corporation [   22.703194] iwl3945 0000:05:00.0: can't
disable ASPM; OS doesn't have ASPM control [   22.757421] iwl3945 0000:05:00.0: Tunable
channels: 11 802.11bg, 13 802.11a channels [   22.757429] iwl3945 0000:05:00.0: Detected
Intel Wireless WiFi Link 3945ABG [   22.757510] iwl3945 0000:05:00.0: irq 44 for
MSI/MSI-X [   22.788267] ieee80211 phy0: Selected rate
control algorithm 'iwl-3945-rs' [  479.008145] iwl3945 0000:05:00.0: Direct
firmware load failed with error -2 [  479.008153] iwl3945 0000:05:00.0: Falling
back to user helper [  479.010100] iwl3945 0000:05:00.0:
iwlwifi-3945-2.ucode firmware file req failed: -2 [  479.010138] iwl3945 0000:05:00.0: Direct
firmware load failed with error -2 [  479.010142] iwl3945 0000:05:00.0: Falling
back to user helper [  479.011583] iwl3945 0000:05:00.0:
iwlwifi-3945-1.ucode firmware file req failed: -2 [  479.011590] iwl3945 0000:05:00.0: Could not
read microcode: -2 

########## wireless info END ############


```

Any help will be most appreciated.

- fernando

(*) Just in case you want to understand why I installed it piece by piece: my CD-ROM does not work. My USB works after booting up, but there is no way BIOS will read it on start up (either cold start or warm start). It does not matter how I configure the BIOS, it will only boot from the hard drive. So, I have wubi running on XP and then, from ubuntu that was running under wubi I downloaded a new copy of ubuntu, piece my piece, creating a whole new system on separate partiton, and then jumping to the new system.

---

### Post by chili555 on 2014-05-06
What an interesting problem! You are probably missing the firmware, somehow.> [  479.010100] iwl3945 0000:05:00.0: iwlwifi-3945-2.ucode firmware file req failed: -2 Let's check a couple of things. Does the file exist with the correct permissions?```
ls -al /lib/firmware | grep 3945
```We hope we see:```
-rw-r--r--  1 root root  150100 Mar  5 10:45 iwlwifi-3945-2.ucode
```If you see nothing, then the file doesn't exist. Use your wired ethernet to install the firmware package:```
sudo apt-get install --reinstall linux-firmware
```If the file exists but the permission is not as I listed, change it:```
sudo chmod 0644 /lib/firmware/iwlwifi-3945-2.ucode
```Reboot and let us see the wireless script again if it isn't working.

I have some concerns about your */etc/network/interfaces*, but let's see if the firmware fixes it first.

---

### Post by fernandojosecabral on 2014-05-06
Are you a ubuntu guru or what?

As soon as I ran
```

sudo apt-get install --reinstall linux-firmware

```
the wireless connection started working. Yes, not even reboot or anything. When the command execution was finishing the wireless network symbol popped up and connected imediately. I unpluged the cable and here it is, working great.

I had already spent several hours comparing this machine with another machine, to no avail. And now, with your hint,
it took me no more than about half a minute.

(I hope it will continue working after I reboot, which I will do after sending this acknowledgment).

Thanks a lot 

- fernando
PS - Yes, rebooted and it is working, but with a glitch: during boot up the system displayed a message saying something like "waiting 60 seconds more for the network". Then, it went on. When I logged in, network was not working. After perhaps 2 minutos, the wireless icon popped up and it started working. So... I' ll leave it at that, I am not trying to figure out why it is taking so long to establish a connection.

---

