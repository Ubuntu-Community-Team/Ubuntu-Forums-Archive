---
title: "Help with wireless"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by normwerner on 2014-06-28
I have been relatively happy so far with my experience converting my old Windows XP laptop to Lunbuntu. While I am not an absolute novice to computing and PCs (I started on  Z-80 machines running CMP and DOS), I will admit to no experience save this one with UNIX in any variation. So far I have been successful downloadinfg and installing the latest version of Lubuntu. I downloaded it to a DVD on another Windows PC and installed off the DVD. That went great. I've been able to download and install apps that I want, such as LibreOffice, and tonight I installed Dropbox and can share files with my PCs, iPad and iPhone - all good things. 

Obviously I can get on the internet,but only with a hard-wired connection. I cannot seem to get my wireless network to work. The wifi hardware is working fine and  I can "see" it and can enter the SSID and password info, but can't seem to get it to connect. Any help would be appreciated, since getting WiFi to work so I can us this system in my office was a primary goal. The advice that I've seen on Google searches on this topic all seemed to lead to a bunch of command line stuff that I'm not sure that I'm up to yet. 

Since I am a newbie, perhaps I can get a first-post pass on not being technical enough with this request, so tell me what I need to tell you in order to get help. Thanks.

Norm

---

### Post by squakie on 2014-06-28
Post back the output of:

lspci | grep Network

and

lsmod

---

### Post by Bucky Ball on 2014-06-28
*Thread moved to **Networking & Wireless**.*

Welcome. Even though you're a newcomer you'll have better luck here. We'll be gentle. ;)

Also, post the output of:
```

sudo lshw -C network
```

---

### Post by normwerner on 2014-06-30
OK, here are trhe post bcks that both of you requested. I'm actually quite proud of the fact that I even figured out how to do this much.

Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  8 
hp_wmi                 13702  0 
hid_generic            12492  0 
sparse_keymap          13708  1 hp_wmi
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
snd_intel8x0           33110  1 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
joydev                 17101  0 
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
serio_raw              13230  0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
btusb                  27580  0 
ipw2200               136401  0 
i915                  705574  2 
snd_seq_midi           13132  0 
libipw                 33144  1 ipw2200
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             342263  22 bnep,btusb,rfcomm
snd_rawmidi            25135  1 snd_seq_midi
lib80211               14040  2 libipw,ipw2200
pcmcia                 51828  0 
cfg80211              409394  2 libipw,ipw2200
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                16864  0 
drm_kms_helper         47182  1 i915
yenta_socket           40201  0 
snd_timer              28584  2 snd_pcm,snd_seq
tifm_7xx1              13163  0 
drm                   244037  3 i915,drm_kms_helper
pcmcia_rsrc            18319  1 yenta_socket
tifm_core              15133  1 tifm_7xx1
snd                    60871  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_algo_bit           13197  1 i915
wmi                    18673  1 hp_wmi
tpm_infineon           17164  0 
video                  18903  1 i915
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
tg3                   152132  0 
sdhci_pci              18535  0 
psmouse                91033  0 
sdhci                  37779  1 sdhci_pci
ptp                    18445  1 tg3
pps_core               18799  1 ptp

 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:b5:6f:76
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5751m-v3.29a ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:15:00:1d:27:61
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:d0100000-d0100fff

---

### Post by normwerner on 2014-06-30
I beliefve that I started this string with an incorrect post. I said that I could see the wifi network, but couldn't sign on. That's not true. I can see tat it is there, but can't seem to get it to work. Wired works fine.

---

### Post by varunendra on 2014-06-30
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Have you tried rebooting without the ethernet cable plugged-in and then try the wireless? Network Manager may not attempt a wireless connection if it detects a wired connection.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by normwerner on 2014-06-30
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Ofwamilinux 3.13.0-30-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) M processor 2.00GHz
Memory : 1500 MB
Uptime : 09:57:21 up 34 min,  2 users,  load average: 0.24, 0.24, 0.18


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:12f5]
    Kernel driver in use: ipw2200
--
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:0944]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Bluetooth 1.2 Interface [Broadcom BCM2035]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ipw2200               136401  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
cfg80211              409394  2 libipw,ipw2200
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
ipw2200      (18): antenna=0 | associate=0 | auto_create=1 | bt_coexist=0 | burst_duration_CCK=0 | burst_duration_OFDM=0 | channel=0 | cmdlog=0 | debug=0 | disable=0 | hwcrypto=0 | led=1 | mode=0 | qos_burst_enable=0 | qos_enable=0 | qos_no_ack_mask=0 | roaming=1 | rtap_iface=0
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth1                       | 802.11 WiFi | ipw2200 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC eth1>

    nwerner-ofwaminet: Infra, <MAC C-02 nwerner-ofwaminet>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Milford:         Infra, <MAC C-01 Milford>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | tg3     | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Wi-Fi connection 1   : ssid=Ofwaminet | mac-address=<MAC eth1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
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
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.365/0.443/0.521/0.078 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.037/0.043/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

eth1      11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Current Channel=0 - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

eth1      Scan completed :
          Cell 01 - Address: <MAC C-01 Milford>
                    ESSID:"Milford"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 124ms ago
          Cell 02 - Address: <MAC C-02 nwerner-ofwaminet>
                    ESSID:"nwerner-ofwaminet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-31 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 20ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ipw2200]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
version:        1.2.2kmprq
srcversion:     6432FDB1497A8B2EC025CB2
depends:        cfg80211,libipw,lib80211
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[libipw]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ipw2x00/libipw.ko
version:        git-1.1.13
srcversion:     73DCC060143DEA6F7EDA255
depends:        cfg80211,lib80211

[lib80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=7ded87a9-098d-4471-824f-60514829ec3b ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.698967] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.699422] audit: initializing netlink socket (disabled)
[    1.595172] tg3 0000:10:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   16.874632] wmi: Mapper loaded
[   17.350522] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.350527] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.350779] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.409407] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   61.420907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

```

---

### Post by varunendra on 2014-06-30
The report shows you connected via Ethernet cable. Did you try rebooting without Ethernet connection like I advised in my previous post? Please try that if you didn't already.

But before that, please change the encryption in your router to pure WPA2 with AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP which should be avoided as long as possible. Reboot the router after saving the change, and try connecting without the cable connection.

If it fails again, please try encryption type WPA with TKIP (I extremely rarely advise this, but if I'm not mistaken, your wifi card is quite an old model, so may work better with WPA. But in no case WPA/WPA2 mixed mode please.

If both settings fail to get you connected, please change to pure WPA2 with AES as suggested first > try to connect and let it fail > generate a fresh report and post it here.

---

### Post by normwerner on 2014-06-30
I'll have to think about that, since I have 4 other devices (2 Windowas and 2 IOS) that connect to that router as it is currently configured without any isses. I don't want to create a lot of extra work for myself by perhaps screwing up those devices while trying to accomodate a shortcoming in Lubuntu. I was able to connect fine with this computer under XP. I will see if I can connect to my work wifi without changing things at home.

-Norm

---

### Post by normwerner on 2014-07-03
So I tried it today in my work office on a wifi network that s pure WAP2 and got nothing. I am perhaps not going through the wifi netowrk set up correctly.  I don't know what all is required inthe set up. I enter the network name and the security password for it and little else. Do I really need to enter all of the rest of that stuff? I never had to under Windows or IOS.

---

### Post by varunendra on 2014-07-04
> **normwerner said:**
> I enter the network name and the security password for it and little else.

Normally all you have to enter (when prompted) is the network security key when it detects a network and tries to connect. Other related settings are automatically detected and saved in a profile with the same name as the SSID of the network.

If you are manually saving the settings _before_ connecting to the desired network, may be that is where some error may be happening. For example, the only saved profile in your last report shows "SSID=ofwaminet", while the only Access Point with a similar name in the same report has the ESSID "nwerner-ofwaminet" - that is what should be the "SSID" in the profile if it is the same AP you were trying to connect to.

I suggest you delete any saved connection, let the Network Manager detect and try to connect to an available one and supply only the security key when it prompts for it. Less manual entry, less chance of errors.

---

