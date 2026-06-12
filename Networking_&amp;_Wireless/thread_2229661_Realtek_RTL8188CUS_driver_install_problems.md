---
title: "Realtek RTL8188CUS driver install problems"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by tylerbode on 2014-06-14
so when i try to compile the driver using ```
sudo bash install.sh
```
i got a error message 
```

/home/user/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:999:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/user/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/user/Downloads/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```

here is the result of lsusb so you can see the adapter 
```
Bus 001 Device 004: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless Adapter v1000 [Realtek RTL8188CUS]
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
i got the driver off reateks website and ive looked around and i think i need the right kernel headers but im not sure what ones i need or anything im using ubuntu 14.04. the wifi adapter is seen as wlan0 but its using the wrong driver so when you try to connect to a network it never connects.

---

### Post by varunendra on 2014-06-15
Welcome to the forums tylerbode!

Which driver is it using by default? Is it "rtl8192cu"? If so, it is not a "wrong driver", just a bit buggy in 14.04.

If the driver is "rtl8192cu", try its patched version as mentioned here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

If that doesn't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by tylerbode on 2014-06-17
sorry it took me so long to reply ive havent had any time to try anything. it now sees the networks just fine and doesnt cut out. i tried disabling power managment like the github page said but it still doesnt connect. 

```
   ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

computer 3.13.0-29-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Celeron(R) M processor         1.60GHz
Memory : 993 MB
Uptime : 13:05:26 up 11 min,  2 users,  load average: 0.00, 0.10, 0.12


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a2d]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 004: ID 050d:1102 Belkin Components F7D1102 N150/Surf Micro Wireless Adapter v1000 [Realtek RTL8188CUS]
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

8192cu                473779  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=0 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    AndroidAP:       Infra, <MAC C-02 AndroidAP>, Freq 2437 MHz, Rate 8 Mb/s, Strength 96
    ATT680:          Infra, <MAC C-NA ATT680 1>, Freq 2437 MHz, Rate 16 Mb/s, Strength 26 WPA WPA2
    Home:            Infra, <MAC C-01 Home>, Freq 2412 MHz, Rate 16 Mb/s, Strength 42 WPA WPA2
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e100      | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.273/0.292/0.311/0.019 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.049/0.050/0.051/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Home>
                    ESSID:"Home"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=26/100  
          Cell 02 - Address: <MAC C-02 AndroidAP>
                    ESSID:"AndroidAP"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:72 Mb/s
                    Quality=48/100  Signal level=78/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi 
```

---

### Post by varunendra on 2014-06-19
> **tylerbode said:**
> it now sees the networks just fine and **doesnt cut out**. i tried disabling power managment like the github page said but it **still doesnt connect.**

Please explain clearly. "Doesn't cut out" suggests it gets connected and stays connected, although I'm sure you mean something different, else there was no need to post the report. Also, the report is incomplete. Make sure to run the script without 'sh' or with 'bash', since some of its code is incompatible with 'sh'. For example, run it as './wireless_script' or 'bash wireless_script'.

Assuming you are still unable to connect, please change the encryption type in the router to pure WPA2-PSK with AES (CCMP). No WPA/WPA2 mixed mode, no TKIP. Reboot the router after saving the change. If this doesn't solve the problem, please post a fresh, complete report again.

---

