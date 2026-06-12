---
title: "Ubuntu 12.04: Connected to Wi-Fi, no internet access"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by W@@dy on 2014-04-19
Haven't had this issue before, so you'll have to walk me through how/what information you need to troubleshoot.

It's a desktop with a linksys PCI wireless adapter plugged in. Connects to the network fine on boot, and the network works fine for all other computers (posting from my laptop on this network right now.)

The desktop is assigned a local IP and it's default gateway is correct, however I can't even ping the router let alone something outside my house. Everything simply times out.

I've searched and tried a few fixes dealing with iwlwifi.config, but those haven't had an effect.

Interestingly, I'm rather sure the internet worked fine for the first few days of the install (a few weeks ago). The only thing I can associate with the cause of failure is my router was factory reset. I've changed the router settings back to as they were, deleted, cleared, and re-established the proper settings on this desktop to connect with the router (and indeed it connects now), but since then it no longer can access anything.

---

### Post by PapaNerd on 2014-04-19
Please post the output of the ```
ifconfig -a
``` command on both the working and non-working machines ... or ```
ipconfig /all
``` if any are running Windoze.

---

### Post by varunendra on 2014-04-19
..and for a more detailed info, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by W@@dy on 2014-04-19
From working OSX machine

```
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384    options=3<RXCSUM,TXCSUM>
    inet6 ::1 prefixlen 128
    inet 127.0.0.1 netmask 0xff000000
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1
    nd6 options=1<PERFORMNUD>
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether b8:8d:12:1a:0e:94
    inet6 fe80::ba8d:12ff:fe1a:e94%en0 prefixlen 64 scopeid 0x4
    inet 192.168.8.104 netmask 0xffffff00 broadcast 192.168.8.255
    nd6 options=1<PERFORMNUD>
    media: autoselect
    status: active
en2: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
    options=60<TSO4,TSO6>
    ether b2:00:1b:e8:bb:00
    media: autoselect <full-duplex>
    status: inactive
bridge0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    options=63<RXCSUM,TXCSUM,TSO4,TSO6>
    ether ba:8d:12:a1:74:00
    Configuration:
        id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
        maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
        root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
        ipfilter disabled flags 0x2
    member: en2 flags=3<LEARNING,DISCOVER>
            ifmaxaddr 0 port 5 priority 0 path cost 0
    nd6 options=1<PERFORMNUD>
    media: <unknown type>
    status: inactive
p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
    ether 0a:8d:12:1a:0e:94
    media: autoselect
    status: inactive
```

From non-working Ubuntu 12.04 machine
```

etho   Link encap:Ethernet  HWaddr 00:26:18:f1:53:d1
         UP BROADCAST MULTICAST  MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0B)   TX bytes:0 (0.0KB)

lo      Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         inet addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:65536 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:17864 (17.8KB)   TX bytes:17864 (17.8KB)

wlan0 Link encap:Ethernet HWaddr 08:10:76:a3:f1:03
         inet addr:192.168.8.102  Bcast:192.168.8.255  Mask:255.255.255.0
         ient6 addr: fe80::a10:76ff:fea3:f103/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:169 errors:0 dropped:0 overruns:0 frame:0
         TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:27421 (27.4KB)   TX bytes:94446 (94.4KB)

```

---

### Post by W@@dy on 2014-04-19
Here's the output from that script. This should be a good jump start on things...

```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise


##### kernel #####


Linux Clark-Tower 3.11.0-19-generic #33~precise1-Ubuntu SMP Wed Mar 12 21:16:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169


04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8178]
	Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0781:5576 SanDisk Corp. 
Bus 002 Device 003: ID 046d:c245 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"Clark"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.8.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.0.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Clark] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Clark:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    jrocka:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84


  IPv4 Settings:
    Address:         192.168.8.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.8.1


    DNS:             68.237.161.12
    DNS:             71.250.0.12


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"Clark"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008fbcc5853a
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0005436C61726B
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"jrocka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000019d48181
                    Extra: Last beacon: 2148ms ago
                    IE: Unknown: 00066A726F636B61
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0600032F010001
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"10FX10012850"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005adf36029f1
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000C313046583130303132383530
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000


##### iwlist channel #####


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


##### lsmod #####


rtl8192ce              58603  0 
rtl8192c_common        58573  1 rtl8192ce
rtl_pci                27261  1 rtl8192ce
rtlwifi                64035  2 rtl8192ce,rtl_pci
mac80211              623607  3 rtl8192ce,rtl_pci,rtlwifi
cfg80211              499466  2 rtlwifi,mac80211


##### modinfo #####


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D6221EBE7F9AFB5C639D02D
depends:        
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7492FC488AD8A6D43075535
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9985D829F92712EC7AE7D4E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 


##### modules #####


lp
rtc


##### blacklist #####


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


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.7/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    7.130903] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    7.738344] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    7.738510] rtlwifi: wireless switch is on
[   12.220550] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.220793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.450589] wlan0: authenticate with <MAC address removed>
[   15.470263] wlan0: send auth to <MAC address removed> (try 1/3)
[   15.473845] wlan0: authenticated
[   15.474066] rtl8192ce 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   15.478235] wlan0: associate with <MAC address removed> (try 1/3)
[   15.480501] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   15.480666] wlan0: associated
[   15.480673] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.578270] Modules linked in: bnep rfcomm bluetooth vesafb parport_pc ppdev xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp fglrx(POF) xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_state arc4 ip6table_filter ip6_tables snd_hda_codec_hdmi snd_hda_codec_via nf_conntrack_netbios_ns rtl8192ce nf_conntrack_broadcast snd_hda_intel nf_nat_ftp rtl8192c_common nf_nat snd_hda_codec nf_conntrack_ftp nf_conntrack rtl_pci rtlwifi snd_hwdep iptable_filter snd_pcm ip_tables x_tables mac80211 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq joydev snd_timer hid_logitech_dj snd_seq_device cfg80211 psmouse snd gpio_ich soundcore amd_iommu_v2 serio_raw i7core_edac snd_page_alloc mac_hid edac_core mxm_wmi wmi asus_atk0110 lpc_ich lp parport pata_acpi hid_generic usbhid hid firewire_ohci firewire_core crc_itu_t r8169 ahci libahci mii pata_jmicron


########## wireless info END ############



```

---

### Post by varunendra on 2014-04-19
Please change the encryption algorithm in the router to AES (CCMP), currently it is set to 'TKIP' which should be avoided. The encryption type is already good (pure WPA2). Keep the encryption to WPA2 with AES even if it doesn't seem to help. Reboot the router after saving the change.

If that alone doesn't seem to help, please try some driver parameters in Ubuntu as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)
As mentioned in the linked post, the changes would be permanent and if any of them seems to help, we can make it permanent.

Frankly, I doubt if any of the above is going to improve things significantly, so we may need to compile a newer driver for your card. But that would be a solution that you'd need to redo every time a kernel upgrade occurs, while the above ones need to be done only once. So we always try the easier solutions first.

Please report back how it goes, and we may take further steps as and if required.

---

### Post by W@@dy on 2014-04-19
Whew, dodged a bullet. Changing it to AES encryption (and deleting the saved connection info again) fixed it. Thanks for the help all.

Can anyone explain to me the difference between AES and TKIP for future reference?

---

### Post by PapaNerd on 2014-04-19
Good catch Varun.

W@@dy:  Check out these pages for more info:
[http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)
[http://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](http://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)

---

### Post by varunendra on 2014-04-19
Thanks PapaNerd. :)

I wouldn't start cheering and celebrating so soon though. I have seen things going crazy again after initial success, particularly with Realtek drivers. So I'll consider it solve only if it performs consistently for a full day or two. If the fix proves to be stable and permanent, please mark the thread as [SOLVED] using the "Thread Tools" link above the top post.

As for this -
> Can anyone explain to me the difference between AES and TKIP for future reference?
..here are a couple of posts that you may find interesting -

Why no TKIP : [http://ubuntuforums.org/showthread.php?p=12817495](http://ubuntuforums.org/showthread.php?p=12817495)
WPA2 vs WPA/WPA2 mixed mode : [http://ubuntuforums.org/showpost.php?p=12817442](http://ubuntuforums.org/showpost.php?p=12817442)

And of course the links posted by PapaNerd above are quite informative (and much more authentic) too.

---

### Post by W@@dy on 2014-04-20
Thanks for all the advice, wireless has been stable all night and was able to get about 3 weeks of updates installed.

---

