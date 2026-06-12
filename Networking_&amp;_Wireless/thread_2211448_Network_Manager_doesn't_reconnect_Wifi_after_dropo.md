---
title: "Network Manager doesn't reconnect Wifi after dropout"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by kamm747 on 2014-03-16
Hi folks,

I'm running an Asus 1201n netbook with Lubuntu 13.10.

All's good except after a Wifi dropout, when Network Manager doesn't automatically reconnect. I can get it to reconnect by closing the lid and reopening or by disabling and then enabling Wifi from the Network Manager GUI.

In Network Manager > General > "Automatically connect to this network when it is avaialable" is connected.

```

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

```

```

~$ uname -r -m
3.11.0-18-generic x86_64

```


```

$ cat  /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```


```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:5d:cc:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1166607 (1.1 MB)  TX bytes:1166607 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:6f:4e:df  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe6f:4edf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 


```


```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:5d:cc:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1166607 (1.1 MB)  TX bytes:1166607 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:6f:4e:df  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe6f:4edf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83608101 (83.6 MB)  TX bytes:14557959 (14.5 MB)

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_PC_NETWORK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:5D:4C:AE:5E:C6   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0


```


```

$ lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: NVIDIA Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: NVIDIA Corporation ION VGA [GeForce 9400M] (rev b1)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
09:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)


```


```

$ lsmod
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
dm_crypt               22832  1 
zram                   18525  4 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  12 
snd_hda_codec_hdmi     41154  1 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
coretemp               13435  0 
sparse_keymap          13948  1 asus_wmi
snd_hda_codec_realtek    56475  1 
joydev                 17377  0 
arc4                   12608  2 
uvcvideo               80885  0 
rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
snd_hda_intel          52267  1 
rtlwifi                63229  2 rtl_pci,rtl8192se
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
videodev              133509  2 uvcvideo,videobuf2_core
cfg80211              480503  2 mac80211,rtlwifi
btusb                  28267  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
bluetooth             372041  22 bnep,btusb,rfcomm
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97655  0 
snd_rawmidi            30095  1 snd_seq_midi
microcode              23656  0 
serio_raw              13413  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
shpchp                 37032  0 
snd                    69141  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_nforce2            13221  0 
soundcore              12680  1 snd
mac_hid                13205  0 
binfmt_misc            17468  1 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
nouveau               943749  2 
mxm_wmi                13021  1 nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    84169  1 nouveau
drm_kms_helper         52710  1 nouveau
drm                   297056  4 ttm,drm_kms_helper,nouveau
ahci                   25819  3 
atl1c                  46086  0 
libahci                32009  1 ahci
video                  19318  2 nouveau,asus_wmi
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi


```


```

$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        E0:CB:4E:5D:CC:BE

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [TP-LINK_PC_NETWORK] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        1C:4B:D6:6F:4E:DF

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *TP-LINK_PC_NETWORK: Infra, D8:5D:4C:AE:5E:C6, Freq 2412 MHz, Rate 54 Mb/s, Strength 66 WEP

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```


```

$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: D8:5D:4C:AE:5E:C6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_PC_NETWORK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000004e4a8
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001254502D4C494E4B5F50435F4E4554574F524B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010004000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD950050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000754502D4C494E4B1023000A544C2D5752313034334E10240003312E301042000131105400083034334E0004000110110024576972656C657373204E204769676162697420526F7574657220544C2D5752313034334E100800020084103C000101


```


```

/var/log$ grep -i networkmanager /var/log/syslog
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> wake requested (sleeping: yes  enabled: yes)
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> waking up and re-enabling...
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> (wlan0): bringing up device.
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> (wlan0): preparing device.
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 16 08:44:31 leon-1201N NetworkManager[736]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (eth0): bringing up device.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (eth0): preparing device.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <warn> Trying to remove a non-existant call id.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Auto-activating connection 'TP-LINK_PC_NETWORK'.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) starting connection 'TP-LINK_PC_NETWORK'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless): access point 'TP-LINK_PC_NETWORK' has security, but secrets are required.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless): connection 'TP-LINK_PC_NETWORK' has security, and secrets exist.  No new secrets needed.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'ssid' value 'TP-LINK_PC_NETWORK'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'scan_ssid' value '1'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'key_mgmt' value 'NONE'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'auth_alg' value 'OPEN'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'wep_key0' value '<omitted>'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: added 'wep_tx_keyidx' value '0'
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> Config: set interface ap_scan to 1
Mar 16 08:44:32 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: associating -> completed
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TP-LINK_PC_NETWORK'.
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> dhclient started with pid 5496
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 16 08:44:33 leon-1201N NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info>   address 192.168.1.105
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info>   prefix 24 (255.255.255.0)
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info>   gateway 192.168.1.1
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info>   nameserver '192.168.1.1'
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 16 08:44:34 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Mar 16 08:44:35 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 16 08:44:35 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 16 08:44:35 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 16 08:44:36 leon-1201N NetworkManager[736]: <info> Policy set 'TP-LINK_PC_NETWORK' (wlan0) as default for IPv4 routing and DNS.
Mar 16 08:44:36 leon-1201N NetworkManager[736]: <info> Writing DNS information to /sbin/resolvconf
Mar 16 08:44:36 leon-1201N NetworkManager[736]: <info> Activation (wlan0) successful, device activated.
Mar 16 08:44:54 leon-1201N NetworkManager[736]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 16 08:44:54 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 16 08:44:54 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 16 08:44:54 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

*** dropout ***

Mar 16 09:29:59 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 16 09:29:59 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 16 09:30:00 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 16 09:30:00 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 16 09:30:00 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 16 09:30:01 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 16 09:30:01 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 16 09:30:02 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: associating -> disconnected

*** etc... ***

Mar 16 09:35:29 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 16 09:35:30 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <warn> (wlan0): link timed out.
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: activated -> failed (reason 'supplicant-timeout') [100 120 11]
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <warn> Activation (wlan0) failed for connection 'TP-LINK_PC_NETWORK'
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 5496
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <warn> DNS: plugin dnsmasq update failed
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> Removing DNS information from /sbin/resolvconf
Mar 16 09:35:31 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> disconnected

*** Close lid ***

Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> sleep requested (sleeping: no  enabled: yes)
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> sleeping or disabling...
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (wlan0): cleaning up...
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (wlan0): taking down device.
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (eth0): cleaning up...
Mar 16 09:51:45 leon-1201N NetworkManager[736]: <info> (eth0): taking down device.

*** Open lid ***

Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> wake requested (sleeping: yes  enabled: yes)
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> waking up and re-enabling...
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (wlan0): bringing up device.
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (wlan0): preparing device.
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (eth0): bringing up device.
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (eth0): preparing device.
Mar 16 09:52:01 leon-1201N NetworkManager[736]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <warn> Trying to remove a non-existant call id.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Auto-activating connection 'TP-LINK_PC_NETWORK'.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) starting connection 'TP-LINK_PC_NETWORK'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless): access point 'TP-LINK_PC_NETWORK' has security, but secrets are required.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless): connection 'TP-LINK_PC_NETWORK' has security, and secrets exist.  No new secrets needed.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'ssid' value 'TP-LINK_PC_NETWORK'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'scan_ssid' value '1'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'key_mgmt' value 'NONE'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'auth_alg' value 'OPEN'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'wep_key0' value '<omitted>'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: added 'wep_tx_keyidx' value '0'
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> Config: set interface ap_scan to 1
Mar 16 09:52:02 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> (wlan0): supplicant interface state: associating -> completed
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TP-LINK_PC_NETWORK'.
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> dhclient started with pid 7383
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 16 09:52:03 leon-1201N NetworkManager[736]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info>   address 192.168.1.105
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info>   prefix 24 (255.255.255.0)
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info>   gateway 192.168.1.1
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info>   nameserver '192.168.1.1'
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 16 09:52:04 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> Policy set 'TP-LINK_PC_NETWORK' (wlan0) as default for IPv4 routing and DNS.
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> Writing DNS information to /sbin/resolvconf
Mar 16 09:52:05 leon-1201N NetworkManager[736]: <info> Activation (wlan0) successful, device activated.

```

---

### Post by kamm747 on 2014-03-22
Setting Network Manager's IPv6 Method to Ignore seems to have solved this for me.


The procedure in Lubuntu 13.10 was:

- Click network status icon
- Click on "Edit"
- Select the name of the wireless network
- Click on "Edit"
- Go to the "IPv6 Settings" tab
- In the "Method" dropdown, choose "Ignore"
- Click on "Save"

---

