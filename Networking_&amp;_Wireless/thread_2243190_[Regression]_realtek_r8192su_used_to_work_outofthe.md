---
title: "[Regression] realtek r8192su used to work outofthebox"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by s-verbeeck2 on 2014-09-07
Hello everyone, I have another realtek wifi chip to throw on the list of failures of this manufacturer. The big deal is that said chip used to work just fine on any distro from 1.5 year ago. 
See, I didn't use linux for about a year and after trying some distros again my wifi fails whereas it used to be fine. Yes, I tried slackware, arch, fedora and debian based ones to get stuck at this point. I was thinking of reporting a linux kernel bug, but the kernel itself doesn't seem to be the issue. I have tried using some older kernels on my ubuntu 14.04 install going way back to the 3.9.0. None of this worked.
The actual problem is (like so many others) an extremely slow wifi connection, while signal strength is high. Internet access works but feels like a broken dial-up (things like refreshing packages runs at 300 b/s as an example).
I tried every realtek/wifi related fix on the ubuntu forums, but these always come down to installing another driver and I never found one that was also suitable for mine. That's why I decided to post a new topic because the **r8192su** hasn't been mentioned before.
However, ndiswrapper works perfectly with this chip. I am still posting this for good measure (thing worked - update - borked) and because ndiswrapper is a rather exotic thing that isn't available in many distributions. You can see it in the script output but I am sure it isn't interfering with the current driver as I unloaded my windows driver and rebooted before running the script. It did however forced me to use a 32 bit installation as ndis fails on 64 bit, but that's off-topic.
Anyway, I am suspecting that it might be some default configuration that breaks it because the kernel didn't make a difference, and looking at the changelog of linux-firmware there hasn't been a change to the r8192su for a long time. 

This is the output of the wifi script:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

stefan-MS-7788 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU G2020 @ 2.90GHz
Memory : 3734 MB
Uptime : 10:07:19 up 2 min,  2 users,  load average: 0,37, 0,15, 0,05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 0718:0639 Imation Corp. 
Bus 002 Device 003: ID 25c4:0002  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. JM20339 SATA Bridge
Bus 001 Device 008: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 007: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 006: ID 0fce:6166 Sony Ericsson Mobile Communications AB Xperia Mini Pro
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**Bus 001 Device 003: ID 06f8:e032 Guillemot Corp. HWGUm-54 [Hercules Wireless G Ultra Mini Key]**
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"bbox2-d701"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 bbox2-d701>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=90/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

r8712u                158706  0 
ndiswrapper           192915  0 
wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

ndiswrapper   (6): 
r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o========o===========o=========o===========o==============o===========
 Interface & ID      | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
=====================o=============o========o===========o=========o===========o==============o===========
 wlan0  [bbox2-d701] | 802.11 WiFi | r8712u | connected | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *bbox2-d701:     Infra, <MAC C-01 bbox2-d701>, Freq 2462 MHz, Rate 54 Mb/s, Strength 97

    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
---------------------+-------------+--------+-----------+---------+-----------+--------------+-----------


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

bbox2-d701           : ssid=bbox2-d701 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.437/2.013/2.590/0.578 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.019/0.024/0.030/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : nl_BE.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 bbox2-d701>
                    ESSID:"bbox2-d701"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=100/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8192cu


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[r8712u]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

[ndiswrapper]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/ndiswrapper.ko
version:        1.59
srcversion:     C101C962263FFF26465A483
depends:        
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# USB device 0x:0x (r8712u)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=41e1b3ca-6385-429e-bde2-1a5d9b95bc56 ro quiet splash rootfstype=ext4 vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.442697] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.442930] audit: initializing netlink socket (disabled)
[    1.793389] wmi: Mapper loaded
[    1.883998] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[    1.884760] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[    2.759257] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.001135] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   28.001717] r8712u: Staging version
[   28.001729] r8712u: register rtl8712_netdev_ops to netdev_ops
[   28.001733] usb 1-1.1: r8712u: USB_SPEED_HIGH with 4 endpoints
[   28.002300] usb 1-1.1: r8712u: Boot from EFUSE: Autoload OK
[   28.674368] usb 1-1.1: r8712u: CustomerID = 0x0000
[   28.674374] usb 1-1.1: r8712u: MAC Address from efuse = <MAC wlan0>
[   28.674377] usb 1-1.1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   29.408638] r8712u 1-1.1:1.0 wlan0: 1 RCR=0x153f00e
[   29.409382] r8712u 1-1.1:1.0 wlan0: 2 RCR=0x553f00e
[   29.516558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.516775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.824514] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.224115] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by praseodym on 2014-09-07
In this case you can blacklist the not-working one:
```

echo "blacklist r8712u" | sudo tee /etc/modprobe.d/blacklist-r8712u.conf
```

---

### Post by s-verbeeck2 on 2014-09-07
Thanks, but I knew that command already. I must use this otherwise both ndiswrapper and r8712u get loaded for the chip, which leads to an instant kernel panic (as expected)

---

