---
title: "No WiFi - Intel Pro/Wireless 4965 - Mythbuntu 14.04.1"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by Hackerbeavis on 2014-11-13
Hello. I just did a fresh install of Mythbuntu 14.04.1 onto a HP/Compaq 6910p laptop. The built-in wireless card is an Intel PRO/Wireless 4965 card. I am able to connect to a wired network and have connectivity, but I have not been successful at all in connecting to a wireless network. I have searched on the forums and not found anything that has helped me. However, I did find the wireless troubleshooting script, and I have pasted the output below. I would be very grateful for any assistance with this. Thanks!

```

########## wireless info START ##########

Report from: 13 Nov 2014 17:42 CST -0600

Booted last: 13 Nov 2014 17:41 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/mythuser/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
	Subsystem: Hewlett-Packard Company Compaq 6910p [103c:30c1]
	Kernel driver in use: e1000e

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
	Subsystem: Intel Corporation Device [8086:1000]
	Kernel driver in use: iwl4965

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless_script.sh: line 176: rfkill: command not found

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
iwl4965               112815  0 
iwlegacy              100569  1 iwl4965
mac80211              630653  2 iwl4965,iwlegacy
cfg80211              484040  3 iwl4965,iwlegacy,mac80211
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
	wireless-essid myssid
	

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:d8520000-d8540000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"myssid"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

** (process:1333): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

** (process:1333): WARNING **: error: could not connect to NetworkManager

NetworkManager Tool

State: unknown

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=myssid
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     24 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.745 GHz (Channel 149)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Riversedge' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Riversedge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006289e3305f
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:63.5 Mb/s
                    Mode:Master
                    Extra:tsf=0000029f0aaf9a3b
                    Extra: Last beacon: 480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'airport' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"airport"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000093466be3be2
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwl4965]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     52A3B1E68D22B0078326AC5
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl4965]
11n_disable: 0
amsdu_size_8K: 1
fw_restart: 1
queues_num: 0
swcrypto: 0

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1049 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.851230] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by chili555 on 2014-11-14
I assume this is your access point or router; it has the highest signal strength:> Cell 02 - Address: <MAC '' [AC2]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:63.5 Mb/s
                    Mode:Master
                    Extra:tsf=0000029f0aaf9a3b
                    Extra: Last beacon: 480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKAs you can see, it is, as it should be, encrypted with WPA2.

However, your /etc/network/interfaces doesn't supply any password:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
	wireless-essid myssidAnd what happens when we try to connect with no password? Request denied!

I suggest you amend the file to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid myssid
wpa-psk mysecretkey
```Restart the interface:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```'-v' for verbose will give us some clues as to whether it connects and if not, why not.

---

### Post by Hackerbeavis on 2014-11-14
Chili,
That worked perfectly! Odd though, I didn't have to put the PSK into /etc/network/interfaces on my last Mythbuntu machine. Is there somewhere else I can specify the password so that it isn't stored in clear text on the machine? I believe I just did it through network manager before, but when I tried that on this PC, it didn't work at all. I was never able to establish a connection. :-(

---

### Post by chili555 on 2014-11-14
Someplace on the system, any password is either visible in plain text or at least discoverable, even in Network Manager.  Please see: [https://wiki.debian.org/WiFi/HowToUse](https://wiki.debian.org/WiFi/HowToUse)> Restrict the permissions of /etc/network/interfaces, to prevent pre-shared key (PSK) disclosure:
```
#chmod 0600 /etc/network/interfaces
```In this case, I'd amend slightly to:```
sudo chmod 0600 /etc/network/interfaces
```At least only those entrusted with the administrators password can read or write to the file. Otherwise:```
Permission denied
```There is also this method: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) However, I haven't seen it used successfully in many years. We'd love for you to test it for a few weeks and tell us if it's valid!!

Should your MythTV box have a static IP address? Or no??

---

### Post by Hackerbeavis on 2014-11-15
> **chili555 said:**
> Someplace on the system, any password is either visible in plain text or at least discoverable, even in Network Manager.

This is good to know! Thanks for the information!


> Should your MythTV box have a static IP address? Or no??

No, this is just a frontend, so no static IP needed for this one.


> There is also this method: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) However, I haven't seen it used successfully in many years. We'd love for you to test it for a few weeks and tell us if it's valid!!

Isn't that just NetworkManager, and what most people use in Ubuntu? :confused: Honestly, the only reason I didn't go that route is because the nm-applet icon does not appear in the system tray, and nothing I have tried to get it to appear has worked. 

In any case, the changes I made to /etc/network/interfaces seemed to work at first, but then stopped working after a reboot. I'm not sure why, but I started looking at NetworkManager again, after you sent that link, and I managed to get the issue resolved. I initially defined the connection for my AP through the Network Connections app under settings. Although I checked the box for NetworkManager to automatically connect to my AP, this never happened. I started reading up on NetworkManager this morning, and used the nmcli command to manually connect to my pre-defined connection. This worked perfectly, but NM was still not connecting automatically after a reboot. During the course of my troubleshooting, I had manually changed /etc/NetworkManager/system-connections/connection. I believe when I did that, the check box under Network Connections was un-checked. Once I went back in there and checked it, it's been working great. 


Does any of this make sense? I'm not sure exactly what sequence of events got this working, to be honest. I think that at this point, I have a much better idea where to look in the future if I have a problem like this, though. I may need to set up another Mythbuntu frontend soon, so that will put my theory on the solution to the test.

As a general rule, what do you feel is the best/preferred way to set up wireless connections? Thought /etc/network/interfaces, or NetworkManager?

Thank you very much for all your help!

---

### Post by chili555 on 2014-11-15
They each have their strengths. Both are pretty reliable. /etc/network/interfaces has an additional strength; it is quite lightweight since it hasn't any GUI front end. I have computers that use each.

One thing that trips up new users is that they can't connect with NM and so they install Wicd. They can't connect with Wicd and fiddle with /etc/network/interfaces. They still can't connect and then they make an appointment with Dr. Chili and we find that there was a deeper underlying problem and, after it's fixed, they connect perfectly.

If I had a set it and forget it machine that never left home to go to the library or coffee shop or on vacation, I'd probably ditch NM and run /etc/network/interfaces only. But I am old school.

By the way, your WPA2 password is in clear text in /etc/NetworkManager/system-connections/*, too!

---

### Post by Hackerbeavis on 2014-11-15
> **chili555 said:**
> They each have their strengths. Both are pretty reliable. /etc/network/interfaces has an additional strength; it is quite lightweight since it hasn't any GUI front end. I have computers that use each.

If I had a set it and forget it machine that never left home to go to the library or coffee shop or on vacation, I'd probably ditch NM and run /etc/network/interfaces only. But I am old school.

By the way, your WPA2 password is in clear text in /etc/NetworkManager/system-connections/*, too!

Yes, I did notice the clear-text password in /etc/NetworkManager/system-connections as well. I had assumed, incorrectly, that it was probably encrypted somewhere. In any case, I learned lots of valuable lessons troubleshooting this issue.

For my next Mythbuntu frontend, I will probably take another look at /etc/network/interfaces, since these machines will never leave the house, and are meant not to have any interaction, aside from the MythTV GUI. 

Thanks again for your help! It is genuinely appreciated!

---

### Post by Hackerbeavis on 2014-11-23
So, I ended up having this problem rear its ugly head again. Things were working fine with the Network Manager configuration until today when things suddenly stopped working. My trick of using nmcli to manually connect, then verifying that the "Connect Automatically" box in Network Manager was checked did not work this time. I decided to ditch Network Manager and try a different, and hopefully more reliable, solution. Here's what I did:

1). Remove Network-Manager.

2). Edit /etc/network/interfaces:
```
        auto wlan0
	iface wlan0 inet dhcp
	wpa-conf /etc/wpa_supplicant.conf
```

3). Create /etc/wpa_supplicant.conf:
```
	network={
	        ssid="yourSSID"
	        scan_ssid=1
	        key_mgmt=WPA-PSK
	        psk="secretpassword"
	}

```	

4). Stop the blinking WiFi indicator lights. Create /etc/modprobe.d/wlan.conf:
```
	options iwlegacy led_mode=1
	options iwl4965 led_mode=1
```


I'm not sure if this is the best way to go about this, but it seems to be working very well after a number of reboots, and it's much faster than Network Manager. Hopefully this will be more reliable.

---

