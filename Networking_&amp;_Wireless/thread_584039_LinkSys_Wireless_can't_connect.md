---
title: "LinkSys Wireless can't connect"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by JSander on 2007-10-20
I've spent the last four days going through the various posts to try and get my LinkSys wireless network to work. The best I've had was the blinking of the wireless light.

I have the LinkSys WRT54GS router using key WPA-PSK, TKIP, non-broadcasting as my router. The wireless card in the PC is the LinkSys PCI Adapter - Wireless-G with SpeedBooster.

Ubuntu 7.10, 2.6.22-14-generic, Feisty Dawn. Installed Ndiswrapper:
  utils version: 1.9
  driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
  version:        1.45
  vermagic:       2.6.22-14-generic SMP mod_unload 586 
=====
ndiswrapper -l
wmp54gs : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
=====
Using 'lshw' command, the section that applies to the wireless card is:
           *-network:0
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: eth1
                version: 02
                serial: 00:1a:70:a4:1e:c1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+wmp54gs driverversion=1.45+Linksys,12/22/2004, 3.100.4 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
 =====
The 'iwconfig' command gives:
eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:93A7-FB4F-041B-7773-67A4-57B2-B26F-0A6D-FA66-2C4B-D7D3-5F5D-4015-08A1-1B49-22A7   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
=====
If I do "iwconfig eth1 essid MyName", then issue the 'iwconfig' command again, it still shows "ESSID:off/any". If I use the Network Manager icon, or "System => Administration => Network" giving the "Network Settings" GUI, they both show and essid of "MyName". I  don't know why 'iwconfig' doesn't correspond with the GUI settings.
=====
The /etc/network/interfaces file has:
auto eth1

iface eth1 inet dhcp
wpa-psk 93a7fb4f041b777367a457b2b26f0a6dfa662c4bd7d35f5d401508a11b4922a7
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MyName
====
The /etc/wpa_supplicant.conf has:
ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="MyName"
   #psk="<ascii_coe>"
   psk=93a7fb4f041b777367a457b2b26f0a6dfa662c4bd7d35f5d401508a11b4922a7
   key_mgmt=WPA-PSK
   proto=WPA
   group=TKIP
   pairwise=TKIP
   }
=====
Used the command:
wpa_supplicant -Dbroadcom -Bw -ieth1 -c/etc/wpa_supplicant.conf -dd
the response was:
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'broadcom' ctrl_interface 'N/A' bridge 'N/A'
Unsupported driver 'broadcom'.

Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout
==
The only one that seemed to work was using "-Dwext" which produced a lot of output.
===

The best I could do was to get the wireless light to flash. I can't make a connection.
The difference between the output of 'iwconfig' and the GUIs is confusing.

If anyone can help I'd appreciate it.
Joe
=====

---

### Post by stinger30au on 2007-10-20
linksys wireless stuff .... run a cat 5 data cable to it to begin with and configure it and get it working first via cable.

then tinker with wireless. your better off running a cable anyhwo. wirless still is not as fast a running cable anyways.

i have the same dramas with XP / Vista

---

### Post by tonamijesus on 2007-10-20
Hey,

I have a very similar Linksys wireless adapter and 7.10 is having trouble (read: completely fails) connecting to my router. The OS recognizes and identifies the wireless networks in the area, but cannot connect to any of them.

---

### Post by kevdog on 2007-10-20
Seems like you want to use ndiswrapper which is good.  But did you blacklist the bcm43xx driver in the /etc/modprobe.d/blacklist file??

Have you tried connecting at the command line first (see my signature) and testing this (if you can) on an unencrypted network connection (no WPA if you can).  WPA is sometimes a big pain in the butt to get going, so I usually recommend make sure everything is setup and running first and then add another layer of complexity to the mix with WPA.

---

### Post by JSander on 2007-10-21
Thank you for your replies. Yes, I did blacllist bcm34xx.

My intentions were to have this PC in an area of the house where there are no cables and too difficult to get them there. I am currently connected with a CAT-5 cable and trying to get the wireless going. However, I think what I'll do today is to move this PC to a wired area of the house, and move one of the Windows PCs to the remote area. I guess I'll wait for Ubuntu and the wireless driver companies to make more progress.

Thanks again for your replies,
Joe

---

