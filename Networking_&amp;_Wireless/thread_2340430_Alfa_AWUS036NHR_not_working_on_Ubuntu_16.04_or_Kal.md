---
title: "Alfa AWUS036NHR not working on Ubuntu 16.04 or Kali"
date: 2016-10-18
forum: Networking &amp; Wireless
---

### Post by 01100010r0k3n on 2016-10-18
I've been trying to setup my laptop for PenTesting. However the one problem is my Alfa wireless adapter is not co-operating. I have a dual boot with Ubuntu and Kali Linux. Ubuntu also has a Kali VM in Virtualbox. The extension pack is installed in Virtualbox. I can't get the Alfa to work the way I want. In Ubuntu I can see the adapter and connect to wifi APs. However in the Kali VM when I look at USB devices I don't see anything listed. I followed a Youtube video and created a new USB filter that didn't work either. When I boot to Kali and bring the adapter down to change the mode the light never turns back on when I try to bring it back up. Then when I try to do the wash command it says the adapter can't be used to get packets. I've searched all over and the information is either dated or it didn't work. I did find this thread [https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385) which I haven't tried yet. Here is all my info

Ubuntu 16.04 x64
```
cd ~/Desktop/backports-4.4.2-1
make defconfig-wifi
make
sudo make install

root@Savage:/home/br0k3n# modprobe rtl8187
root@Savage:/home/br0k3n# dmesg | grep rtl
[   21.674873] rtl8192cu: Chip version 0x10
[   22.138080] rtl8192cu: MAC address: 00:c0:ca:7b:ab:f1
[   22.138087] rtl8192cu: Board Type 1
[   22.139437] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   22.139524] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   22.139713] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[   22.139982] usbcore: registered new interface driver rtl8192cu
[   22.275688] rtl8192cu 2-3:1.0 wlx00c0ca7babf1: renamed from wlan0
[   33.363604] rtl8192cu: MAC auto ON okay!
[   33.591078] rtl8192cu: Tx queue select: 0x05
[ 1023.270605] usbcore: registered new interface driver rtl8187
root@Savage:/home/br0k3n# 

lsusb
Bus 002 Device 004: ID 0bda:817f Realtek Semiconductor Corp. RTL8188RU 802.11n WLAN Adapter

lsmod
Module                  Size  Used by
rfcomm                 69632  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
ctr                    16384  3
ccm                    20480  3
bnep                   20480  2
drbg                   32768  1
ansi_cprng             16384  0
dm_crypt               28672  2
rtsx_usb_ms            20480  0
memstick               20480  1 rtsx_usb_ms
uvcvideo               90112  0
ath3k                  20480  0
btusb                  45056  0
btrtl                  16384  1 btusb
videobuf2_vmalloc      16384  1 uvcvideo
btbcm                  16384  1 btusb
btintel                16384  1 btusb
kvm_amd                65536  0
kvm                   540672  1 kvm_amd
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
videobuf2_v4l2         28672  1 uvcvideo
crc32_pclmul           16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
aesni_intel           167936  2899
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
arc4                   16384  2
ath9k                  94208  0
hid_multitouch         20480  0
dell_wmi               16384  0
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
ath9k_common           36864  1 ath9k
ablk_helper            16384  1 aesni_intel
ath9k_hw              450560  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
dcdbas                 16384  1 dell_laptop
dell_led               16384  1
edac_mce_amd           24576  0
dell_smm_hwmon         16384  0
mac80211              647168  1 ath9k
cryptd                 20480  1448 aesni_intel,ablk_helper
joydev                 20480  0
input_leds             16384  0
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
serio_raw              16384  0
compat                 16384  4 cfg80211,ath9k_common,ath9k,mac80211
edac_core              53248  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
snd_hda_intel          40960  5
fam15h_power           16384  0
i2c_piix4              24576  0
mac_hid                16384  0
k10temp                16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
dell_rbtn              16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
shpchp                 36864  0
tpm_crb                16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
i2c_designware_platform    16384  0
8250_dw                16384  0
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_designware_core    20480  1 i2c_designware_platform
soundcore              16384  1 snd
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 49152  0
amdkfd                131072  2
amd_iommu_v2           20480  1 amdkfd
amdgpu                987136  3
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
psmouse               126976  0
drm_kms_helper        155648  1 amdgpu
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  3
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   364544  58 ttm,drm_kms_helper,amdgpu
r8169                  81920  0
mii                    16384  1 r8169
wmi                    20480  2 dell_led,dell_wmi
fjes                   28672  0
video                  40960  2 dell_wmi,dell_laptop
i2c_hid                20480  0
hid                   118784  4 i2c_hid,hid_multitouch,hid_generic,usbhid

root@Savage:/home/br0k3n# agi build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by QIII on 2016-10-18
Is your question specifically about Kali in the VM?

Let me remind those who may answer:  Discussions of penetration testing and pen testing tools are not allowed on the Ubuntu Forums.

Keep this discussion strictly to solving the ooerational failure of the hardware or the thread will be closed.

---

### Post by 01100010r0k3n on 2016-10-18
My question is about getting the adapter to work. I don't care if it works in Ubuntu or Kali I just want it to be recognized properly. I don't need discussion of pentesting I know what I'm doing there. The card is reporting as 8188 but loading firmware is 8192cu. I just want the card to be recognized properly by Ubuntu and show up in my list of USB items in the VM. There must be something I'm doing wrong.
Here are the results of the script
```

########## wireless info START ##########

Report from: 18 Oct 2016 14:41 EDT -0400

Booted last: 18 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:06bd]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020e]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 004: ID 0bda:817f Realtek Semiconductor Corp. RTL8188RU 802.11n WLAN Adapter
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0c45:6712 Microdia 
Bus 002 Device 004: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 003: ID 2a94:5201  
Bus 002 Device 006: ID 0cf3:e005 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              94208  0
rtl_usb                24576  1 rtl8192cu
rtl8192c_common        77824  1 rtl8192cu
rtlwifi               106496  3 rtl_usb,rtl8192c_common,rtl8192cu
ath3k                  20480  0
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
ath9k                  94208  0
dell_wmi               16384  0
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
ath9k_common           36864  1 ath9k
ath9k_hw              450560  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
dcdbas                 16384  1 dell_laptop
mac80211              647168  4 ath9k,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  5 ath,ath9k_common,ath9k,mac80211,rtlwifi
compat                 16384  6 cfg80211,ath9k_common,ath9k,mac80211,rtlwifi,rtl8192cu
wmi                    20480  2 dell_led,dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:10.0.1.175  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::3af2:454d:a2b1:da57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:236224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141197748 (141.1 MB)  TX bytes:13766954 (13.7 MB)

wlx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF3]>' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF3]>  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlp2s0    IEEE 802.11bgn  ESSID:"TCaps12"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'TCaps12' [AC5]>   
          Bit Rate=52 Mb/s   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:114  Invalid misc:2449   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    600    0        0 wlp2s0
10.0.0.0        0.0.0.0         255.0.0.0       U     600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search guest.local

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1025     1  0 08:42 ?        00:00:13 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TCaps12
GENERAL.CON-UUID:                       dad06d0a-f0f5-40a2-ace1-6ff6fb348144
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     57 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dad06d0a-f0f5-40a2-ace1-6ff6fb348144 | TCaps12
IP4.ADDRESS[1]:                         10.0.1.175/8
IP4.GATEWAY:                            10.0.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.1.1
IP4.DOMAIN[1]:                          guest.local
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1476880984
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.0.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.1.175
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = guest.local
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.255.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 10.0.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.0.0.0
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.1.1
IP6.ADDRESS[1]:                         fe80::3af2:454d:a2b1:da57/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         0bda
GENERAL.PRODUCT:                        11n USB
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.3/1-1.3:1.0/net/wlx<IF from MAC [IF3]>
GENERAL.IP-IFACE:                       
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
shih                          <MAC 'shih' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Groovyshoes                   <MAC 'Groovyshoes' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HP-Print-73-LaserJet Pro MFP  <MAC 'HP-Print-73-LaserJet Pro MFP' [AC15]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
One Zone_High Speed Internet  <MAC 'One Zone_High Speed Internet' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
TCaps12                       <MAC 'TCaps12' [AC5]>  Infra  3     2422 MHz  54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA2       yes     * 
BELL288                       <MAC 'BELL288' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no        
Carl's Jr Guest               <MAC 'Carl's Jr Guest' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
QSWPVT-2F                     <MAC 'QSWPVT-2F' [AC8]>  Infra  9     2452 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no        
HP-Print-2F-LaserJet Pro MFP  <MAC 'HP-Print-2F-LaserJet Pro MFP' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --         no        
CMPA Toronto                  <MAC 'CMPA Toronto' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
AP12A                         <MAC 'AP12A' [AC6]>  Infra  4     2427 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
--                            <MAC '

########## wireless info START ##########

Report from: 18 Oct 2016 14:41 EDT -0400

Booted last: 18 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:06bd]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020e]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 004: ID 0bda:817f Realtek Semiconductor Corp. RTL8188RU 802.11n WLAN Adapter
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0c45:6712 Microdia 
Bus 002 Device 004: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 003: ID 2a94:5201  
Bus 002 Device 006: ID 0cf3:e005 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              94208  0
rtl_usb                24576  1 rtl8192cu
rtl8192c_common        77824  1 rtl8192cu
rtlwifi               106496  3 rtl_usb,rtl8192c_common,rtl8192cu
ath3k                  20480  0
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
ath9k                  94208  0
dell_wmi               16384  0
dell_laptop            20480  0
sparse_keymap          16384  1 dell_wmi
ath9k_common           36864  1 ath9k
ath9k_hw              450560  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
dcdbas                 16384  1 dell_laptop
mac80211              647168  4 ath9k,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  5 ath,ath9k_common,ath9k,mac80211,rtlwifi
compat                 16384  6 cfg80211,ath9k_common,ath9k,mac80211,rtlwifi,rtl8192cu
wmi                    20480  2 dell_led,dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:10.0.1.175  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::3af2:454d:a2b1:da57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:236224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141197748 (141.1 MB)  TX bytes:13766954 (13.7 MB)

wlx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF3]>' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF3]>  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlp2s0    IEEE 802.11bgn  ESSID:"TCaps12"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'TCaps12' [AC5]>   
          Bit Rate=52 Mb/s   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:114  Invalid misc:2449   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    600    0        0 wlp2s0
10.0.0.0        0.0.0.0         255.0.0.0       U     600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search guest.local

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1025     1  0 08:42 ?        00:00:13 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TCaps12
GENERAL.CON-UUID:                       dad06d0a-f0f5-40a2-ace1-6ff6fb348144
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     57 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dad06d0a-f0f5-40a2-ace1-6ff6fb348144 | TCaps12
IP4.ADDRESS[1]:                         10.0.1.175/8
IP4.GATEWAY:                            10.0.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.1.1
IP4.DOMAIN[1]:                          guest.local
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1476880984
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.0.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.1.175
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = guest.local
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.255.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 10.0.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.0.0.0
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.1.1
IP6.ADDRESS[1]:                         fe80::3af2:454d:a2b1:da57/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         0bda
GENERAL.PRODUCT:                        11n USB
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:12.0/usb1/1-1/1-1.3/1-1.3:1.0/net/wlx<IF from MAC [IF3]>
GENERAL.IP-IFACE:                       
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
shih                          <MAC 'shih' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Groovyshoes                   <MAC 'Groovyshoes' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
HP-Print-73-LaserJet Pro MFP  <MAC 'HP-Print-73-LaserJet Pro MFP' [AC15]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
One Zone_High Speed Internet  <MAC 'One Zone_High Speed Internet' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
TCaps12                       <MAC 'TCaps12' [AC5]>  Infra  3     2422 MHz  54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA2       yes     * 
BELL288                       <MAC 'BELL288' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no        
Carl's Jr Guest               <MAC 'Carl's Jr Guest' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --         no        
QSWPVT-2F                     <MAC 'QSWPVT-2F' [AC8]>  Infra  9     2452 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no        
HP-Print-2F-LaserJet Pro MFP  <MAC 'HP-Print-2F-LaserJet Pro MFP' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --         no        
CMPA Toronto                  <MAC 'CMPA Toronto' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
AP12A                         <MAC 'AP12A' [AC6]>  Infra  4     2427 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
--                            <MAC '
```

---

### Post by 01100010r0k3n on 2016-10-19
Well I at least got it partially working. I got it working in Kali and that's good enough for now. I'd love to get it working in the VM as well but I'm seeing that Kali has always had problems in a VM. I may create a new VM instead of using a Kali vbox image. Anyway this laptop has this peculiarity. There are 3 USB ports, 2 USB2 on one side and a USB3 on the other side. Usually I had my mouse plugged into the USB2. If I plugged the Alfa into the USB3 port for some reason it didn't work at all. If I plugged it into the other USB2 port I get the problems I described. I switched it so that my mouse is plugged into the USB3 and the Alfa is in the USB2 and in Kali I have no problems =) Now I just need to get it working in the VM and I'll be golden.

---

