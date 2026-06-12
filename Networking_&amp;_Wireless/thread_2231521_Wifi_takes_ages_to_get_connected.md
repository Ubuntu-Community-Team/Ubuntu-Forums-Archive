---
title: "Wifi takes ages to get connected"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by rompelstilchen on 2014-06-26
Hello,

i installed xubuntu 14.04 LTS and it kept asking me for a keyring pass for the wifi credentials
so i removed the keyring file and as it asked for a new keyring pass, i put a blank one and confirmed
it works fine but the wifi takes between 5 to 10 minutes to get connected

if i go to network connections, no connection are listed

i need the connection to be on cos i want to rdp the box

thx

---

### Post by varunendra on 2014-06-26
Does it connect quickly on a Live session?

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by rompelstilchen on 2014-06-26
maybe my router is the issue, sometimes the connection goes off
i have to ping the box from my windows box, and then i redo a vnc or rdp and it works again
but i did not have that issue with 13.10 beeing updated to 14.04

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

odroid-desktop 3.4.91 armv7l,  Ubuntu 14.04 LTS, trusty

CPU    : 
Memory : 1746 MB
Uptime : 14:44:55 up  5:37,  6 users,  load average: 1.46, 1.26, 1.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 003: ID 0424:3503 Standard Microsystems Corp. 
Bus 001 Device 002: ID 0424:9730 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"***********"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 ***********>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192cu             464530  0 


module parameters ~~~~~~~~~~~~~~~~~~

rtl8192cu    (32): ifname=wlan0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=1 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_initmac=(null) | rtw_intel_class_mode=0 | rtw_ips_mode=0 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
======================o=============o===========o==============o=========o===========o==============o===========
 wlan0  [***********] | 802.11 WiFi | rtl8192cu | connected    | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    ************:    Infra, <MAC C-01 ***********>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    telenet-CE15E:   Infra, <MAC C-10 telenet-CE15E>, Freq 2462 MHz, Rate 2 Mb/s, Strength 49 WPA WPA2
    telenet-5B231:   Infra, <MAC C-06 telenet-5B231>, Freq 2432 MHz, Rate 2 Mb/s, Strength 45 WPA WPA2
    Rabbit Fingusa:  Infra, <MAC C-NA Rabbit Fingusa 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    bbox2-6fc9:      Infra, <MAC C-02 bbox2-6fc9>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    WiFi_93:         Infra, <MAC C-NA WiFi_93 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 30
    TELENETHOMESPOT: Infra, <MAC C-NA TELENETHOMESPOT 1>, Freq 2412 MHz, Rate 2 Mb/s, Strength 29
    FON_BELGACOM:    Infra, <MAC C-NA FON_BELGACOM 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15
    bbox2-4c44:      Infra, <MAC C-NA bbox2-4c44 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    bbox2-844c:      Infra, <MAC C-NA bbox2-844c 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    devolo-bcf2afb66dc6: Infra, <MAC C-NA devolo-bcf2afb66dc6 1>, Freq 2412 MHz, Rate 22 Mb/s, Strength 29 WPA2
    telenet-20C46:   Infra, <MAC C-NA telenet-20C46 1>, Freq 2462 MHz, Rate 2 Mb/s, Strength 30 WPA WPA2

    Address:         ***********.104
    Prefix:          24 (255.255.255.0)
    Gateway:         ***********.1
    DNS:             195.130.131.129
    DNS:             195.130.130.1
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0                 | Wired       | smsc95xx  | unavailable  | no      |           |              | <MAC ID removed>
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

***********          : ssid=*********** | permissions=user:odroid:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home
nameserver 127.0.1.1
search lan


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         ***********.1   0.0.0.0         UG    0      0        0 wlan0
***********.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- ***********.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.322/1.374/1.426/0.052 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.108/0.144/0.181/0.038 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.165/0.201/0.238/0.039 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en)
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 ***********>
                    ESSID:"***********"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=-45 dBm  
          Cell 02 - Address: <MAC C-02 bbox2-6fc9>
                    ESSID:"bbox2-6fc9"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=94/100  Signal level=-82 dBm  
          Cell 03 - Address: <MAC C-03 katrishania>
                    ESSID:"katrishania"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=80/100  Signal level=-82 dBm  
          Cell 04 - Address: <MAC C-04 FON_BELGACOM>
                    ESSID:"FON_BELGACOM"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=-74 dBm  
          Cell 05 - Address: <MAC C-05 Casitas>
                    ESSID:"Casitas"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=86/100  Signal level=-82 dBm  
          Cell 06 - Address: <MAC C-06 telenet-5B231>
                    ESSID:"telenet-5B231"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=88/100  Signal level=-72 dBm  
          Cell 07 - Address: <MAC C-07 bbox2-9780>
                    ESSID:"bbox2-9780"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=-73 dBm  
          Cell 08 - Address: <MAC C-08 SpeedTouch61610>
                    ESSID:"SpeedTouch61610"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=93/100  Signal level=-82 dBm  
          Cell 09 - Address: <MAC C-09 TELENETHOMESPOT>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Quality=100/100  Signal level=-72 dBm  
          Cell 10 - Address: <MAC C-10 telenet-CE15E>
                    ESSID:"telenet-CE15E"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=-71 dBm  
          Cell 11 - Address: <MAC C-11 TELENETHOMESPOT>
                    ESSID:"TELENETHOMESPOT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Quality=68/100  Signal level=-83 dBm  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192cu]
filename:       /lib/modules/3.4.91/kernel/drivers/net/wireless/rtl8192cu/rtl8192cu.ko
version:        v3.4.4_4749.20121105
srcversion:     CBC4FC8A41E8053184C1ECC
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:charp
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_intel_class_mode:The intel class mode [0: off, 1: on] (uint)
parm:           rtw_mc2u_disable:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

console=ttySAC2,115200n8 vmalloc=512M console=tty1 console=ttySAC2,115200n8 root=UUID=e139ce78-9841-40fe-8823-96a304a09859 rootwait ro left=56 right=24 upper=3 lower=3 vsync=3 hsync=14 fb_x_res=1280 fb_y_res=720 vout=hdmi hdmi_phy_res=720p60hz led_blink=1


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    5.028971] ctnetlink v0.93: registering with nfnetlink.
[    5.096573] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.772799] smsc95xx 1-2:1.0: eth0: register 'smsc95xx' at usb-s5p-ehci-2, smsc95xx USB 2.0 Ethernet, <MAC ID removed>
[  330.560020] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  330.567871] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  333.536232] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  345.262964] wlan0: no IPv6 routers present

    ======== Done ========

```

---

### Post by varunendra on 2014-06-26
Is this an ARM processor based system? May not be related, but the kernel is obviously different, and so I'm not sure if all my suggestions would work on it as on normal setups.

The driver you are using is known to have some issues in latest kernels. Try a patched version suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049) and let us know the result.

As a side note, your router is using AES with WPA(1). As far as I know, WPA depends on TKIP, not sure how well it works with AES. I recommend you change the encryption to WPA2 with AES. No WPA, no TKIP.

---

### Post by rompelstilchen on 2014-06-26
> **varunendra said:**
> Is this an ARM processor based system? May not be related, but the kernel is obviously different, and so I'm not sure if all my suggestions would work on it as on normal setups.

The driver you are using is known to have some issues in latest kernels. Try a patched version suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049) and let us know the result.

As a side note, your router is using AES with WPA(1). As far as I know, WPA depends on TKIP, not sure how well it works with AES. I recommend you change the encryption to WPA2 with AES. No WPA, no TKIP.

thx for the reply 
i dont have wpa2

wep
wpa personal
psk2
psk2 mixt
wpa enterprise
psk2+radius
radius

i guess its wpa enterprise

i'll give it a try
[edit : wow there are many options, i am not sure i follow the right path, it asks for a radius, looks like some sort of ip
it also asks for radius port and shared secret, ia m really not a network guru...

and yes, it's an ARM cpu]

---

### Post by rompelstilchen on 2014-06-26
there seem to have a problem with the headers...

odroid@odroid-desktop:~/WORK/rtl8192cu-fixes$ sudo dkms install 8192cu/1.9
Error! Your kernel headers for kernel 3.4.91 cannot be found.
Please install the linux-headers-3.4.91 package,
or use the --kernelsourcedir option to tell DKMS where it's located

odroid@odroid-desktop:~/WORK/rtl8192cu-fixes$ sudo apt-get install linux-headers-3.4.91
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.4.91
E: Couldn't find any package by regex 'linux-headers-3.4.91'

---

### Post by jeremy31 on 2014-06-26
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.91-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.91-quantal/)

You can find headers here

---

### Post by rompelstilchen on 2014-06-26
i downloaded [linux-headers-3.4.91-030491_3.4.91-030491.201405180835_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4.91-quantal/linux-headers-3.4.91-030491_3.4.91-030491.201405180835_all.deb") and installed the package with Software Center

but i cant find the headers anywhere

```

cd /lib/modules/$(uname -r)/build/include/linux
bash: cd: /lib/modules/3.4.91/build/include/linux: No such file or directory

```

but they seem to be installed 
```

 sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.4.91-030491' for regex 'linux-headers-3.4.91'
linux-headers-3.4.91-030491 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

sudo dkms install 8192cu/1.9 --kernelsourcedir /usr/src/linux-headers-$(uname -r)/include
Error! Your kernel headers for kernel 3.4.91 cannot be found.
Please install the linux-headers-3.4.91 package,
or use the --kernelsourcedir option to tell DKMS where it's located

```

and finaly
```


ls /usr/src -l
total 16
drwxr-xr-x  6 root root 4096 Jun 26 18:52 8192cu-1.9
drwxr-xr-x 24 root root 4096 Jun 26 18:50 linux-headers-3.13.0-24
drwxr-xr-x  7 root root 4096 Jun 26 18:50 linux-headers-3.13.0-24-generic
drwxr-xr-x 23 root root 4096 Jun 26 19:56 linux-headers-3.4.91-030491

```

both lines give the same error

```

odroid@odroid-desktop:~/WORK/rtl8192cu-fixes$ sudo dkms install  8192cu/1.9 --kernelsourcedir  /usr/src/linux-headers-3.4.91-030491/include/
odroid@odroid-desktop:~/WORK/rtl8192cu-fixes$  sudo dkms install 8192cu/1.9  --kernelsourcedir=/usr/src/linux-headers-3.4.91-030491/include/

```

---

### Post by rompelstilchen on 2014-06-27
from odroid's forum, odroid's xubuntu 14.04 LTS already use the realtek driver
i am so tired of feeling like exchangind new features with regressions everytime there is a new ubuntu version
anyway thx for the help

[edit : I did not have the issue with my former 13.10 box updated to 14.04...???]

---

### Post by jeremy31 on 2014-06-27
It is looking for the header source files, like you would have for compiling your own kernel.  I am not sure where to find them but they should be at [www.kernel.org](www.kernel.org) somewhere

---

### Post by rompelstilchen on 2014-06-27
> **jeremy31 said:**
> It is looking for the header source files, like you would have for compiling your own kernel.  I am not sure where to find them but they should be at [www.kernel.org]("http://www.kernel.org") somewhere

the xubntu for odroid already have the realtek driver

i did not have that issue with the 13.10=>14.04 box

---

### Post by rompelstilchen on 2014-06-28
any idea ?

with 13.10 updated to 14.04 the wifi connection gets up instantly, so it is not a wpa/wpa2 router issue

---

