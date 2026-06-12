---
title: "Can connect to wireless-wired networks but no internet"
date: 2015-04-02
forum: Networking &amp; Wireless
---

### Post by stephen71 on 2015-04-02
I am running Ubuntu 14.04 LTS and my wireless adaptor is a TP Link TL-WN851ND. I can see and connect to wireless networks, but cannot access the internet (no web browsing, updates, pinging, etc). This problem has occurred before and I was only able to get round it by re-installing Ubuntu, but I would like to avoid doing this again and get to the root of the problem. As far as I can remember, I had not installed or updated anything that may have triggered this to happen each time. I have also tried a wired connection, which connects, but again no internet.

My apologies if there is already a solution to this posted, but after a lot of searching I have not found anything that works.

If any additional information is required please let me know. Any help on this would be very much appreciated!

---

### Post by stephen71 on 2015-04-02
Forgot to include - I have run the wireless script:

```

########## wireless info START ##########

Report from: 02 Apr 2015 17:48 BST +0100

Booted last: 02 Apr 2015 17:06 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

02:07.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:2091]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 003 Device 002: ID 0951:1665 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.11.11  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::76ea:3aff:fec1:38d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:579116 (579.1 KB)  TX bytes:351842 (351.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"GPSHOME"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'GPSHOME' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:122   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

search york.ac.uk
nameserver 144.32.128.228
nameserver 144.32.129.66

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [GPSHOME] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    4CE6766461E6:    Infra, <MAC '4CE6766461E6' [AC3]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    virginmedia5248675: Infra, <MAC 'virginmedia5248675' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    *GPSHOME:        Infra, <MAC 'GPSHOME' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA2

  IPv4 Settings:
    Address:         192.168.11.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.11.1

    DNS:             192.168.11.1

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

[[/etc/NetworkManager/system-connections/TheBatcave]] (600 root)
[connection] id=TheBatcave | type=802-11-wireless
[802-11-wireless] ssid=TheBatcave | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GPSHOME]] (600 root)
[connection] id=GPSHOME | type=802-11-wireless
[802-11-wireless] ssid=GPSHOME | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'GPSHOME' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"GPSHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019ed3e753a
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'virginmedia5248675' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"virginmedia5248675"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000112794b5fac
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '4CE6766461E6' [AC3]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"4CE6766461E6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000acaece3d3eb
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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
options iwlwifi 11n_disable=0

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0029 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.973731] ath: EEPROM regdomain: 0x809c
[   11.973734] ath: EEPROM indicates we should expect a country code
[   11.973735] ath: doing EEPROM country->regdmn map search
[   11.973736] ath: country maps to regdmn code: 0x52
[   11.973737] ath: Country alpha2 being used: CN
[   11.973738] ath: Regpair used: 0x52
[   13.749686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   14.804820] wlan0: authenticate with <MAC 'GPSHOME' [AC1]>
[   14.822256] wlan0: send auth to <MAC 'GPSHOME' [AC1]> (try 1/3)
[   14.828192] wlan0: authenticated
[   14.828324] ath9k 0000:02:07.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   14.828327] ath9k 0000:02:07.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   14.831790] wlan0: associate with <MAC 'GPSHOME' [AC1]> (try 1/3)
[   14.835608] wlan0: RX AssocResp from <MAC 'GPSHOME' [AC1]> (capab=0x11 status=0 aid=4)
[   14.835730] wlan0: associated
[   14.835748] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by ajgreeny on 2015-04-02
Could be a DNS problem.

What do you see if you use command **ping 216.58.210.78** (which is google.com) in terminal and then try **ping google.com** first when cable connected then wirelessly?

The second may fail, if I am right about DNS.

---

### Post by stephen71 on 2015-04-02
Thanks for your reply, ajgreeny. Here's what I found..

Strangely, pinging the IP address works for both wired and wireless, whereas pinging google.com does not. I did make sure to disconnect the connection I wasn't testing before pinging.

---

### Post by ajgreeny on 2015-04-02
So it is a DNS problem of some sort.

Click the network icon in your panel and choose Edit then go to the IPv4 tab and add the IPs **8.8.8.8, 8.8.4.4** exactly as shown here to the Additional DNS Servers box.  Save the setting (might need your password here) and restart networking.  You should now find that you can get to the internet.

Come back again if no success.

---

### Post by stephen71 on 2015-04-02
No success I'm afraid. It does seem as though it's a DNS issue though. I can also get to Google by typing the IP straight into the web browser, but of course navigating from there to other websites runs into the problem again.

---

### Post by ajgreeny on 2015-04-02
Did you definitely restart networking? Try a reboot; that will certainly restart it.

You could also.try changing the network type in that edit box from AutoDHCP to AutoDHCP (Addresses only) leaving the public DNS server numbers the same 8.8.8.8,8.8.4.4

PS
I hope you noticed the comma in the middle of that number sequence?

---

### Post by stephen71 on 2015-04-02
Update: I managed to fix the problem by uninstalling resolvconf,  restarting network manager, then re-installing. Just removing  resolveconf and restarting network manager fixed the problem, but I thought it would be best to  see if the problem returned after reinstalling, incase its removal caused  other problems.

```
sudo apt-get remove --purge resolvconf
```

```
sudo restart network-manager
```

```
sudo apt-get install --reinstall resolvconf
```

ajgreeny:  I did restart networking (I even tried rebooting) and yes I did notice  the comma! My solution was a very slightly modified version of this one:   [http://askubuntu.com/questions/455338/ping-unknown-host-google-com-but-ips-works-fine](http://askubuntu.com/questions/455338/ping-unknown-host-google-com-but-ips-works-fine)

I'm quite new to Ubuntu so if my solution worked, but for the wrong reasons, please do let me know!

Thanks for your help.

---

### Post by jeremy31 on 2015-04-02
I wonder why ```
nameserver 127.0.1.1
``` isn't in the /etc/resolv.conf as it usually is

---

