---
title: "Slower Wifi hostpot after upgrading to 18.04 tp-link wn881nd (rtl8192ee)"
date: 2018-05-16
forum: Networking &amp; Wireless
---

### Post by choutzi on 2018-05-16
I have a problem with my wifi card tp link wn881nd which I use as a wifi hostpot (with hostapd) on ubuntu 18.04.
I'm using the wifi signal to connect to an app (a java app) with a digital tablet. I was using this solution on ubuntu 14.04, it worked pretty well but I wanted to upgrade my system because 14.04 support is coming to an end.
Since this upgrade the download on my tablet is really low (i'm just sending .pdf files and it can take several minutes whereas it took 3 to 4 second on 14.04). I'm on a fresh install right now.

I can say that the problem is caused by the driver or chipset of my tp link wn881nd **v2** (Realtek chipset **rtl8192ee**) because when i use the older version of this wifi card tp link wn881nd **v1** (Atheros chipset **AR9287**) on ubuntu 18.04 it's working and it's working godly (it took less than a second no lagging). But I can't use the older version.

Do you have a solution to this problem? Or a suggestion of an other wireless adapter which is not using the Realtek chipset and at the same price of the wn881nd? Any suggestions much appreciated!
    
```
    ########## wireless info START ##########
    
    Report from: 16 May 2018 10:38 CEST +0200
    
    Booted last: 16 May 2018 00:00 CEST +0200
    
    Script from: 10 Jan 2018 20:04 UTC +0000
    
    ##### release ###########################
    
    Distributor ID:    Ubuntu
    Description:    Ubuntu 18.04 LTS
    Release:    18.04
    Codename:    bionic
    
    ##### kernel ############################
    
    Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
    
    Parameters: ro, net.ifnames=0, biosdevname=0, quiet, splash, vt.handoff=1
    
    ##### desktop ###########################
    
    Ubuntu
    
    ##### lspci #############################
    
    00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 31)
        Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
        Kernel driver in use: e1000e
    
    06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:8196]
        Kernel driver in use: rtl8192ee
    
    07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
        Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
        Kernel driver in use: r8169
    
    ##### lsusb #############################
    
    Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 003: ID 0461:4d81 Primax Electronics, Ltd Dell N889 Optical Mouse
    Bus 001 Device 002: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    
    ##### PCMCIA card info ##################
    
    ##### rfkill ############################
    
    0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
    
    ##### lsmod #############################
    
    eeepc_wmi              16384  0
    rtl8192ee             110592  0
    asus_wmi               28672  1 eeepc_wmi
    wmi_bmof               16384  0
    btcoexist             131072  1 rtl8192ee
    sparse_keymap          16384  1 asus_wmi
    intel_wmi_thunderbolt    16384  0
    rtl_pci                32768  1 rtl8192ee
    rtlwifi                77824  3 rtl8192ee,rtl_pci,btcoexist
    mac80211              778240  3 rtl8192ee,rtl_pci,rtlwifi
    cfg80211              622592  2 mac80211,rtlwifi
    mxm_wmi                16384  0
    wmi                    24576  4 asus_wmi,wmi_bmof,intel_wmi_thunderbolt,mxm_wmi
    video                  40960  1 asus_wmi
    
    ##### interfaces ########################
    
    [/etc/network/interfaces]
    auto lo
    iface lo inet loopback
    auto wlan0
    iface wlan0 inet static
        address 192.168.1.1
        network 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
    
    ##### ifconfig ##########################
    
    eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 192.168.0.171  netmask 255.255.255.0  broadcast 192.168.0.255
            inet6 fe80::8a20:2dd9:67d2:620e  prefixlen 64  scopeid 0x20<link>
            ether <MAC address>  txqueuelen 1000  (Ethernet)
            RX packets 81434  bytes 12965891 (12.9 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 11891  bytes 1741388 (1.7 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    eth1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            ether <MAC address>  txqueuelen 1000  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
            device interrupt 16  memory 0xdff00000-dff20000  
    
    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 28568  bytes 6460885 (6.4 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 28568  bytes 6460885 (6.4 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 192.168.1.1  netmask 255.255.255.0  broadcast 192.168.1.255
            inet6 fe80::523e:aaff:fe3e:2055  prefixlen 64  scopeid 0x20<link>
            ether <MAC address>  txqueuelen 1000  (Ethernet)
            RX packets 342  bytes 31545 (31.5 KB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 375  bytes 50169 (50.1 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    ##### iwconfig ##########################
    
    eth1      no wireless extensions.
    
    lo        no wireless extensions.
    
    eth0      no wireless extensions.
    
    wlan0     IEEE 802.11  Mode:Master  Tx-Power=20 dBm   
              Retry short limit:7   RTS thr=2347 B   Fragment thr:off
              Power Management:on
              
    
    ##### route #############################
    
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         192.168.0.254   0.0.0.0         UG    100    0        0 eth0
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
    192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
    192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
    
    ##### resolv.conf #######################
    
    nameserver 127.0.0.53
    search lan
    
    ##### network managers ##################
    
    Installed:
    
        NetworkManager
    
    Running:
    
    root       886     1  0 09:42 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
    
    ##### NetworkManager info ###############
    
    GENERAL.DEVICE:                         eth0
    GENERAL.TYPE:                           ethernet
    GENERAL.NM-TYPE:                        NMDeviceEthernet
    GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
    GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    GENERAL.DRIVER:                         r8169
    GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
    GENERAL.FIRMWARE-VERSION:               --
    GENERAL.HWADDR:                         <MAC address>
    GENERAL.MTU:                            1500
    GENERAL.STATE:                          100 (connected)
    GENERAL.REASON:                         0 (No reason given)
    GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:07:00.0/net/eth0
    GENERAL.IP-IFACE:                       eth0
    GENERAL.IS-SOFTWARE:                    no
    GENERAL.NM-MANAGED:                     yes
    GENERAL.AUTOCONNECT:                    yes
    GENERAL.FIRMWARE-MISSING:               no
    GENERAL.NM-PLUGIN-MISSING:              no
    GENERAL.PHYS-PORT-ID:                   --
    GENERAL.CONNECTION:                     Connexion filaire 1
    GENERAL.CON-UUID:                       5c60eaea-372d-3bbb-959c-d0a9310f5e41
    GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
    GENERAL.METERED:                        no (guessed)
    CAPABILITIES.CARRIER-DETECT:            yes
    CAPABILITIES.SPEED:                     1000 Mb/s
    CAPABILITIES.IS-SOFTWARE:               no
    CAPABILITIES.SRIOV:                     no
    WIRED-PROPERTIES.CARRIER:               on
    IP4.ADDRESS[1]:                         192.168.0.171/24
    IP4.GATEWAY:                            192.168.0.254
    IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.254, mt = 100
    IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
    IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
    IP4.DNS[1]:                             192.168.0.4
    IP4.DOMAIN[1]:                          lan
    IP4.WINS[1]:                            192.168.0.4
    DHCP4.OPTION[1]:                        requested_domain_search = 1
    DHCP4.OPTION[2]:                        broadcast_address = 192.168.0.255
    DHCP4.OPTION[3]:                        requested_time_offset = 1
    DHCP4.OPTION[4]:                        requested_broadcast_address = 1
    DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
    DHCP4.OPTION[6]:                        routers = 192.168.0.254
    DHCP4.OPTION[7]:                        requested_domain_name = 1
    DHCP4.OPTION[8]:                        requested_netbios_scope = 1
    DHCP4.OPTION[9]:                        expiry = 1526499737
    DHCP4.OPTION[10]:                       next_server = 0.0.0.0
    DHCP4.OPTION[11]:                       requested_ntp_servers = 1
    DHCP4.OPTION[12]:                       dhcp_message_type = 5
    DHCP4.OPTION[13]:                       requested_interface_mtu = 1
    DHCP4.OPTION[14]:                       requested_wpad = 1
    DHCP4.OPTION[15]:                       ip_address = 192.168.0.171
    DHCP4.OPTION[16]:                       requested_subnet_mask = 1
    DHCP4.OPTION[17]:                       requested_static_routes = 1
    DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
    DHCP4.OPTION[19]:                       dhcp_lease_time = 43200
    DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
    DHCP4.OPTION[21]:                       domain_name = lan
    DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.4
    DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
    DHCP4.OPTION[24]:                       wpad = a
    DHCP4.OPTION[25]:                       requested_routers = 1
    DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
    DHCP4.OPTION[27]:                       netbios_name_servers = 192.168.0.4
    DHCP4.OPTION[28]:                       network_number = 192.168.0.0
    DHCP4.OPTION[29]:                       requested_host_name = 1
    DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.4
    IP6.ADDRESS[1]:                         fe80::8a20:2dd9:67d2:620e/64
    IP6.GATEWAY:                            --
    IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
    IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
    IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
    CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
    CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5c60eaea-372d-3bbb-959c-d0a9310f5e41 | Connexion filaire 1
    
    GENERAL.DEVICE:                         eth1
    GENERAL.TYPE:                           ethernet
    GENERAL.NM-TYPE:                        NMDeviceEthernet
    GENERAL.VENDOR:                         Intel Corporation
    GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
    GENERAL.DRIVER:                         e1000e
    GENERAL.DRIVER-VERSION:                 3.2.6-k
    GENERAL.FIRMWARE-VERSION:               0.7-4
    GENERAL.HWADDR:                         <MAC address>
    GENERAL.MTU:                            1500
    GENERAL.STATE:                          20 (unavailable)
    GENERAL.REASON:                         2 (Device is now managed)
    GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/eth1
    GENERAL.IP-IFACE:                       --
    GENERAL.IS-SOFTWARE:                    no
    GENERAL.NM-MANAGED:                     yes
    GENERAL.AUTOCONNECT:                    yes
    GENERAL.FIRMWARE-MISSING:               no
    GENERAL.NM-PLUGIN-MISSING:              no
    GENERAL.PHYS-PORT-ID:                   --
    GENERAL.CONNECTION:                     --
    GENERAL.CON-UUID:                       --
    GENERAL.CON-PATH:                       --
    GENERAL.METERED:                        unknown
    CAPABILITIES.CARRIER-DETECT:            yes
    CAPABILITIES.SPEED:                     unknown
    CAPABILITIES.IS-SOFTWARE:               no
    CAPABILITIES.SRIOV:                     no
    WIRED-PROPERTIES.CARRIER:               off
    CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
    
    GENERAL.DEVICE:                         wlan0
    GENERAL.TYPE:                           wifi
    GENERAL.NM-TYPE:                        NMDeviceWifi
    GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
    GENERAL.PRODUCT:                        RTL8192EE PCIe Wireless Network Adapter
    GENERAL.DRIVER:                         rtl8192ee
    GENERAL.DRIVER-VERSION:                 4.15.0-20-generic
    GENERAL.FIRMWARE-VERSION:               N/A
    GENERAL.HWADDR:                         <MAC address>
    GENERAL.MTU:                            1500
    GENERAL.STATE:                          10 (unmanaged)
    GENERAL.REASON:                         0 (No reason given)
    GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0/net/wlan0
    GENERAL.IP-IFACE:                       wlan0
    GENERAL.IS-SOFTWARE:                    no
    GENERAL.NM-MANAGED:                     no
    GENERAL.AUTOCONNECT:                    yes
    GENERAL.FIRMWARE-MISSING:               no
    GENERAL.NM-PLUGIN-MISSING:              no
    GENERAL.PHYS-PORT-ID:                   --
    GENERAL.CONNECTION:                     --
    GENERAL.CON-UUID:                       --
    GENERAL.CON-PATH:                       --
    GENERAL.METERED:                        unknown
    CAPABILITIES.CARRIER-DETECT:            no
    CAPABILITIES.SPEED:                     unknown
    CAPABILITIES.IS-SOFTWARE:               no
    CAPABILITIES.SRIOV:                     no
    WIFI-PROPERTIES.WEP:                    yes
    WIFI-PROPERTIES.WPA:                    yes
    WIFI-PROPERTIES.WPA2:                   yes
    WIFI-PROPERTIES.TKIP:                   yes
    WIFI-PROPERTIES.CCMP:                   yes
    WIFI-PROPERTIES.AP:                     yes
    WIFI-PROPERTIES.ADHOC:                  yes
    WIFI-PROPERTIES.2GHZ:                   yes
    WIFI-PROPERTIES.5GHZ:                   no
    IP4.ADDRESS[1]:                         192.168.1.1/24
    IP4.GATEWAY:                            --
    IP4.ROUTE[1]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 0
    IP6.ADDRESS[1]:                         fe80::523e:aaff:fe3e:2055/64
    IP6.GATEWAY:                            --
    IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
    IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
    CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
    
    SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
    
    ##### NetworkManager.state ##############
    
    [main]
    NetworkingEnabled=true
    WirelessEnabled=true
    WWANEnabled=true
    
    ##### NetworkManager.conf ###############
    
    [main]
    plugins=ifupdown,keyfile
    
    [ifupdown]
    managed=false
    
    [device]
    wifi.scan-rand-mac-address=no
    
    ##### NetworkManager profiles ###########
    
    ##### Netplan config ####################
    
    [/etc/netplan/01-network-manager-all.yaml]
    network:
      version: 2
      renderer: NetworkManager
    
    ##### iw reg get ########################
    
    Region: Europe/Paris (based on set time zone)
    
    global
    country FR: DFS-ETSI
        (2402 - 2482 @ 40), (N/A, 20), (N/A)
        (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
        (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
        (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
        (57000 - 66000 @ 2160), (N/A, 40), (N/A)
    
    ##### iwlist channels ###################
    
    eth1      no frequency information.
    
    lo        no frequency information.
    
    eth0      no frequency information.
    
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
    
    ##### iwlist scan #######################
    
    eth1      Interface doesn't support scanning.
    
    wlan0     Interface doesn't support scanning : Operation not supported
    
    lo        Interface doesn't support scanning.
    
    eth0      Interface doesn't support scanning.
    
    ##### module infos ######################
    
    [rtl8192ee]
    filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192ee/rtl8192ee.ko
    firmware:       rtlwifi/rtl8192eefw.bin
    description:    Realtek 8192EE 802.11n PCI wireless
    license:        GPL
    author:         Larry Finger    <Larry.Finger@lwfinger.net>
    author:         Realtek WlanFAE    <wlanfae@realtek.com>
    srcversion:     FB988A61D42E8DCCD613E97
    depends:        rtlwifi,rtl_pci,btcoexist,mac80211
    retpoline:      Y
    intree:         Y
    name:           rtl8192ee
    vermagic:       4.15.0-20-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           swenc:Set to 1 for software crypto (default 0)
     (bool)
    parm:           ips:Set to 0 to not use link power save (default 1)
     (bool)
    parm:           swlps:Set to 1 to use SW control power save (default 0)
     (bool)
    parm:           fwlps:Set to 1 to use FW control power save (default 1)
     (bool)
    parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
     (bool)
    parm:           dma64:Set to 1 to use DMA 64 (default 0)
     (bool)
    parm:           aspm:Set to 1 to enable ASPM (default 1)
     (int)
    parm:           debug_level:Set debug level (0-5) (default 0) (int)
    parm:           debug_mask:Set debug mask (default 0) (ullong)
    parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
     (bool)
    
    [rtl_pci]
    filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
    description:    PCI basic driver for rtlwifi
    license:        GPL
    author:         Larry Finger    <Larry.FInger@lwfinger.net>
    author:         Realtek WlanFAE    <wlanfae@realtek.com>
    author:         lizhaoming    <chaoming_li@realsil.com.cn>
    srcversion:     9F5FA8A771710F4CA500C6E
    depends:        mac80211,rtlwifi
    retpoline:      Y
    intree:         Y
    name:           rtl_pci
    vermagic:       4.15.0-20-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    
    [rtlwifi]
    filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
    description:    Realtek 802.11n PCI wireless core
    license:        GPL
    author:         Larry Finger    <Larry.FInger@lwfinger.net>
    author:         Realtek WlanFAE    <wlanfae@realtek.com>
    author:         lizhaoming    <chaoming_li@realsil.com.cn>
    srcversion:     8AB8B2AAF3BCFFB93D91956
    depends:        mac80211,cfg80211
    retpoline:      Y
    intree:         Y
    name:           rtlwifi
    vermagic:       4.15.0-20-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    
    [mac80211]
    filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
    license:        GPL
    description:    IEEE 802.11 subsystem
    srcversion:     1CEA5CF286EDB289C1D0BF8
    depends:        cfg80211
    retpoline:      Y
    intree:         Y
    name:           mac80211
    vermagic:       4.15.0-20-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
    parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
    parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
    parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
    parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
    parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
    
    [cfg80211]
    filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
    description:    wireless configuration support
    license:        GPL
    author:         Johannes Berg
    srcversion:     D5B0789D4C423C81CCFB437
    depends:        
    retpoline:      Y
    intree:         Y
    name:           cfg80211
    vermagic:       4.15.0-20-generic SMP mod_unload 
    signat:         PKCS#7
    signer:         
    sig_key:        
    sig_hashalgo:   md4
    parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
    parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
    parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
    
    ##### module parameters #################
    
    [rtl8192ee]
    aspm: 1
    debug_level: 0
    debug_mask: 0
    disable_watchdog: N
    dma64: N
    fwlps: Y
    ips: Y
    msi: Y
    swenc: N
    swlps: N
    
    [mac80211]
    beacon_loss_count: 7
    ieee80211_default_rc_algo: minstrel_ht
    max_nullfunc_tries: 2
    max_probe_tries: 5
    minstrel_vht_only: Y
    probe_wait_ms: 500
    
    [cfg80211]
    bss_entries_limit: 1000
    cfg80211_disable_40mhz_24ghz: N
    ieee80211_regdom: 00
    
    ##### /etc/modules ######################
    
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
    
    ##### rc.local ##########################
    
    grep: /etc/rc.local: No such file or directory
    
    ##### pm-utils ##########################
    
    ##### udev rules ########################
    
    ##### dmesg #############################
    
    [    8.462174] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
    [    8.639148] rtl8192ee: Using firmware rtlwifi/rtl8192eefw.bin
    [    8.649364] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
    [    8.649507] rtlwifi: rtlwifi: wireless switch is on
    [   11.290858] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
    [   12.084668] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   12.102872] r8169 0000:07:00.0 eth0: link down (repeated 2 times)
    [   12.102955] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
    [   12.106459] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
    [   12.308596] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
    [   15.231676] r8169 0000:07:00.0 eth0: link up
    [   15.231682] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
    [   35.044119] rtlwifi: -----hwsec_cam_bitmap: 0x0 entry_idx=4
    
    ########## wireless info END ############
```

---

