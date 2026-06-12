---
title: "WNA1000M wireless dongle not working"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by Th3MadHatter on 2014-06-02
Hey all,  So, I got my friends computer a couple of days ago and the thing is ancient, seriously some old Pentium thing. Since she pretty much does nothing else then email and use excel and such I suggested to install Ubuntu instead of the requested Win 7/8 (which was never going to happen with this setup anyway :P) so I put 14.01 TLS on it, it was still slow as hell so switched to lubuntu and that pretty much solved that so everything worked great but I had it hooked up with an ethernet cable so she came over earlier and asked me how she could connect to her equally ancient router (after first telling me that she still had pictures on it and why I didn't back it up after she explicitly asked me to fix it asap and just uninstall everything, ofcourse -_- lol), turns out there was an ancient WNA1000M dongle plugged in the back that I didn't even notice. I figured, "Oh well, how hard can it be", it has a little led light (or something) in it and it was blue so I figured it would work and it did show up as wlan0 so I figured it would work, but it doesnt, it really really doesn't. I tried to connect to a dd-wrt device aswell but that ain't happening either.  I tried to set it up but any threads I could find about ubuntu + a WNA1000M dongle are from 3-4 years ago, all possible links are expired and the general topics are just outdated.  It just doesn't seem to recognize it automatically as a wlan device eventhough it is listed as wlan. I can scan for networks all I want, can try to connect to known working networks but none of it works.  I tried some random things like running a prehistoric broadcom windows driver that should work with it but, it just doesn't.  If I check lsusb it shows up as "Bus 004 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL81588CUS]". I seriously ran out of ideas on how to fix this, i'm not really a network expert (actually I hate anything network related, always have) soooo could someone help me out with this one?  Thanks in advance.

---

### Post by varunendra on 2014-06-05
Welcome to the forums Th3MadHatter !

Please follow the instructions in this post to try a patched driver that should be one the adapter needs : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

If it doesn't work even with that driver, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Th3MadHatter on 2014-06-06
Thanks alot, gonna give that a try ^_^

---

### Post by Th3MadHatter on 2014-06-06
Alright I gave the first one a shot, unfortunately, no dice. The dongle DID start flashing instead of showing a stable blue light but I cant connect to my dd-wrt router by adding it manually through Network Connections (using lubuntu gui) nor can I scan for networks using some sort of app from the ubuntu market called wpa_gui (which doesnt do anything but error out to be honest).

I ran the script from the second option and this is the outcome:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

PC 3.13.0-27-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory : 1746 MB
Uptime : 21:08:12 up 5 min,  2 users,  load average: 0,21, 0,46, 0,27


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:80f8]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d65 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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

8192cu                572859  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | e100      | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.114
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    LAPTOPOUD_Network: Infra, <MAC C-04 LAPTOPOUD_Network>, Freq 2452 MHz, Rate 54 Mb/s, Strength 46 WPA
    UPC WifiSpots:   Infra, <MAC C-02 UPC WifiSpots>, Freq 2412 MHz, Rate 16 Mb/s, Strength 44 WPA2 Enterprise
    UPC1083712:      Infra, <MAC C-01 UPC1083712>, Freq 2412 MHz, Rate 16 Mb/s, Strength 42 WPA WPA2
    VGV751900DE2B:   Infra, <MAC C-NA VGV751900DE2B 1>, Freq 2412 MHz, Rate 16 Mb/s, Strength 42 WPA WPA2
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

Draadloze verbinding 1 : ssid=dd-wrt23 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


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
rtt min/avg/max/mdev = 0.583/0.659/0.735/0.076 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.085/0.115/0.145/0.030 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "nl_NL.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 UPC1083712>
                    ESSID:"UPC1083712"
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
                    Quality=96/100  Signal level=45/100  
          Cell 02 - Address: <MAC C-02 UPC WifiSpots>
                    ESSID:"UPC WifiSpots"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=100/100  Signal level=44/100  
          Cell 03 - Address: <MAC C-03 >
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=65/100  Signal level=26/100  
          Cell 04 - Address: <MAC C-04 LAPTOPOUD_Network>
                    ESSID:"LAPTOPOUD_Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=66/100  Signal level=34/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[8192cu]
filename:       /lib/modules/3.13.0-27-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     0178C5A913EE91E7925ADE1
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
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
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

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

BOOT_IMAGE=/vmlinuz-3.13.0-27-generic root=/dev/mapper/ubuntu--vg-root ro rootflags=sync quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.427739] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.428372] audit: initializing netlink socket (disabled)
[   15.895280] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   15.962048] rtl8192cu driver version=v4.0.2_9000.20130911
[   15.962180] register rtw_netdev_ops to netdev_ops
[   17.091393] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.356445] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[   22.687064] rtl8192cu_hal_init in 560ms
[   22.697639] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.698814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.712336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.726491] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   26.753629] ==> rtl8192cu_hal_deinit 
[   46.003327] ===> ips_netdrv_open.........
[   46.552456] rtl8192cu_hal_init in 552ms
[   48.592717] ==> rtl8192cu_hal_deinit 
[   79.003259] ===> ips_netdrv_open.........
[   79.552705] rtl8192cu_hal_init in 552ms
[   81.592907] ==> rtl8192cu_hal_deinit 
[  122.004759] ===> ips_netdrv_open.........
[  122.556909] rtl8192cu_hal_init in 552ms
[  124.597234] ==> rtl8192cu_hal_deinit 
[  175.002422] ===> ips_netdrv_open.........
[  175.548487] rtl8192cu_hal_init in 548ms
[  177.589122] ==> rtl8192cu_hal_deinit 
[  238.006979] ===> ips_netdrv_open.........
[  238.552434] rtl8192cu_hal_init in 548ms
[  240.592954] ==> rtl8192cu_hal_deinit 
[  301.003139] ===> ips_netdrv_open.........
[  301.568424] rtl8192cu_hal_init in 568ms

    ======== Done ========
```

Hope someone will be able to help me get this to work, I highly doubt she has any money for a new dongle and since it doesnt work over here (on my dd-wrt router) it wont work over there (on her standard not Netgear router she got from her ISP).

Edit: Werid though, if I check the log it shows wireless networks but is unable to connect.

---

### Post by varunendra on 2014-06-07
It doesn't seem to have even tried to connect. Can you try again with the Ethernet cable unplugged?

And is your access-point listed in the 'iwlist scan' section? Which one is it?

---

### Post by Th3MadHatter on 2014-06-07
Yeah I noticed that aswell which is really really weird, I tried unplugging the cable, rebooting with the cable unplugged, all of the basic stuff really but nothings happening at all, I'm sure the SSID I used and password are correct (lol) I'm sure sure I'm in range because both my phone and tablet get full connection just half a foot/meter (whatever) away from the dongle.  It's not in the iwlist scan section because SSID is turned off.

---

### Post by varunendra on 2014-06-07
Can you delete the connection and retry "Connect to a Hidden network.." from NM applet?

The 'iwlist scan' section does show an access-point whose SSID is turned off (Cell - 3), can it be yours?

What are the general settings in the router? (Channel, encryption type, band (2.4/5 GHz or mixed mode), and any other advanced settings)

The fact that it is detecting APs around indicates a possible problem in configuration of the router, if it is not the one in "Cell - 3" of the report.

---

### Post by Th3MadHatter on 2014-06-07
I'm running this with lubuntu as front end, where would one find "Connect to a hidden network". It's not really that important but I do have to test if it actually automatically connects so I can setup her network access to her router without having to go over there a 1000 times lol.  Router should be configured properly because it's been running perfectly on any wireless device (including linux based platforms) for years but as far as the specs go, lemmi add them anyway.  Wireless Mode = AP Wireless Network Mode = Mixed Wireless Network Name (SSID) = dd-wrt23 Wireless Channel = 6 @ 2.437Ghz Sensitivity Range (ACK Timing) = 2000 meters Network Configuration = bridged Security = WPA2 Personal Algorithm = AES Authentication Type = Auto   Basic Rate = Default Transmission Fixed Rate = Auto CTS Protection Mode Auto  Frame Burst = Enabled  As for advanced (doubt you'll need this but lemmi add it anyway) Beacon Interval = 100ms DTIM Interval = 1 Fragmentation Threshold = 2346 RTS Threshold = 2347 Max Associated Clients = 129 AP Isolation = Disabled TX Antenna = Auto RX Antenna = Auto Preamble = Long Shortslot Override = Auto TX Power = 71mW

---

### Post by varunendra on 2014-06-07
> **Th3MadHatter said:**
> I'm running this with lubuntu as front end, where would one find "Connect to a hidden network".
There is a bug in Lubuntu 14.04 due to which the Network Manager GUI (nm-applet) does not load at startup. Fix is here : [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

Once the nm-applet icon is in the notification area, you should see "Connect to Hidden Network" option in its click-to-open menu.

By the way, I am slightly doubtful about this -
> **Th3MadHatter said:**
> Wireless Network Mode = **Mixed**
What kind of 'Mixed'? b/g/n type or 2.4/5 GHz type?

If it is 2.4/5 GHz dual band type mixing, I think you should try fixing it to one of these, not both in mixed mode.

If it is b/g/n type mixed mode, you should try b/g mode if there is an option to fix that.

Obviously I have no more concrete clues and I may be jumping on shadows.

---

### Post by Th3MadHatter on 2014-06-07
No dice.  It does show 2 little computers (no Upstream Downstream arrows) in the corner but if I right click it it's filled with fail.  My options are (Rougly translated):   Enable Network (which is checked)  Enable WiFi (which is checked aswell) Connection information (greyed out)  Edit Connections (which just brings me to the standard network manager I used to setup wireless before) That's it, no networks available to choose from. It looks like something intercepts it because I don't see the iwlist networks at all.  As for the question if it was b/g/n mixed mode, just b/g, it's a wrt54gl, changing does not help.

---

### Post by varunendra on 2014-06-07
I must admit that I may not be paying full attention (half my brain is in the 'urgent' office work), but please post a fresh report of the wireless_script (hope I'm not annoying you with that). Besides that, please also post the full outputs of -
```
lsmod
egrep -i 'wlan|8192|network' /var/log/syslog
```

If I couldn't find anything useful there, I'm afraid I'd have to give up!

---

### Post by Th3MadHatter on 2014-06-07
Ah it's no problem, i'm used to running beta/nightly/dev branch software/OSes etc. so I make my fair share of reports on a daily base :P. 

First the new script log:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

PC 3.13.0-27-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory : 1746 MB
Uptime : 19:32:10 up 4 min,  2 users,  load average: 0,22, 0,51, 0,26


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:80f8]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 002: ID 0461:4d65 Primax Electronics, Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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

8192cu                572859  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o===========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | e100      | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.114
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    LAPTOPOUD_Network: Infra, <MAC C-04 LAPTOPOUD_Network>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA
    UPC1083712:      Infra, <MAC C-01 UPC1083712>, Freq 2412 MHz, Rate 16 Mb/s, Strength 44 WPA WPA2
    VGV751900DE2B:   Infra, <MAC C-NA VGV751900DE2B 1>, Freq 2412 MHz, Rate 16 Mb/s, Strength 44 WPA WPA2
    UPC WifiSpots:   Infra, <MAC C-02 UPC WifiSpots>, Freq 2412 MHz, Rate 16 Mb/s, Strength 44 WPA2 Enterprise
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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search arnhem.chello.nl


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.570/0.580/0.590/0.010 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.075/0.101/0.128/0.028 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "nl_NL.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 UPC1083712>
                    ESSID:"UPC1083712"
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
                    Quality=100/100  Signal level=42/100  
          Cell 02 - Address: <MAC C-02 UPC WifiSpots>
                    ESSID:"UPC WifiSpots"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=86/100  Signal level=43/100  
          Cell 03 - Address: <MAC C-03 >
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=46/100  
          Cell 04 - Address: <MAC C-04 LAPTOPOUD_Network>
                    ESSID:"LAPTOPOUD_Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=26/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[8192cu]
filename:       /lib/modules/3.13.0-27-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     0178C5A913EE91E7925ADE1
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
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
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

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

BOOT_IMAGE=/vmlinuz-3.13.0-27-generic root=/dev/mapper/ubuntu--vg-root ro rootflags=sync quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.426983] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.427555] audit: initializing netlink socket (disabled)
[   15.626871] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   15.646269] rtl8192cu driver version=v4.0.2_9000.20130911
[   15.646486] register rtw_netdev_ops to netdev_ops
[   17.208533] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[   17.429580] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.544511] rtl8192cu_hal_init in 568ms
[   22.557676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.558555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.566301] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   22.591430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.629684] ==> rtl8192cu_hal_deinit 
[   46.004229] ===> ips_netdrv_open.........
[   46.564592] rtl8192cu_hal_init in 560ms
[   48.606694] ==> rtl8192cu_hal_deinit 
[   79.008778] ===> ips_netdrv_open.........
[   79.557343] rtl8192cu_hal_init in 548ms
[   81.601035] ==> rtl8192cu_hal_deinit 
[  122.005333] ===> ips_netdrv_open.........
[  122.560526] rtl8192cu_hal_init in 556ms
[  124.600881] ==> rtl8192cu_hal_deinit 
[  175.003198] ===> ips_netdrv_open.........
[  175.561821] rtl8192cu_hal_init in 560ms
[  177.600909] ==> rtl8192cu_hal_deinit 
[  238.006577] ===> ips_netdrv_open.........
[  238.552653] rtl8192cu_hal_init in 548ms
[  240.592781] ==> rtl8192cu_hal_deinit 
[  270.222003] ===> ips_netdrv_open.........
[  270.776526] rtl8192cu_hal_init in 556ms

    ======== Done ========
```

lsmod:
```
lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39203  1 
cfg80211              409394  0 
gpio_ich               13229  0 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
ip6t_REJECT            12809  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      14318  8 
nf_defrag_ipv6         26163  1 nf_conntrack_ipv6
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
ipt_REJECT             12485  1 
xt_LOG                 17445  10 
xt_multiport           12694  28 
xt_limit               12541  13 
xt_tcpudp              12756  46 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  8 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  16 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
joydev                 17101  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
8192cu                572859  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 20826  1 nf_nat_ftp
snd_timer              28584  2 snd_pcm,snd_seq
nf_conntrack_ftp       14056  1 nf_nat_ftp
i915                  705396  2 
nf_conntrack           83685  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  14 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,xt_multiport,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
video                  18903  1 i915
soundcore              12600  1 snd
drm_kms_helper         46907  1 i915
lpc_ich                16864  0 
shpchp                 32128  0 
drm                   243792  3 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_logitech_dj        18165  0 
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  3 hid_generic,usbhid,hid_logitech_dj
psmouse                91033  0 
e100                   35945  0 
mii                    13654  1 e100
floppy                 55416  0 <- lol yes it still has a floppy drive :P

```

I'll do the grep in another post because it seems to space out if I try to copy and paste anything below this.



 

[/code]

---

### Post by Th3MadHatter on 2014-06-07
This is everything from this session from the moment I booted up until the moment I executed grep

```

Jun  7 19:28:07 PC kernel: [    0.004198] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jun  7 19:28:07 PC kernel: [    0.004204] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jun  7 19:28:07 PC kernel: [    0.266286] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jun  7 19:28:07 PC kernel: [    0.266318] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jun  7 19:28:07 PC kernel: [    0.266375] TCP: Hash tables configured (established 8192 bind 8192)
Jun  7 19:28:07 PC kernel: [    2.692086] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jun  7 19:28:07 PC kernel: [    3.641802] usb 1-3: Product: 802.11n WLAN Adapter
Jun  7 19:28:07 PC kernel: [    4.039137] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Jun  7 19:28:07 PC kernel: [   15.449997] type=1400 audit(1402162086.059:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=368 comm="apparmor_parser"
Jun  7 19:28:07 PC kernel: [   15.454344] type=1400 audit(1402162086.063:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=368 comm="apparmor_parser"
Jun  7 19:28:07 PC kernel: [   15.626871] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
Jun  7 19:28:07 PC kernel: [   15.646269] rtl8192cu driver version=v4.0.2_9000.20130911
Jun  7 19:28:07 PC kernel: [   15.646464] CHIP TYPE: RTL8188C_8192C
Jun  7 19:28:07 PC kernel: [   15.684772] ====> ReadAdapterInfo8192C
Jun  7 19:28:07 PC kernel: [   17.206612] readAdapterInfo_8192CU(): REPLACEMENT = 1
Jun  7 19:28:07 PC kernel: [   17.206618] <==== ReadAdapterInfo8192C in 1520 ms
Jun  7 19:28:07 PC kernel: [   17.208692] usbcore: registered new interface driver rtl8192cu
Jun  7 19:28:08 PC avahi-daemon[680]: Network interface enumeration completed.
Jun  7 19:28:11 PC NetworkManager[802]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun  7 19:28:11 PC NetworkManager[802]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun  7 19:28:11 PC NetworkManager[802]: <info> WEXT support is enabled
Jun  7 19:28:12 PC NetworkManager[802]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun  7 19:28:12 PC NetworkManager[802]: <info> DNS: loaded plugin dnsmasq
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: init!
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: update_system_hostname
Jun  7 19:28:12 PC NetworkManager[802]:       interface-parser: parsing file /etc/network/interfaces
Jun  7 19:28:12 PC NetworkManager[802]:       interface-parser: finished parsing file /etc/network/interfaces
Jun  7 19:28:12 PC NetworkManager[802]:    SCPluginIfupdown: management mode: unmanaged
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0)
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: end _init.
Jun  7 19:28:12 PC NetworkManager[802]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  7 19:28:12 PC NetworkManager[802]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ofono: init!
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ofono: end _init.
Jun  7 19:28:12 PC NetworkManager[802]: <info> Loaded plugin (null): (null)
Jun  7 19:28:12 PC NetworkManager[802]:    Ifupdown: get unmanaged devices count: 0
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: (145858512) ... get_connections.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ifupdown: (145858512) ... get_connections (managed=false): return empty list.
Jun  7 19:28:12 PC NetworkManager[802]:    keyfile: parsing Wired connection 1 ... 
Jun  7 19:28:12 PC NetworkManager[802]:    keyfile:     read connection 'Wired connection 1'
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ofono: (145750240) ... get_connections.
Jun  7 19:28:12 PC NetworkManager[802]:    SCPlugin-Ofono: (145750240) connections count: 0
Jun  7 19:28:12 PC NetworkManager[802]:    Ifupdown: get unmanaged devices count: 0
Jun  7 19:28:12 PC NetworkManager[802]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  7 19:28:12 PC NetworkManager[802]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  7 19:28:12 PC NetworkManager[802]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  7 19:28:12 PC NetworkManager[802]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  7 19:28:12 PC NetworkManager[802]: <info> Networking is enabled by state file
Jun  7 19:28:12 PC NetworkManager[802]: <warn> failed to allocate link cache: (-12) Object not found
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): driver supports SSID scans (scan_capa 0x3F).
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): using WEXT for WiFi device control
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 3)
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 19:28:12 PC NetworkManager[802]: <info> (wlan0): bringing up device.
Jun  7 19:28:13 PC kernel: [   22.544511] rtl8192cu_hal_init in 568ms
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): preparing device.
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): taking down device.
Jun  7 19:28:13 PC kernel: [   22.557676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 19:28:13 PC kernel: [   22.558555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 19:28:13 PC kernel: [   22.566301] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): bringing up device.
Jun  7 19:28:13 PC kernel: [   22.591430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 19:28:13 PC NetworkManager[802]: <warn> failed to allocate link cache: (-12) Object not found
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): carrier is OFF
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): new Ethernet device (driver: 'e100' ifindex: 2)
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): bringing up device.
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): preparing device.
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun  7 19:28:13 PC NetworkManager[802]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  7 19:28:13 PC NetworkManager[802]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): carrier now ON (device state 20)
Jun  7 19:28:13 PC NetworkManager[802]: <info> urfkill disappeared from the bus
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun  7 19:28:13 PC NetworkManager[802]: <info> Auto-activating connection 'Wired connection 1'.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  7 19:28:13 PC NetworkManager[802]: <info> NetworkManager state is now CONNECTING
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  7 19:28:13 PC NetworkManager[802]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  7 19:28:13 PC NetworkManager[802]: <info> dhclient started with pid 837
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun  7 19:28:13 PC NetworkManager[802]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  7 19:28:13 PC NetworkManager[802]: <info> ModemManager available in the bus
Jun  7 19:28:13 PC NetworkManager[802]: <info> wpa_supplicant started
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 19:28:13 PC NetworkManager[802]: <warn> Trying to remove a non-existant call id.
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun  7 19:28:13 PC NetworkManager[802]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 19:28:13 PC kernel: [   23.199308] type=1400 audit(1402162093.807:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/libNetworkManager/nm-dhcp-client.action" pid=926 comm="apparmor_parser"
Jun  7 19:28:13 PC kernel: [   23.201403] type=1400 audit(1402162093.811:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/libNetworkManager/nm-dhcp-client.action" pid=926 comm="apparmor_parser"
Jun  7 19:28:14 PC kernel: [   24.145607] survey done event(e) band:0 for wlan0
Jun  7 19:28:14 PC NetworkManager[802]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun  7 19:28:14 PC NetworkManager[802]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  7 19:28:16 PC kernel: [   25.528171] survey done event(a) band:0 for wlan0
Jun  7 19:28:16 PC NetworkManager[802]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun  7 19:28:16 PC NetworkManager[802]: <info>   address 192.168.1.114
Jun  7 19:28:16 PC NetworkManager[802]: <info>   prefix 24 (255.255.255.0)
Jun  7 19:28:16 PC NetworkManager[802]: <info>   gateway 192.168.1.1
Jun  7 19:28:16 PC NetworkManager[802]: <info>   hostname 'PC'
Jun  7 19:28:16 PC NetworkManager[802]: <info>   nameserver '192.168.1.1'
Jun  7 19:28:16 PC NetworkManager[802]: <info>   domain name 'arnhem.chello.nl'
Jun  7 19:28:16 PC NetworkManager[802]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  7 19:28:16 PC NetworkManager[802]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  7 19:28:17 PC kernel: [   26.629684] ==> rtl8192cu_hal_deinit 
Jun  7 19:28:17 PC NetworkManager[802]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  7 19:28:17 PC NetworkManager[802]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  7 19:28:17 PC NetworkManager[802]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  7 19:28:17 PC NetworkManager[802]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  7 19:28:17 PC NetworkManager[802]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  7 19:28:17 PC NetworkManager[802]: <info> DNS: starting dnsmasq...
Jun  7 19:28:17 PC NetworkManager[802]: <warn> dnsmasq not available on the bus, can't update servers.
Jun  7 19:28:17 PC NetworkManager[802]: <error> [1402162097.412729] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  7 19:28:17 PC NetworkManager[802]: <warn> DNS: plugin dnsmasq update failed
Jun  7 19:28:17 PC NetworkManager[802]: <info> Writing DNS information to /sbin/resolvconf
Jun  7 19:28:18 PC NetworkManager[802]: <info> Activation (eth0) successful, device activated.
Jun  7 19:28:18 PC NetworkManager[802]: <warn> dnsmasq appeared on DBus: :1.18
Jun  7 19:28:18 PC NetworkManager[802]: <info> Writing DNS information to /sbin/resolvconf
Jun  7 19:28:22 PC NetworkManager[802]: <info> WiFi hardware radio set enabled
Jun  7 19:28:33 PC NetworkManager[802]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  7 19:28:33 PC NetworkManager[802]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  7 19:28:33 PC NetworkManager[802]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  7 19:28:33 PC NetworkManager[802]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  7 19:28:37 PC kernel: [   46.564592] rtl8192cu_hal_init in 560ms
Jun  7 19:28:38 PC kernel: [   47.889917] survey done event(9) band:0 for wlan0
Jun  7 19:28:39 PC kernel: [   48.606694] ==> rtl8192cu_hal_deinit 
Jun  7 19:29:10 PC kernel: [   79.557343] rtl8192cu_hal_init in 548ms
Jun  7 19:29:11 PC kernel: [   80.885914] survey done event(3) band:0 for wlan0
Jun  7 19:29:12 PC kernel: [   81.601035] ==> rtl8192cu_hal_deinit 
Jun  7 19:29:53 PC kernel: [  122.560526] rtl8192cu_hal_init in 556ms
Jun  7 19:29:54 PC kernel: [  123.889973] survey done event(6) band:0 for wlan0
Jun  7 19:29:55 PC kernel: [  124.600881] ==> rtl8192cu_hal_deinit 
Jun  7 19:30:46 PC kernel: [  175.561821] rtl8192cu_hal_init in 560ms
Jun  7 19:30:47 PC kernel: [  176.889898] survey done event(8) band:0 for wlan0
Jun  7 19:30:48 PC kernel: [  177.600909] ==> rtl8192cu_hal_deinit 
Jun  7 19:31:49 PC kernel: [  238.552653] rtl8192cu_hal_init in 548ms
Jun  7 19:31:50 PC kernel: [  239.877935] survey done event(7) band:0 for wlan0
Jun  7 19:31:51 PC kernel: [  240.592781] ==> rtl8192cu_hal_deinit 
Jun  7 19:32:21 PC kernel: [  270.776526] rtl8192cu_hal_init in 556ms
Jun  7 19:32:22 PC kernel: [  272.097935] survey done event(6) band:0 for wlan0
Jun  7 19:32:23 PC kernel: [  272.816763] ==> rtl8192cu_hal_deinit 
Jun  7 19:32:52 PC kernel: [  301.544398] rtl8192cu_hal_init in 544ms
Jun  7 19:32:53 PC kernel: [  302.869931] survey done event(b) band:0 for wlan0
Jun  7 19:33:56 PC kernel: [  365.322044] survey done event(3) band:0 for wlan0
Jun  7 19:34:59 PC kernel: [  428.313879] survey done event(1) band:0 for wlan0
Jun  7 19:36:02 PC kernel: [  491.317875] survey done event(5) band:0 for wlan0
Jun  7 19:37:05 PC kernel: [  554.313990] survey done event(2) band:0 for wlan0
Jun  7 19:38:08 PC kernel: [  617.317986] survey done event(1) band:0 for wlan0
Jun  7 19:39:11 PC kernel: [  680.313850] survey done event(2) band:0 for wlan0
Jun  7 19:40:14 PC kernel: [  743.317972] survey done event(4) band:0 for wlan0
Jun  7 19:41:17 PC kernel: [  806.313999] survey done event(5) band:0 for wlan0
Jun  7 19:42:20 PC kernel: [  869.313955] survey done event(5) band:0 for wlan0
Jun  7 19:43:23 PC kernel: [  932.313944] survey done event(3) band:0 for wlan0
Jun  7 19:44:26 PC kernel: [  995.322078] survey done event(2) band:0 for wlan0

```

This is everything from before that, it should have a couple wireless sessions in it aswell.

```
 Jun  7 13:48:51 PC NetworkManager[807]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  7 13:48:51 PC NetworkManager[807]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  7 13:49:53 PC kernel: [  363.313976] survey done event(d) band:0 for wlan0
Jun  7 13:50:56 PC kernel: [  426.317958] survey done event(10) band:0 for wlan0
Jun  7 13:51:59 PC kernel: [  489.321969] survey done event(10) band:0 for wlan0
Jun  7 13:53:02 PC kernel: [  552.326598] survey done event(10) band:0 for wlan0
Jun  7 13:54:05 PC kernel: [  615.317956] survey done event(10) band:0 for wlan0
Jun  7 13:55:08 PC kernel: [  678.317882] survey done event(4) band:0 for wlan0
Jun  7 13:56:53 PC kernel: [    0.004200] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jun  7 13:56:53 PC kernel: [    0.004205] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jun  7 13:56:53 PC kernel: [    0.266484] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jun  7 13:56:53 PC kernel: [    0.266517] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jun  7 13:56:53 PC kernel: [    0.266573] TCP: Hash tables configured (established 8192 bind 8192)
Jun  7 13:56:53 PC kernel: [    2.692121] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jun  7 13:56:53 PC kernel: [    3.473710] usb 1-3: Product: 802.11n WLAN Adapter
Jun  7 13:56:53 PC kernel: [    4.074416] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Jun  7 13:56:53 PC kernel: [   15.256364] type=1400 audit(1402142211.875:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=376 comm="apparmor_parser"
Jun  7 13:56:53 PC kernel: [   15.257698] type=1400 audit(1402142211.875:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=376 comm="apparmor_parser"
Jun  7 13:56:53 PC kernel: [   15.766885] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
Jun  7 13:56:53 PC kernel: [   15.786929] rtl8192cu driver version=v4.0.2_9000.20130911
Jun  7 13:56:53 PC kernel: [   15.787150] CHIP TYPE: RTL8188C_8192C
Jun  7 13:56:53 PC kernel: [   15.800413] ====> ReadAdapterInfo8192C
Jun  7 13:56:53 PC kernel: [   17.314711] readAdapterInfo_8192CU(): REPLACEMENT = 1
Jun  7 13:56:53 PC kernel: [   17.314718] <==== ReadAdapterInfo8192C in 1512 ms
Jun  7 13:56:53 PC kernel: [   17.316886] usbcore: registered new interface driver rtl8192cu
Jun  7 13:56:54 PC avahi-daemon[656]: Network interface enumeration completed.
Jun  7 13:56:58 PC NetworkManager[806]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun  7 13:56:58 PC NetworkManager[806]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun  7 13:56:58 PC NetworkManager[806]: <info> WEXT support is enabled
Jun  7 13:56:58 PC NetworkManager[806]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun  7 13:56:58 PC NetworkManager[806]: <info> DNS: loaded plugin dnsmasq
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: init!
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: update_system_hostname
Jun  7 13:56:58 PC NetworkManager[806]:       interface-parser: parsing file /etc/network/interfaces
Jun  7 13:56:58 PC NetworkManager[806]:       interface-parser: finished parsing file /etc/network/interfaces
Jun  7 13:56:58 PC NetworkManager[806]:    SCPluginIfupdown: management mode: unmanaged
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0)
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: end _init.
Jun  7 13:56:58 PC NetworkManager[806]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  7 13:56:58 PC NetworkManager[806]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ofono: init!
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ofono: end _init.
Jun  7 13:56:58 PC NetworkManager[806]: <info> Loaded plugin (null): (null)
Jun  7 13:56:58 PC NetworkManager[806]:    Ifupdown: get unmanaged devices count: 0
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: (154535768) ... get_connections.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ifupdown: (154535768) ... get_connections (managed=false): return empty list.
Jun  7 13:56:58 PC NetworkManager[806]:    keyfile: parsing Draadloze verbinding 1 ... 
Jun  7 13:56:58 PC NetworkManager[806]:    keyfile:     read connection 'Draadloze verbinding 1'
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ofono: (154589408) ... get_connections.
Jun  7 13:56:58 PC NetworkManager[806]:    SCPlugin-Ofono: (154589408) connections count: 0
Jun  7 13:56:58 PC NetworkManager[806]:    Ifupdown: get unmanaged devices count: 0
Jun  7 13:56:58 PC NetworkManager[806]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  7 13:56:58 PC NetworkManager[806]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  7 13:56:58 PC NetworkManager[806]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  7 13:56:58 PC NetworkManager[806]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  7 13:56:58 PC NetworkManager[806]: <info> Networking is enabled by state file
Jun  7 13:56:58 PC NetworkManager[806]: <warn> failed to allocate link cache: (-12) Object not found
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): driver supports SSID scans (scan_capa 0x3F).
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): using WEXT for WiFi device control
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 3)
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 13:56:58 PC NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  7 13:56:59 PC kernel: [   22.745046] type=1400 audit(1402142219.363:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/libNetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
Jun  7 13:56:59 PC kernel: [   22.746378] type=1400 audit(1402142219.363:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/libNetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
Jun  7 13:56:59 PC kernel: [   22.787622] rtl8192cu_hal_init in 568ms
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): preparing device.
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): taking down device.
Jun  7 13:56:59 PC kernel: [   22.801298] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 13:56:59 PC kernel: [   22.802585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 13:56:59 PC kernel: [   22.813184] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Jun  7 13:56:59 PC kernel: [   22.815161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  7 13:56:59 PC NetworkManager[806]: <warn> failed to allocate link cache: (-12) Object not found
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): carrier is OFF
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): new Ethernet device (driver: 'e100' ifindex: 2)
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): bringing up device.
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): preparing device.
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun  7 13:56:59 PC NetworkManager[806]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0
Jun  7 13:56:59 PC NetworkManager[806]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  7 13:56:59 PC NetworkManager[806]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): carrier now ON (device state 20)
Jun  7 13:56:59 PC NetworkManager[806]: <info> urfkill disappeared from the bus
Jun  7 13:56:59 PC NetworkManager[806]: <info> wpa_supplicant started
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun  7 13:56:59 PC NetworkManager[806]: <info> ModemManager available in the bus
Jun  7 13:56:59 PC NetworkManager[806]: <info> Auto-activating connection 'Wired connection 1'.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  7 13:56:59 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTING
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  7 13:56:59 PC NetworkManager[806]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  7 13:56:59 PC NetworkManager[806]: <info> dhclient started with pid 883
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun  7 13:56:59 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 13:56:59 PC NetworkManager[806]: <warn> Trying to remove a non-existant call id.
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun  7 13:56:59 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 13:57:00 PC kernel: [   24.262018] survey done event(7) band:0 for wlan0
Jun  7 13:57:00 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun  7 13:57:00 PC NetworkManager[806]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  7 13:57:02 PC kernel: [   25.627769] survey done event(e) band:0 for wlan0
Jun  7 13:57:03 PC kernel: [   26.853505] ==> rtl8192cu_hal_deinit 
Jun  7 13:57:07 PC NetworkManager[806]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  7 13:57:07 PC NetworkManager[806]: <info>   address 192.168.1.114
Jun  7 13:57:07 PC NetworkManager[806]: <info>   prefix 24 (255.255.255.0)
Jun  7 13:57:07 PC NetworkManager[806]: <info>   gateway 192.168.1.1
Jun  7 13:57:07 PC NetworkManager[806]: <info>   hostname 'PC'
Jun  7 13:57:07 PC NetworkManager[806]: <info>   nameserver '192.168.1.1'
Jun  7 13:57:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  7 13:57:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  7 13:57:08 PC NetworkManager[806]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  7 13:57:08 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  7 13:57:08 PC NetworkManager[806]: <info> WiFi hardware radio set enabled
Jun  7 13:57:08 PC NetworkManager[806]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  7 13:57:09 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  7 13:57:09 PC NetworkManager[806]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  7 13:57:09 PC NetworkManager[806]: <info> DNS: starting dnsmasq...
Jun  7 13:57:09 PC NetworkManager[806]: <warn> dnsmasq not available on the bus, can't update servers.
Jun  7 13:57:09 PC NetworkManager[806]: <error> [1402142229.74118] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  7 13:57:09 PC NetworkManager[806]: <warn> DNS: plugin dnsmasq update failed
Jun  7 13:57:09 PC NetworkManager[806]: <info> Writing DNS information to /sbin/resolvconf
Jun  7 13:57:19 PC NetworkManager[806]: <info> Activation (eth0) successful, device activated.
Jun  7 13:57:19 PC NetworkManager[806]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  7 13:57:19 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  7 13:57:19 PC NetworkManager[806]: <warn> dnsmasq appeared on DBus: :1.22
Jun  7 13:57:19 PC NetworkManager[806]: <info> Writing DNS information to /sbin/resolvconf
Jun  7 13:57:30 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  7 13:57:30 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  7 13:57:30 PC kernel: [   53.949171] rtl8192cu_hal_init in 568ms
Jun  7 13:57:31 PC kernel: [   55.274060] survey done event(f) band:0 for wlan0
Jun  7 13:57:32 PC kernel: [   55.993207] ==> rtl8192cu_hal_deinit 
Jun  7 13:58:04 PC kernel: [   87.569694] rtl8192cu_hal_init in 564ms
Jun  7 13:58:05 PC kernel: [   88.894452] survey done event(7) band:0 for wlan0
Jun  7 13:58:06 PC kernel: [   89.609616] ==> rtl8192cu_hal_deinit 
Jun  7 13:58:47 PC kernel: [  130.564497] rtl8192cu_hal_init in 564ms
Jun  7 13:58:48 PC kernel: [  131.890189] survey done event(10) band:0 for wlan0
Jun  7 13:58:49 PC kernel: [  132.611726] ==> rtl8192cu_hal_deinit 
Jun  7 13:58:54 PC NetworkManager[806]:    keyfile: removed /etc/NetworkManager/system-connections/Draadloze verbinding 1.
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): device state change: activated -> disconnected (reason 'connection-removed') [100 30 38]
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): deactivating device (reason 'connection-removed') [38]
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): canceled DHCP transaction, DHCP client pid 883
Jun  7 13:59:07 PC NetworkManager[806]: <warn> DNS: plugin dnsmasq update failed
Jun  7 13:59:07 PC NetworkManager[806]: <info> Removing DNS information from /sbin/resolvconf
Jun  7 13:59:07 PC NetworkManager[806]: <info> NetworkManager state is now DISCONNECTED
Jun  7 13:59:07 PC NetworkManager[806]: <info> Saved default wired connection 'Wired connection 1' to persistent storage
Jun  7 13:59:07 PC NetworkManager[806]: <info> Auto-activating connection 'Wired connection 1'.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  7 13:59:07 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTING
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  7 13:59:07 PC NetworkManager[806]: <info> dhclient started with pid 1877
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun  7 13:59:07 PC NetworkManager[806]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  7 13:59:07 PC NetworkManager[806]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  7 13:59:08 PC NetworkManager[806]:    Ifupdown: get unmanaged devices count: 0
Jun  7 13:59:08 PC NetworkManager[806]:    Ifupdown: get unmanaged devices count: 0
Jun  7 13:59:10 PC NetworkManager[806]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun  7 13:59:10 PC NetworkManager[806]: <info>   address 192.168.1.114
Jun  7 13:59:10 PC NetworkManager[806]: <info>   prefix 24 (255.255.255.0)
Jun  7 13:59:10 PC NetworkManager[806]: <info>   gateway 192.168.1.1
Jun  7 13:59:10 PC NetworkManager[806]: <info>   hostname 'PC'
Jun  7 13:59:10 PC NetworkManager[806]: <info>   nameserver '192.168.1.1'
Jun  7 13:59:10 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  7 13:59:10 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  7 13:59:11 PC NetworkManager[806]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  7 13:59:11 PC NetworkManager[806]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  7 13:59:11 PC NetworkManager[806]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  7 13:59:11 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  7 13:59:11 PC NetworkManager[806]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  7 13:59:11 PC NetworkManager[806]: <info> Writing DNS information to /sbin/resolvconf
Jun  7 13:59:21 PC NetworkManager[806]: <info> Activation (eth0) successful, device activated.
Jun  7 13:59:28 PC NetworkManager[806]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  7 13:59:28 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  7 13:59:28 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  7 13:59:28 PC NetworkManager[806]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  7 13:59:40 PC kernel: [  183.569051] rtl8192cu_hal_init in 564ms
Jun  7 13:59:41 PC kernel: [  184.889940] survey done event(a) band:0 for wlan0
Jun  7 13:59:42 PC kernel: [  185.608908] ==> rtl8192cu_hal_deinit 
Jun  7 14:00:43 PC kernel: [  246.553151] rtl8192cu_hal_init in 548ms
Jun  7 14:00:44 PC kernel: [  247.877935] survey done event(5) band:0 for wlan0
Jun  7 14:00:45 PC kernel: [  248.593482] ==> rtl8192cu_hal_deinit 
Jun  7 14:01:31 PC NetworkManager[806]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  7 14:01:33 PC NetworkManager[806]: <info> (eth0): carrier now ON (device state 100)
Jun  7 14:01:46 PC kernel: [  309.572391] rtl8192cu_hal_init in 564ms
Jun  7 14:01:47 PC kernel: [  310.893922] survey done event(9) band:0 for wlan0
Jun  7 14:02:49 PC kernel: [  373.313888] survey done event(3) band:0 for wlan0
Jun  7 14:03:52 PC kernel: [  436.317880] survey done event(7) band:0 for wlan0
Jun  7 14:04:55 PC kernel: [  499.313871] survey done event(5) band:0 for wlan0
Jun  7 14:05:59 PC kernel: [  562.313863] survey done event(8) band:0 for wlan0
Jun  7 14:07:02 PC kernel: [  625.313857] survey done event(7) band:0 for wlan0
Jun  7 14:08:05 PC kernel: [  688.317850] survey done event(a) band:0 for wlan0
Jun  7 14:09:08 PC kernel: [  751.313840] survey done event(11) band:0 for wlan0
Jun  7 14:10:11 PC kernel: [  814.317834] survey done event(c) band:0 for wlan0
Jun  7 14:11:14 PC kernel: [  877.313948] survey done event(8) band:0 for wlan0
Jun  7 14:12:17 PC kernel: [  940.317944] survey done event(6) band:0 for wlan0
Jun  7 14:13:20 PC kernel: [ 1003.313934] survey done event(9) band:0 for wlan0
Jun  7 14:14:23 PC kernel: [ 1066.317926] survey done event(9) band:0 for wlan0
Jun  7 14:15:26 PC kernel: [ 1129.313918] survey done event(9) band:0 for wlan0
Jun  7 14:16:29 PC kernel: [ 1192.317912] survey done event(5) band:0 for wlan0
Jun  7 14:17:32 PC kernel: [ 1255.313904] survey done event(6) band:0 for wlan0
Jun  7 14:18:35 PC kernel: [ 1318.317897] survey done event(a) band:0 for wlan0
Jun  7 14:19:38 PC kernel: [ 1381.313888] survey done event(7) band:0 for wlan0
Jun  7 14:20:41 PC kernel: [ 1444.317880] survey done event(9) band:0 for wlan0
Jun  7 14:21:44 PC kernel: [ 1507.313872] survey done event(9) band:0 for wlan0
Jun  7 14:22:47 PC kernel: [ 1570.317865] survey done event(8) band:0 for wlan0
Jun  7 14:23:50 PC kernel: [ 1633.317976] survey done event(6) band:0 for wlan0
Jun  7 14:24:53 PC kernel: [ 1696.317953] survey done event(c) band:0 for wlan0
Jun  7 14:25:56 PC kernel: [ 1759.313927] survey done event(6) band:0 for wlan0
Jun  7 14:26:59 PC kernel: [ 1822.318072] survey done event(a) band:0 for wlan0
Jun  7 14:28:02 PC kernel: [ 1885.317879] survey done event(6) band:0 for wlan0
Jun  7 14:29:05 PC kernel: [ 1948.317978] survey done event(6) band:0 for wlan0
Jun  7 14:30:08 PC kernel: [ 2011.317955] survey done event(a) band:0 for wlan0
Jun  7 14:31:11 PC kernel: [ 2074.313930] survey done event(8) band:0 for wlan0
Jun  7 14:32:14 PC kernel: [ 2137.313917] survey done event(a) band:0 for wlan0
Jun  7 14:33:17 PC kernel: [ 2200.317883] survey done event(a) band:0 for wlan0
Jun  7 14:34:20 PC kernel: [ 2263.314550] survey done event(b) band:0 for wlan0
Jun  7 14:34:47 PC NetworkManager[806]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  7 14:34:51 PC NetworkManager[806]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Jun  7 14:34:51 PC NetworkManager[806]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Jun  7 14:34:52 PC NetworkManager[806]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1877
Jun  7 14:34:52 PC NetworkManager[806]: <warn> DNS: plugin dnsmasq update failed
Jun  7 14:34:52 PC NetworkManager[806]: <info> Removing DNS information from /sbin/resolvconf
Jun  7 14:34:52 PC NetworkManager[806]: <info> NetworkManager state is now DISCONNECTED
Jun  7 14:35:23 PC kernel: [ 2326.313904] survey done event(b) band:0 for wlan0
Jun  7 14:35:49 PC NetworkManager[806]: <info> disable requested (sleeping: no  enabled: yes)
Jun  7 14:35:49 PC NetworkManager[806]: <info> sleeping or disabling...
Jun  7 14:35:49 PC NetworkManager[806]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Jun  7 14:35:49 PC NetworkManager[806]: <info> (wlan0): cleaning up...
Jun  7 14:35:49 PC NetworkManager[806]: <info> (wlan0): taking down device.
Jun  7 14:35:49 PC NetworkManager[806]: <info> NetworkManager state is now ASLEEP
Jun  7 14:35:49 PC NetworkManager[806]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jun  7 14:35:49 PC NetworkManager[806]: <info> (eth0): cleaning up...
Jun  7 14:35:49 PC NetworkManager[806]: <info> (eth0): taking down device.
Jun  7 14:35:49 PC kernel: [ 2352.785811] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Jun  7 14:35:51 PC kernel: [ 2354.121957] survey done event(13) band:0 for wlan0
Jun  7 14:35:52 PC NetworkManager[806]: <info> enable requested (sleeping: no  enabled: no)
Jun  7 14:35:52 PC NetworkManager[806]: <info> waking up and re-enabling...
Jun  7 14:35:52 PC NetworkManager[806]: <info> WWAN now enabled by management service
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): preparing device.
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  7 14:35:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 14:35:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 14:35:52 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  7 14:35:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 14:35:52 PC kernel: [ 2355.697863] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 14:35:52 PC NetworkManager[806]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 14:35:52 PC NetworkManager[806]: <info> (eth0): bringing up device.
Jun  7 14:35:52 PC NetworkManager[806]: <info> (eth0): preparing device.
Jun  7 14:35:52 PC NetworkManager[806]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun  7 14:35:52 PC NetworkManager[806]: <info> NetworkManager state is now DISCONNECTED
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  7 14:35:52 PC NetworkManager[806]: <warn> Trying to remove a non-existant call id.
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun  7 14:35:52 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 14:35:53 PC kernel: [ 2357.033869] survey done event(b) band:0 for wlan0
Jun  7 14:35:54 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun  7 14:35:55 PC kernel: [ 2358.373939] survey done event(e) band:0 for wlan0
Jun  7 14:35:56 PC kernel: [ 2359.728715] ==> rtl8192cu_hal_deinit 
Jun  7 14:36:16 PC kernel: [ 2379.548357] rtl8192cu_hal_init in 544ms
Jun  7 14:36:17 PC kernel: [ 2380.869826] survey done event(a) band:0 for wlan0
Jun  7 14:36:18 PC kernel: [ 2381.588846] ==> rtl8192cu_hal_deinit 
Jun  7 14:36:49 PC kernel: [ 2412.548322] rtl8192cu_hal_init in 548ms
Jun  7 14:36:50 PC kernel: [ 2413.869810] survey done event(c) band:0 for wlan0
Jun  7 14:36:51 PC kernel: [ 2414.588846] ==> rtl8192cu_hal_deinit 
Jun  7 14:37:32 PC kernel: [ 2455.544317] rtl8192cu_hal_init in 540ms
Jun  7 14:37:33 PC kernel: [ 2456.865826] survey done event(9) band:0 for wlan0
Jun  7 14:37:34 PC kernel: [ 2457.584798] ==> rtl8192cu_hal_deinit 
Jun  7 14:38:25 PC kernel: [ 2508.544440] rtl8192cu_hal_init in 544ms
Jun  7 14:38:26 PC kernel: [ 2509.865844] survey done event(e) band:0 for wlan0
Jun  7 14:38:27 PC kernel: [ 2510.584752] ==> rtl8192cu_hal_deinit 
Jun  7 14:39:28 PC kernel: [ 2571.556487] rtl8192cu_hal_init in 552ms
Jun  7 14:39:29 PC kernel: [ 2572.881910] survey done event(14) band:0 for wlan0
Jun  7 14:39:30 PC kernel: [ 2573.596850] ==> rtl8192cu_hal_deinit 
Jun  7 14:40:31 PC kernel: [ 2634.560388] rtl8192cu_hal_init in 560ms
Jun  7 14:40:32 PC kernel: [ 2635.881826] survey done event(f) band:0 for wlan0
Jun  7 14:40:33 PC kernel: [ 2636.600680] ==> rtl8192cu_hal_deinit 
Jun  7 14:41:34 PC kernel: [ 2697.572824] rtl8192cu_hal_init in 568ms
Jun  7 14:41:35 PC kernel: [ 2698.901899] survey done event(d) band:0 for wlan0
Jun  7 14:41:36 PC kernel: [ 2699.613205] ==> rtl8192cu_hal_deinit 
Jun  7 14:42:37 PC kernel: [ 2760.552407] rtl8192cu_hal_init in 552ms
Jun  7 14:42:38 PC kernel: [ 2761.877868] survey done event(e) band:0 for wlan0
Jun  7 14:42:39 PC kernel: [ 2762.593123] ==> rtl8192cu_hal_deinit 
Jun  7 14:43:40 PC kernel: [ 2823.548393] rtl8192cu_hal_init in 544ms
Jun  7 14:43:41 PC kernel: [ 2824.873862] survey done event(a) band:0 for wlan0
Jun  7 14:43:42 PC kernel: [ 2825.589123] ==> rtl8192cu_hal_deinit 
Jun  7 14:44:43 PC kernel: [ 2886.548318] rtl8192cu_hal_init in 548ms
Jun  7 14:44:44 PC kernel: [ 2887.869917] survey done event(f) band:0 for wlan0
Jun  7 14:44:45 PC kernel: [ 2888.588866] ==> rtl8192cu_hal_deinit 
Jun  7 14:45:46 PC kernel: [ 2949.548365] rtl8192cu_hal_init in 544ms
Jun  7 14:45:47 PC kernel: [ 2950.873844] survey done event(7) band:0 for wlan0
Jun  7 14:45:48 PC kernel: [ 2951.589171] ==> rtl8192cu_hal_deinit 
Jun  7 14:46:49 PC kernel: [ 3012.544358] rtl8192cu_hal_init in 544ms
Jun  7 14:46:50 PC kernel: [ 3013.865841] survey done event(b) band:0 for wlan0
Jun  7 14:46:51 PC kernel: [ 3014.584815] ==> rtl8192cu_hal_deinit 
Jun  7 14:47:52 PC kernel: [ 3075.552500] rtl8192cu_hal_init in 548ms
Jun  7 14:47:53 PC kernel: [ 3076.877858] survey done event(f) band:0 for wlan0
Jun  7 14:47:54 PC kernel: [ 3077.592562] ==> rtl8192cu_hal_deinit 
Jun  7 14:48:55 PC kernel: [ 3138.544384] rtl8192cu_hal_init in 544ms
Jun  7 14:48:56 PC kernel: [ 3139.869871] survey done event(7) band:0 for wlan0
Jun  7 14:48:57 PC kernel: [ 3140.584827] ==> rtl8192cu_hal_deinit 
Jun  7 14:49:58 PC kernel: [ 3201.548359] rtl8192cu_hal_init in 544ms
Jun  7 14:49:59 PC kernel: [ 3202.869847] survey done event(b) band:0 for wlan0
Jun  7 14:50:00 PC kernel: [ 3203.589134] ==> rtl8192cu_hal_deinit 
Jun  7 14:51:01 PC kernel: [ 3264.544410] rtl8192cu_hal_init in 544ms
Jun  7 14:51:02 PC kernel: [ 3265.869899] survey done event(b) band:0 for wlan0
Jun  7 14:51:03 PC kernel: [ 3266.584860] ==> rtl8192cu_hal_deinit 
Jun  7 14:52:04 PC kernel: [ 3327.564509] rtl8192cu_hal_init in 560ms
Jun  7 14:52:05 PC kernel: [ 3328.889874] survey done event(7) band:0 for wlan0
Jun  7 14:52:06 PC kernel: [ 3329.604855] ==> rtl8192cu_hal_deinit 
Jun  7 14:53:07 PC kernel: [ 3390.544538] rtl8192cu_hal_init in 544ms
Jun  7 14:53:08 PC kernel: [ 3391.869903] survey done event(7) band:0 for wlan0
Jun  7 14:53:09 PC kernel: [ 3392.584738] ==> rtl8192cu_hal_deinit 
Jun  7 14:54:10 PC kernel: [ 3453.548345] rtl8192cu_hal_init in 544ms
Jun  7 14:54:11 PC kernel: [ 3454.869964] survey done event(c) band:0 for wlan0
Jun  7 14:54:12 PC kernel: [ 3455.588796] ==> rtl8192cu_hal_deinit 
Jun  7 14:55:13 PC kernel: [ 3516.548431] rtl8192cu_hal_init in 548ms
Jun  7 14:55:14 PC kernel: [ 3517.873923] survey done event(d) band:0 for wlan0
Jun  7 14:55:15 PC kernel: [ 3518.588756] ==> rtl8192cu_hal_deinit 
Jun  7 14:56:16 PC kernel: [ 3579.552411] rtl8192cu_hal_init in 548ms
Jun  7 14:56:17 PC kernel: [ 3580.877902] survey done event(9) band:0 for wlan0
Jun  7 14:56:18 PC kernel: [ 3581.592739] ==> rtl8192cu_hal_deinit 
Jun  7 14:57:19 PC kernel: [ 3642.544411] rtl8192cu_hal_init in 544ms
Jun  7 14:57:20 PC kernel: [ 3643.869902] survey done event(5) band:0 for wlan0
Jun  7 14:57:21 PC kernel: [ 3644.584863] ==> rtl8192cu_hal_deinit 
Jun  7 14:58:22 PC kernel: [ 3705.548419] rtl8192cu_hal_init in 544ms
Jun  7 14:58:23 PC kernel: [ 3706.873913] survey done event(9) band:0 for wlan0
Jun  7 14:58:24 PC kernel: [ 3707.588680] ==> rtl8192cu_hal_deinit 
Jun  7 14:59:25 PC kernel: [ 3768.552437] rtl8192cu_hal_init in 548ms
Jun  7 14:59:26 PC kernel: [ 3769.877931] survey done event(a) band:0 for wlan0
Jun  7 14:59:27 PC kernel: [ 3770.592764] ==> rtl8192cu_hal_deinit 
Jun  7 15:00:28 PC kernel: [ 3831.548468] rtl8192cu_hal_init in 544ms
Jun  7 15:00:29 PC kernel: [ 3832.869838] survey done event(b) band:0 for wlan0
Jun  7 15:00:30 PC kernel: [ 3833.589106] ==> rtl8192cu_hal_deinit 
Jun  7 15:01:31 PC kernel: [ 3894.548377] rtl8192cu_hal_init in 548ms
Jun  7 15:01:32 PC kernel: [ 3895.873871] survey done event(8) band:0 for wlan0
Jun  7 15:01:33 PC kernel: [ 3896.588879] ==> rtl8192cu_hal_deinit 
Jun  7 15:02:34 PC kernel: [ 3957.548416] rtl8192cu_hal_init in 544ms
Jun  7 15:02:35 PC kernel: [ 3958.873911] survey done event(a) band:0 for wlan0
Jun  7 15:02:36 PC kernel: [ 3959.588668] ==> rtl8192cu_hal_deinit 
Jun  7 15:03:37 PC kernel: [ 4020.544334] rtl8192cu_hal_init in 544ms
Jun  7 15:03:38 PC kernel: [ 4021.865829] survey done event(9) band:0 for wlan0
Jun  7 15:03:39 PC kernel: [ 4022.584714] ==> rtl8192cu_hal_deinit 
Jun  7 15:04:40 PC kernel: [ 4083.544380] rtl8192cu_hal_init in 540ms
Jun  7 15:04:41 PC kernel: [ 4084.869873] survey done event(8) band:0 for wlan0
Jun  7 15:04:42 PC kernel: [ 4085.584832] ==> rtl8192cu_hal_deinit 
Jun  7 15:05:43 PC kernel: [ 4146.544803] rtl8192cu_hal_init in 544ms
Jun  7 15:05:44 PC kernel: [ 4147.869923] survey done event(b) band:0 for wlan0
Jun  7 15:05:45 PC kernel: [ 4148.585003] ==> rtl8192cu_hal_deinit 
Jun  7 15:06:46 PC kernel: [ 4209.548726] rtl8192cu_hal_init in 544ms
Jun  7 15:06:47 PC kernel: [ 4210.869847] survey done event(8) band:0 for wlan0
Jun  7 15:06:48 PC kernel: [ 4211.589129] ==> rtl8192cu_hal_deinit 
Jun  7 15:07:49 PC kernel: [ 4272.548529] rtl8192cu_hal_init in 548ms
Jun  7 15:07:50 PC kernel: [ 4273.873895] survey done event(9) band:0 for wlan0
Jun  7 15:07:51 PC kernel: [ 4274.588798] ==> rtl8192cu_hal_deinit 
Jun  7 15:08:52 PC kernel: [ 4335.552329] rtl8192cu_hal_init in 548ms
Jun  7 15:08:53 PC kernel: [ 4336.873823] survey done event(b) band:0 for wlan0
Jun  7 15:08:54 PC kernel: [ 4337.592710] ==> rtl8192cu_hal_deinit 
Jun  7 15:09:55 PC kernel: [ 4398.560382] rtl8192cu_hal_init in 560ms
Jun  7 15:09:56 PC kernel: [ 4399.885875] survey done event(9) band:0 for wlan0
Jun  7 15:09:57 PC kernel: [ 4400.601138] ==> rtl8192cu_hal_deinit 
Jun  7 15:10:58 PC kernel: [ 4461.548437] rtl8192cu_hal_init in 544ms
Jun  7 15:10:59 PC kernel: [ 4462.869807] survey done event(a) band:0 for wlan0
Jun  7 15:11:00 PC kernel: [ 4463.588862] ==> rtl8192cu_hal_deinit 
Jun  7 15:12:01 PC kernel: [ 4524.548365] rtl8192cu_hal_init in 548ms
Jun  7 15:12:02 PC kernel: [ 4525.873861] survey done event(7) band:0 for wlan0
Jun  7 15:12:03 PC kernel: [ 4526.588869] ==> rtl8192cu_hal_deinit 
Jun  7 15:13:04 PC kernel: [ 4587.548545] rtl8192cu_hal_init in 544ms
Jun  7 15:13:05 PC kernel: [ 4588.873912] survey done event(a) band:0 for wlan0
Jun  7 15:13:06 PC kernel: [ 4589.588674] ==> rtl8192cu_hal_deinit 
Jun  7 15:14:07 PC kernel: [ 4650.544477] rtl8192cu_hal_init in 544ms
Jun  7 15:14:08 PC kernel: [ 4651.869847] survey done event(c) band:0 for wlan0
Jun  7 15:14:09 PC kernel: [ 4652.584855] ==> rtl8192cu_hal_deinit 
Jun  7 15:15:10 PC kernel: [ 4713.552404] rtl8192cu_hal_init in 548ms
Jun  7 15:15:11 PC kernel: [ 4714.877898] survey done event(9) band:0 for wlan0
Jun  7 15:15:12 PC kernel: [ 4715.592658] ==> rtl8192cu_hal_deinit 
Jun  7 15:16:13 PC kernel: [ 4776.544336] rtl8192cu_hal_init in 540ms
Jun  7 15:16:14 PC kernel: [ 4777.865832] survey done event(d) band:0 for wlan0
Jun  7 15:16:15 PC kernel: [ 4778.584717] ==> rtl8192cu_hal_deinit 
Jun  7 15:17:16 PC kernel: [ 4839.548391] rtl8192cu_hal_init in 544ms
Jun  7 15:17:17 PC kernel: [ 4840.873886] survey done event(b) band:0 for wlan0
Jun  7 15:17:18 PC kernel: [ 4841.588855] ==> rtl8192cu_hal_deinit 
Jun  7 15:18:19 PC kernel: [ 4902.544448] rtl8192cu_hal_init in 544ms
Jun  7 15:18:20 PC kernel: [ 4903.865819] survey done event(c) band:0 for wlan0
Jun  7 15:18:21 PC kernel: [ 4904.584825] ==> rtl8192cu_hal_deinit 
Jun  7 15:19:22 PC kernel: [ 4965.548503] rtl8192cu_hal_init in 544ms
Jun  7 15:19:23 PC kernel: [ 4966.873872] survey done event(8) band:0 for wlan0
Jun  7 15:19:24 PC kernel: [ 4967.588882] ==> rtl8192cu_hal_deinit 
Jun  7 15:20:25 PC kernel: [ 5028.544436] rtl8192cu_hal_init in 544ms
Jun  7 15:20:26 PC kernel: [ 5029.869930] survey done event(c) band:0 for wlan0
Jun  7 15:20:27 PC kernel: [ 5030.584805] ==> rtl8192cu_hal_deinit 
Jun  7 15:21:28 PC kernel: [ 5091.552363] rtl8192cu_hal_init in 548ms
Jun  7 15:21:29 PC kernel: [ 5092.877857] survey done event(e) band:0 for wlan0
Jun  7 15:21:30 PC kernel: [ 5093.592949] ==> rtl8192cu_hal_deinit 
Jun  7 15:22:31 PC kernel: [ 5154.544546] rtl8192cu_hal_init in 544ms
Jun  7 15:22:32 PC kernel: [ 5155.869915] survey done event(b) band:0 for wlan0
Jun  7 15:22:33 PC kernel: [ 5156.584749] ==> rtl8192cu_hal_deinit 
Jun  7 15:23:34 PC kernel: [ 5217.552350] rtl8192cu_hal_init in 548ms
Jun  7 15:23:35 PC kernel: [ 5218.873846] survey done event(c) band:0 for wlan0
Jun  7 15:23:36 PC kernel: [ 5219.593113] ==> rtl8192cu_hal_deinit 
Jun  7 15:24:37 PC kernel: [ 5280.548532] rtl8192cu_hal_init in 548ms
Jun  7 15:24:38 PC kernel: [ 5281.873899] survey done event(9) band:0 for wlan0
Jun  7 15:24:39 PC kernel: [ 5282.588192] usb_read_port_complete()-1284: RX Warning! bDriverStopped(0) OR bSurpriseRemoved(0) bReadPortCancel(1)
Jun  7 15:24:39 PC kernel: [ 5282.588861] ==> rtl8192cu_hal_deinit 
Jun  7 15:25:40 PC kernel: [ 5343.564334] rtl8192cu_hal_init in 560ms
Jun  7 15:25:41 PC kernel: [ 5344.885828] survey done event(11) band:0 for wlan0
Jun  7 15:25:42 PC kernel: [ 5345.604719] ==> rtl8192cu_hal_deinit 
Jun  7 15:25:52 PC kernel: [ 5355.075856] rtl8192cu_hal_init in 0ms
Jun  7 15:25:52 PC avahi-daemon[656]: Withdrawing workstation service for wlan0.
Jun  7 15:25:52 PC kernel: [ 5355.096197] rtw_sta_flush(wlan0)
Jun  7 15:25:52 PC kernel: [ 5355.096353] rtw_cmd_thread(wlan0) stop_req:1, break
Jun  7 15:25:52 PC kernel: [ 5355.096694] =====> rtl8192c_free_hal_data =====
Jun  7 15:25:52 PC kernel: [ 5355.096699] <===== rtl8192c_free_hal_data =====
Jun  7 15:25:52 PC NetworkManager[806]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jun  7 15:25:52 PC NetworkManager[806]: <info> (wlan0): cleaning up...
Jun  7 15:25:52 PC NetworkManager[806]: <warn> (3) failed to find interface name for index
Jun  7 15:25:52 PC NetworkManager[806]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jun  7 15:25:52 PC NetworkManager[806]: <error> [1402147552.43031] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jun  7 15:25:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 15:25:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 15:25:52 PC NetworkManager[806]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  7 15:25:52 PC NetworkManager[806]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  7 15:25:52 PC NetworkManager[806]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jun  7 15:25:52 PC wpa_supplicant[875]: Could not read interface wlan0 flags: No such device
Jun  7 15:25:54 PC kernel: [ 5357.621801] usb 1-3: Product: 802.11n WLAN Adapter
Jun  7 15:25:54 PC kernel: [ 5357.622651] CHIP TYPE: RTL8188C_8192C
Jun  7 15:25:54 PC kernel: [ 5357.623781] ====> ReadAdapterInfo8192C
Jun  7 15:25:54 PC kernel: [ 5357.767292] readAdapterInfo_8192CU(): REPLACEMENT = 1
Jun  7 15:25:54 PC kernel: [ 5357.767295] <==== ReadAdapterInfo8192C in 144 ms
Jun  7 15:25:54 PC NetworkManager[806]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jun  7 15:25:54 PC NetworkManager[806]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  7 15:25:54 PC NetworkManager[806]: <warn> failed to allocate link cache: (-12) Object not found
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): driver supports SSID scans (scan_capa 0x3F).
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): using WEXT for WiFi device control
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 4)
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  7 15:25:54 PC NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  7 15:25:55 PC kernel: [ 5358.392559] rtl8192cu_hal_init in 588ms
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): preparing device.
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): taking down device.
Jun  7 15:25:55 PC kernel: [ 5358.405570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 15:25:55 PC kernel: [ 5358.406496] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 15:25:55 PC kernel: [ 5358.414225] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): bringing up device.
Jun  7 15:25:55 PC NetworkManager[806]: <info> NetworkManager state is now DISCONNECTED
Jun  7 15:25:55 PC kernel: [ 5358.417192] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  7 15:25:55 PC NetworkManager[806]: <warn> Trying to remove a non-existant call id.
Jun  7 15:25:55 PC wpa_supplicant[875]: wlan0: Reject scan trigger since one is already pending
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun  7 15:25:55 PC NetworkManager[806]: <info> (wlan0) supports 1 scan SSIDs
Jun  7 15:25:56 PC kernel: [ 5359.741923] survey done event(9) band:0 for wlan0
Jun  7 15:25:56 PC NetworkManager[806]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun  7 15:25:59 PC kernel: [ 5362.455556] ==> rtl8192cu_hal_deinit 
Jun  7 15:26:19 PC kernel: [ 5382.564531] rtl8192cu_hal_init in 560ms
Jun  7 15:26:20 PC kernel: [ 5383.889901] survey done event(f) band:0 for wlan0
Jun  7 15:26:21 PC kernel: [ 5384.604860] ==> rtl8192cu_hal_deinit 
Jun  7 15:26:52 PC kernel: [ 5415.564437] rtl8192cu_hal_init in 564ms
Jun  7 15:26:53 PC kernel: [ 5416.897944] survey done event(11) band:0 for wlan0
Jun  7 15:26:54 PC kernel: [ 5417.606448] ==> rtl8192cu_hal_deinit 
Jun  7 15:27:35 PC kernel: [ 5458.548560] rtl8192cu_hal_init in 544ms
Jun  7 15:27:36 PC kernel: [ 5459.869807] survey done event(d) band:0 for wlan0
Jun  7 15:27:37 PC kernel: [ 5460.588793] ==> rtl8192cu_hal_deinit 
Jun  7 15:28:28 PC kernel: [ 5511.544526] rtl8192cu_hal_init in 544ms
```

---

### Post by chili555 on 2014-06-07
Varun is going to take a few hours off; we require that he sleep, eat and bathe from time to time!! He has asked that I step in.

First, Network Manager will default to wired ethernet if it is available as it is generally faster and more secure. Once we make a few tweaks, we'll want to see the wireless script run with the ethernet detached.

Your device scans and sees networks, so we're most of the way done!> wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 UPC1083712>
                    ESSID:"UPC1083712"
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
                    Quality=100/100  Signal level=42/100  
          Cell 02 - Address: <MAC C-02 UPC WifiSpots>
                    ESSID:"UPC WifiSpots"
                    Protocol:IEEE 802.11bgn
<snip>I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close gedit.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Now, please reboot with the ethernet detached, try to connect and run the wireless script. Hook up the ethernet and post the script here.

---

### Post by Th3MadHatter on 2014-06-07
Ofcourse, we all need to get some rest every now and then right ;).
Thanks for stepping in.

Ok, first of all I did see a popup saying wireless networks are available but unfortunately they are nowhere to be found except when you manually scan (terminal) for it so it looks like the GUI gets "wlan blocked" lol

I readded a wireless network and set both wired and wireless ipv6's to ignore (which I usually do anyway because we're still on ipv4).

This is what the log coughed up with the wlan in my network manager, without a connection ofcourse.

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

PC 3.13.0-27-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory : 1746 MB
Uptime : 21:22:37 up 3 min,  2 users,  load average: 0,67, 0,61, 0,28


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:80f8]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0461:4d65 Primax Electronics, Ltd 
Bus 008 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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

8192cu                572859  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=1 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 eth0           | Wired       | e100      | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    LAPTOPOUD_Network: Infra, <MAC C-03 LAPTOPOUD_Network>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA
    VGV751900DE2B:   Infra, <MAC C-01 VGV751900DE2B>, Freq 2412 MHz, Rate 16 Mb/s, Strength 43 WPA WPA2
    UPC WifiSpots:   Infra, <MAC C-02 UPC WifiSpots>, Freq 2412 MHz, Rate 16 Mb/s, Strength 42 WPA2 Enterprise
    UPC1083712:      Infra, <MAC C-NA UPC1083712 1>, Freq 2412 MHz, Rate 16 Mb/s, Strength 42 WPA WPA2
    UPC033925:       Infra, <MAC C-04 UPC033925>, Freq 2437 MHz, Rate 16 Mb/s, Strength 23 WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Draadloze verbinding 1 : ssid=dd-wrt23 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "nl_NL.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 VGV751900DE2B>
                    ESSID:"VGV751900DE2B"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac020100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=92/100  Signal level=42/100  
          Cell 02 - Address: <MAC C-02 UPC WifiSpots>
                    ESSID:"UPC WifiSpots"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality=20/100  Signal level=42/100  
          Cell 03 - Address: <MAC C-03 LAPTOPOUD_Network>
                    ESSID:"LAPTOPOUD_Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=78/100  Signal level=42/100  
          Cell 04 - Address: <MAC C-04 UPC033925>
                    ESSID:"UPC033925"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=52/100  Signal level=26/100  
          Cell 05 - Address: <MAC C-05 >
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=42/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[8192cu]
filename:       /lib/modules/3.13.0-27-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     0178C5A913EE91E7925ADE1
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
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
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

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

BOOT_IMAGE=/vmlinuz-3.13.0-27-generic root=/dev/mapper/ubuntu--vg-root ro rootflags=sync quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    2.426966] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.427543] audit: initializing netlink socket (disabled)
[   15.674060] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   15.717738] rtl8192cu driver version=v4.0.2_9000.20130911
[   15.722138] register rtw_netdev_ops to netdev_ops
[   16.732965] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.811814] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[   22.984563] rtl8192cu_hal_init in 660ms
[   22.997829] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.999028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.017184] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[   23.019420] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.054022] ==> rtl8192cu_hal_deinit 
[   46.001544] ===> ips_netdrv_open.........
[   46.556473] rtl8192cu_hal_init in 556ms
[   48.597056] ==> rtl8192cu_hal_deinit 
[   79.003732] ===> ips_netdrv_open.........
[   79.548343] rtl8192cu_hal_init in 548ms
[   81.588801] ==> rtl8192cu_hal_deinit 
[  122.004673] ===> ips_netdrv_open.........
[  122.545553] rtl8192cu_hal_init in 540ms
[  122.573215] rtl8192c_set_FwJoinBssReport_cmd mstatus(0)
[  124.276615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  128.315381] ==> rtl8192cu_hal_deinit 
[  148.006785] ===> ips_netdrv_open.........
[  148.556849] rtl8192cu_hal_init in 552ms
[  150.596822] ==> rtl8192cu_hal_deinit 
[  181.003231] ===> ips_netdrv_open.........
[  181.552459] rtl8192cu_hal_init in 552ms
[  183.593160] ==> rtl8192cu_hal_deinit 
[  224.004420] ===> ips_netdrv_open.........
[  224.556786] rtl8192cu_hal_init in 552ms
[  226.596865] ==> rtl8192cu_hal_deinit 
[  232.999131] ===> ips_netdrv_open.........
[  233.540535] rtl8192cu_hal_init in 544ms

    ======== Done ========
```

Edit: Reading back the log myself I notice the country code being reset to 00 as in "anything goes" while my crda still says NL, figured I'd mention it because it was something I instantly noticed.
Another small edit: The connection I'm going for is in Cell 05.

---

### Post by chili555 on 2014-06-07
> Cell 05 - Address: <MAC C-05 >
                    ESSID:""
<snip>I doubt that a hidden SSID helps in any way. I suggest you un-hide it and use a name without any spaces; may I suggest something like 'varunrocks'?

I am assuming you compiled 8192cu and blacklisted the native **rtl**8192cu. Why?> Ok, first of all I did see a popup saying wireless networks are available but unfortunately they are nowhere to be found except when you manually scan (terminal) for it so it looks like the GUI gets "wlan blocked" lolMay I assume that you *DO* see the NM icon at the top right? And you see *no* networks when you click it?? Weird!

---

### Post by Th3MadHatter on 2014-06-07
Well, this hidden network is just for testing purposes, the comp isn't mine it's my friends so as soon as I'm able to connect to my network I'll delete it and add her network instead (which isn't hidden, just some ISP random router). I could un-hide it but, will it be useful? I doubt it if I can't find ANY network at all and have no option to "connect to a hidden network" (as in your pic which I will move on to now :P)  As for why i'm running the patched driver, it was the first thing Varun suggested to do so I gave it a shot (see quote)  > **varunendra said:**
> Welcome to the forums Th3MadHatter !  Please follow the instructions in this post to try a patched driver that should be one the adapter needs : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)  If it doesn't work even with that driver, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)  As for you picture, I run Lubuntu since this thing is seriously ancient but yes I see the network manager (on the right at the bottom for me since it's lubuntu) after applying the "manual auto start" fix, however, when I open it I only see the bottom 4 options shown in your pic. Enable Networking, Enable Wireless (both are checked), Connection info and Edit Connections. Which is extremely weird if you ask me since it does pick up on random chatter from routers if you manually scan through terminal (and obviously can see in the log), what I also noticed is that it looks like my wlan0 is listening to channel 1 both here: "  Mode:Managed  Frequency=2.412 GHz " and here ```
  wlan0     13 channels in total; available frequencies :           Channel 01 (2.412 GHz) - 13 (2.472 GHz)            Current Frequency=2.412 GHz (Channel 1)
```  Might just be me but my cell is on channel 8 :P either that has nothing to do with it and I'm just seeing things or that's just wrong hehe.

---

### Post by chili555 on 2014-06-07
> NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[COLOR="#FF0000"]no-auto-default=<MAC eth0>,[/COLOR]

[ifupdown]
managed=falseI assume this is because you plugged in details about your router in Network Manager. Let's try a change:```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```Use nano or leafpad or any other text editor if you don't have gedit. Change the file to:```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

**#**no-auto-default=<MAC eth0>,

[ifupdown]
managed=false

```In short, we are commenting out the extras temporarily. Proofread, save and close the text editor. Now do:```
sudo service network-manager restart
```Now do you see networks??

---

### Post by Th3MadHatter on 2014-06-07
Nope no dice, nothings showing up.

---

### Post by Th3MadHatter on 2014-06-09
Lemmi bump this one up because it's still not working. Can't see any networks if I rightclick the network manager, just the bottom four options as in the picture on post #16.

---

### Post by chili555 on 2014-06-09
Is the behavior changed at all with the ethernet disconnected? Does the card still scan?```
sudo iwlist wlan0 scan
```We don't need to see all the results; just tell us if it sees them or, if not, the error message.

---

### Post by Th3MadHatter on 2014-06-09
Yeah networks still show up if I scan.  Another really weird thing is that, right after booting, the gui loads, a popup showing "You're disconnected" shows up and right after that another popup which says something along the lines of "there are wireless networks available click blablabla to connect" yet there's nothing there.

---

### Post by chili555 on 2014-06-09
It is my understanding that, as long as /etc/NetworkManager/NetworkManager.conf says:```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
[COLOR="#FF0000"]managed=false[/COLOR]
```And as long as /etc/network/interfaces has no listing at all except:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```That then Network Manager should take off and run perfectly. Would you please recheck?

Are there *any* settings in Network Manager that you added to try to get a connection? Usually, they are not needed.> Another really weird thing is that, right after booting, the gui loads, a popup showing "You're disconnected" shows up and right after that another popup which says something along the lines of "there are wireless networks available click blablabla to connect"That's the expected behavior. It is then waiting for you to click on your network; for instance GBR1 in the example above. It then ought to ask for your WPA2 password and connect.

May we also see:```
ls /etc/NetworkManager/system-connections/
```

---

### Post by Th3MadHatter on 2014-06-09
Lol omg I'm so retarded. Seriously you have to add this to "did you try and unplug your modem?" list.  Right clicking network manager shows you nothing, just what I said it did, the last couple of options. So, I wanted to unplug my mouse and move it back to my other comp and accidently clicked the network with my left button and the dropdown menu showed up "D'oh" (>_

---

### Post by chili555 on 2014-06-09
> **Th3MadHatter said:**
> Lol omg I'm so retarded. Seriously you have to add this to "did you try and unplug your modem?" list.  Right clicking network manager shows you nothing, just what I said it did, the last couple of options. So, I wanted to unplug my mouse and move it back to my other comp and accidently clicked the network with my left button and the dropdown menu showed up "D'oh" (>_I am happy it's working by whatever means. So you are all set?

---

### Post by Th3MadHatter on 2014-06-09
Yeah it looks like its working, i'm having some troubles with the firewall, it pretty much doesn't load anything it did do on eth0 (like email doesn't work at all, browsing is eeexxttreemmeellyy slow) but it IS connected.

---

### Post by varunendra on 2014-06-11
I'm still not really "back", am almost certainly going to be too busy throughout this month to even check on the responses on threads I'm dealing with, but..> Yeah it looks like its working, i'm having some troubles with the firewall, it pretty much doesn't load anything it did do on eth0 (like email doesn't work at all, browsing is eeexxttreemmeellyy slow) but it IS connected.
..are you sure it is firewall? Does it work better with firewall disabled or removed from in-between? Just curious.

And how about marking this thread as [SOLVED] if the problem is indeed the firewall? Using "Thread Tools" link above the top post on the page. :)

**PS:** Thanks for taking care of this one Doc Chili ! I had given up even if I had more time. :)

---

### Post by Th3MadHatter on 2014-06-14
Sorry for the late reply, been kind of busy so I kinda forgot :P.  I haven't had to much time to fondle around with it but it does seem like ufw slows things down, even when properly forwarded. My normal wifi devices load pages with a load average of about 0.30, 0.46, 0.56  (picked a random site that's actually pretty slow so numbers should be better then this) but loading things with the firewall turned hits the time-out rate of both firefox and thunderbird (think firefox times out at, like, 60 seconds and thunderbird at 90? something like that) atleast 8/10 times, it seemed slightly less when I turned the firewall off, timed out about 5/10 times. But like I said, I haven't had the time to thoroughly test it yet. If I can't figure out what's causing it I'll be back ofcourse :P.  I'll mark this one as solved though because the initial problem IS solved, it does connect :).

---

