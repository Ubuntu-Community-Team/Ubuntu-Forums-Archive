---
title: "Can see wifi network, can't connect on Ubuntu 12.04"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by sanssadness on 2014-04-25
I am running Ubuntu 12.04. For some reason, I can't connect to my wireless network. I can connect just fine using other computers and devices, so I know the network is set up properly. On Ubuntu, however, I can see the list of wifi networks, but my authentication isn't accepted. I know my password is correct for sure. Any suggestions on how I should begin troubleshooting the problem?

---

### Post by wildmanne39 on 2014-04-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by sanssadness on 2014-05-03
Attached. I cannot connect to the network with 100 strength (whatever that means).

---

### Post by sanssadness on 2014-05-15
I hope it's not unacceptable to give this a bump; it's been more than a week since I posted my diagnosis information.

---

### Post by QIII on 2014-05-16
Perfectly acceptable.  Just don't bump any more often than 24 hours.

Best wishes!

---

### Post by sanssadness on 2014-05-17
Good to know, thanks. Is there anyone besides Wild Man who usually analyzes such diagnostic logs?

---

### Post by Hadaka on 2014-05-17
hi, is your router name "linksys" ?

if so,,please chane...in the router,,channel to 1 or 11
change from TKIP to AES
keep wpa2  or wpa....but not mixed if possible.
set ipv6 to ignore
everything else looks fine.

---

### Post by sanssadness on 2014-05-17
Edit: Disregard this post; newer information available.

---

### Post by sanssadness on 2014-05-19
Still hoping for a solution on this.

---

### Post by Hadaka on 2014-05-20
Hi please do and post..
```
cat /etc/default/crda
iw reg get
cat /etc/modules
```
thanks.

---

### Post by wildmanne39 on 2014-05-20
Sorry I have not had much time to research your issue and reply, when I first posted I did but by the time you posted back I was out of town on business.

You have a bug, lets install the driver from the backports and see if it fixes it.

Go here [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/") and download the newest driver to your computer then place the file on your desktop and right click and extract here.

Then compile the driver using the directions below.
```
cd ~/Desktop/backports-3.15-rc1-1
make defconfig-ath5k
make
sudo make install
sudo modprobe -rv ath5k 
sudo modprobe -v ath5k

```
When you have an upgrade to the kernel you will need to do:
```

cd ~/Desktop/backports-3.15-rc1-1
make clean
make defconfig-ath5k
make
sudo make install
sudo modprobe -rv ath5k 
sudo modprobe -v ath5k
```
Thanks

---

### Post by sanssadness on 2014-05-21
While waiting for a solution to this, I upgraded the computer having this problem to Ubuntu 14.04. Before I proceed with installing the backports driver, would having 14.04 instead of 12.04 (I still have the same problem of failing to connect to my network) change any of your advice or require me to run that wireless script again?

In the meantime, Hadaka, here is the result of the commands you requested I run:

```
cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=


iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
```

---

### Post by Hadaka on 2014-05-21
Hi...YES if you changed your os from 12.04 to 14.04 please run the script again.
also pleas do..

you can find your 2 digit country code here..
```
cat /usr/share/zoneinfo/zone.tab
```

once found replace the XX with your country code.

```
sudo sed -i 's/REGDOMAIN=/REGDOMAIN=XX/' /etc/default/crda
```
BOOT
then to verify,,please do and post
```
iw reg get
```
Thanks

---

### Post by Hadaka on 2014-05-21
Hi...YES if you changed your os from 12.04 to 14.04 please run the script again.
also pleas do..

you can find your 2 digit country code here..
```
cat /usr/share/zoneinfo/zone.tab
```

once found replace the XX with your country code.

```
sudo sed -i 's/REGDOMAIN=/REGDOMAIN=XX/' /etc/default/crda
```
BOOT
then to verify,,please do and post
```
iw reg get
```
Thanks

---

### Post by varunendra on 2014-05-22
I suggest running a new, experimental version of the wireless_script this time : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

It covers some extra info that we often have to ask separately while troubleshooting. Having all that info in one place has its advantages.

---

### Post by sanssadness on 2014-05-28
I'm about to run the new script, because I am still failing to connect even with my new country code set, but before I do, the result of iw reg set is now the following. Does this look correct Hadaka?:

```
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
```

---

### Post by sanssadness on 2014-05-28
Here are the results of the experimental script I was asked to run, wrapped in code tags as instructed. The SSID of my wireless network is "keiththeone":

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

centralnexus 3.13.0-27-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
Memory : 7915 MB
Uptime : 20:11:37 up 9 min,  2 users,  load average: 0.14, 0.64, 0.53


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:0035]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04d9:a088 Holtek Semiconductor, Inc. 
Bus 006 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              626511  1 ath5k
cfg80211              484040  3 ath,ath5k,mac80211
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Blue:            Infra, <MAC C-01 Blue>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Vicex:           Infra, <MAC C-09 Vicex>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    123Netgear:      Infra, <MAC C-04 123Netgear>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Sushi:           Infra, <MAC C-03 Sushi>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    2WIRE145:        Infra, <MAC C-NA 2WIRE145 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Down Under:      Infra, <MAC C-NA Down Under 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    linksys:         Infra, <MAC C-02 linksys>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA
    joe's wireless:  Infra, <MAC C-NA joe's wireless 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 14 WPA2
    justintime:     Infra, <MAC C-07 justintime>, Freq 2432 MHz, Rate 54 Mb/s, Strength 0 WPA2
    keiththeone:     Infra, <MAC C-06 keiththeone>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    HP-Print-2F-Deskjet 2540 series: Infra, <MAC C-NA HP-Print-2F-Deskjet 2540 series 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2
    99_Family:       Infra, <MAC C-NA 99_Family 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    99_Family-guest: Infra, <MAC C-05 99_Family-guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 2
    Smith Network:   Infra, <MAC C-08 Smith Network>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
    TO NOWHERE:       Infra, <MAC C-NA TO NOWHERE 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e1000e | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.40.202
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.40.1
    DNS:             192.168.40.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search lan


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.40.1   0.0.0.0         UG    0      0        0 eth0
192.168.40.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.40.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.309/0.415/0.521/0.106 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.030/0.032/0.035/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Blue>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Blue"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 linksys>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003fee0204e2
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Sushi>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Sushi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000676a31349c
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 123Netgear>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"123Netgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d0d4c05f4a
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 99_Family-guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"99_Family-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000100409cfde
                    Extra: Last beacon: 896ms ago
          Cell 06 - Address: <MAC C-06 keiththeone>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"keiththeone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000062dde9c
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 justintime>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"justintime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d0969e6048
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Smith Network>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/70  Signal level=-102 dBm  
                    Encryption key:on
                    ESSID:"Smith Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d0949c7183
                    Extra: Last beacon: 612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 Vicex>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Vicex"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000042251fb222
                    Extra: Last beacon: 548ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B09A94F74DCA60EBD06A6B6
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-27-generic root=/dev/mapper/VolumeGroup-Volume--Root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.080154] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.080557] audit: initializing netlink socket (disabled)
[    1.924199] wmi: Mapper loaded
[    7.739011] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.759974] thinkpad_acpi: http://ibm-acpi.sf.net/
[   21.350052] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.350201] ath5k 0000:03:00.0: registered as 'phy0'
[   22.079634] ath: EEPROM regdomain: 0x67
[   22.079639] ath: EEPROM indicates we should expect a direct regpair map
[   22.079643] ath: Country alpha2 being used: 00
[   22.079645] ath: Regpair used: 0x67
[   22.270727] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.700877] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.544841] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.546780] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.339135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   92.260672] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.411578] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  122.055078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========
```

---

### Post by wildmanne39 on 2014-05-28
I still believe post 11 will fix the issue.

---

### Post by sanssadness on 2014-05-28
I managed to solve this problem another way right before I installed the backports driver, and I cannot believe what the cause was!

Ubuntu seems to have a problem with MAC address cloning. When I turned this option off, I was able to connect immediately without any problems. The MAC cloning feature is bugged.

I need help reporting this bug. In order for a bug on Launchpad to get triaged, I have to give the software package that is causing the bug. What is the software package responsible for allowing users to manage WiFi connections (and the MAC cloning feature)? I didn't install any replacement packages; I am simply using what Ubuntu provides by default.

---

### Post by Hadaka on 2014-05-29
Glad you got it working.
please mark this thread SOLVED
How to [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

### Post by sanssadness on 2014-05-29
I'd consider my approach more of a temporary workaround than a solution. It is still a bug in Ubuntu's WiFi package that cloning MACs doesn't work. To really solve this, I need the name of the package that lets users manage WiFi connections. Does anyone know the name of this package so I can properly report it as a bug?

---

### Post by varunendra on 2014-05-30
DISCLAIMER: Currently I have no authentic links to back my *beliefs* stated below, and I am not very certain about these.

As far as I know, successful MAC cloning (also called "MAC Spoofing") depends upon the capability of the driver. The network manager does the job of communicating with the driver to get the job done. As such, the bug can be either in the driver or the Network Manager.

Another way to do mac spoofing is to use the "ifconfig <interface> hw ether <MAC Address>" command. For example -
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether **00:aa:bb:cc:22:44**
sudo ifconfig wlan0 up
```
If this works, the bug is in Network Manager (package name : network-manager, network-manager-gnome). If it fails, the bug *may be* in the driver (ath5k).

In case the bug is in Network Manager, you should be able to use a different network manager successfully like 'Wicd' or WPA-Supplicant directly.

---

### Post by sanssadness on 2014-06-06
Is there a way to replicate the 3 sudo commands by editing a text file? I just want to have a way to reverse the process if something goes wrong.

---

### Post by varunendra on 2014-06-07
There should be some, but none that I know of. But what those commands do is temporary anyway, so will be reversed on a reboot.

---

### Post by sanssadness on 2014-06-09
I have run your test to narrow the problem down. I can connect to WiFi until I run those 3 commands, which prevents me from connecting to WiFi. However, as you said, the changes were reversed after I rebooted, and I was able to connect to WiFi again.

So this is likely a problem with the driver right? Is ath5k open source or is it provided by the manufacturer?

---

### Post by varunendra on 2014-06-11
All the ath**[COLOR="#FF0000"]*X*[/COLOR]**k series drivers for Atheros cards, including 'ath5k', are fully open source as far as I know.

---

### Post by sanssadness on 2014-06-23
What would I have to do to narrow down the MAC cloning issue to te ath5k driver?

---

### Post by varunendra on 2014-06-24
I have no idea. Probably using another card/usb-dongle and repeat the cloning steps?

If other devices/drivers don't seem to suffer with the same issue, you may wish to file a bug report against ath5k. If it managed to get attention of the developers, they will themselves tell you what to try to confirm and pin-point the source of the problem, in order to fix it.

How to properly file a bug report : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by sanssadness on 2014-07-08
Well, I did something very similar to what you suggested; I used another computer's wireless card and attempted to connect while cloning the MAC address. The result was that I was able to connect normally without MAC cloning, but MAC cloning caused my connection to fail again!

I did this test on a computer where the driver was "iwlwifi". This seems to indicate that the problem was not caused by the ath5k driver. Does this narrow down the possibilities for the source of the bug a bit? What should I do next?

---

### Post by varunendra on 2014-07-10
I think the problem has already gone beyond my current knowledge and experience, and I don't get much time these days to dig too deep for an issue. So I'm out of ideas here.

If anyone has anything to add to the thread, please join us.

---

### Post by sanssadness on 2014-07-15
For now I've reported it as a wireless-tools bug, but it hasn't received much attention: [https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/1324355](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/1324355)

What is the procedure they use for determining which bugs to fix and which ones to ignore?

---

### Post by varunendra on 2014-07-15
> **sanssadness said:**
> What is the procedure they use for determining which bugs to fix and which ones to ignore?

Not sure, but most probably based on its importance/significance? Which is also represented by "Bug Heat" on the report page. Clicking on it shows how it is calculated -
> Launchpad helps you to appraise a bug by giving you a calculated measure — called bug heat — of its likely significance. You can see bug heat in bug listings, and also on individual bug pages, as a number next to a flame icon...

---

### Post by sanssadness on 2014-08-06
Is it possible that a bug is never fixed because its heat score never rises high enough, or will they eventually get to this, say, by the next long term release?

---

### Post by varunendra on 2014-08-08
Some bugs get fixed before even being reported.

I really don't know how bugs are prioritized and fixed behind the scenes. But using my common sense, I think the following factors decide what kind of problems are going to get how much attention from developers -

1) How many people are affected by the bug. The more the people, the more is the importance of the bug.
2) How badly it is affecting other things in the overall system. The more things it affects, the more important it is to fix it.
3) How easy it is to fix. If it ain't gonna take a lot of time and experiments, the developer may fix it as soon as they notice it.
4) How significant it is and for how long. If it is related to something that is going to be dropped soon, the developers may choose to ignore it and move on to next project.

I believe a combination of these decides when and whether a bug is going to be fixed, and then the developers may have their own way of prioritizing things.

I know it is not a straight answer to your question, but I believe a 'Generalized' answer would be a wrong answer, and I don't have the knowledge to be able to answer it specifically.

---

### Post by sanssadness on 2014-11-07
For anyone else who has this problem, I noticed that the bug got marked as a duplicate of this one in September: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752)

The duplicate was reported 10 days earlier than mine was, and it has a significantly higher bug heat, but the status is still stuck on "confirmed".

Is there some kind of bug bounty feature where we can donate money to raise the bug heat?

---

