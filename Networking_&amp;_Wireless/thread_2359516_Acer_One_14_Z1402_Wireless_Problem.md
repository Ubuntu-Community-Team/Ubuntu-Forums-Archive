---
title: "Acer One 14 Z1402 Wireless Problem"
date: 2017-04-25
forum: Networking &amp; Wireless
---

### Post by rajnish-mumbai on 2017-04-25
Hi all,
Just want to share, I have a laptop acer one 14 z1402- NX. Y52SI. 005, and  installed Ubuntu 17.04. And one that not working are Wireless (Wifi).
After looking around I found the solution for the wireless / wifi in here
[https://forums.linuxmint.com/viewtopic.php?t=208434](https://forums.linuxmint.com/viewtopic.php?t=208434)
With solution from as below, (with connection to internet via other device, I connected through bluetooth teethring):

sudo apt-get install git build-essential
git clone [https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu)
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu

Unfortunately It didn't works for me. 
When I boot up Network Manager doesnt show any wireless SSID's however of restart of wireless adapter starts showing all. But it still doesn't connect. 

Output of lsusb is 
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:065e Acer, Inc 
Bus 001 Device 006: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and lspci is 

```
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 21)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 21)
00:13.0 SATA controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SATA Controller (rev 21)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 21)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 21)
00:1b.0 Audio device: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller (rev 21)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 21)
00:1c.1 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #2 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 21)
00:1f.3 SMBus: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller (rev 21)


```

---

### Post by wildmanne39 on 2017-04-25
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here.

---

### Post by rajnish-mumbai on 2017-04-25
Here is the link to Pastebin [URL="http://paste.ubuntu.com/24452703/"]http://paste.ubuntu.com/24452703/

[/URL]```
  
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"][/TD]
[TD="class: code"]########## wireless info START ##########

Report from: 25 Apr 2017 12:23 IST +0530

Booted last: 25 Apr 2017 00:00 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:065e Acer, Inc 
Bus 001 Device 002: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8xxxu              126976  0
mac80211              782336  1 rtl8xxxu
cfg80211              602112  1 mac80211
snd_soc_rt5670        126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5670
snd_soc_core          233472  2 snd_soc_rt5670,snd_soc_sst_mfld_platform
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_soc_rt5670,snd_pcm_dmaengine,snd_hda_core,snd_hda_codec_hdmi,snd_soc_sst_mfld_platform,snd_soc_core
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlx38a28c6f18c4: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlx38a28c6f18c4' [IF1]> brd <MAC address>
3: bnep0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether <MAC 'bnep0' [IF2]> brd <MAC address>
    inet 192.168.44.174/24 brd 192.168.44.255 scope global dynamic bnep0
       valid_lft 2321sec preferred_lft 2321sec
    inet6 fe80::9057:82c2:cc5e:9c3f/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

bnep0     no wireless extensions.

wlx38a28c6f18c4  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.44.1 dev bnep0 proto static metric 750 
169.254.0.0/16 dev bnep0 scope link metric 1000 
192.168.44.0/24 dev bnep0 proto kernel scope link src 192.168.44.174 metric 750 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       790     1  0 10:18 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_C4_0B_CB_58_D2_C8
GENERAL.IP-IFACE:                       bnep0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Rag Network
GENERAL.CON-UUID:                       654063d7-ac30-43a3-8181-5845320245e9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 DUN NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   654063d7-ac30-43a3-8181-5845320245e9 | Rag Network
IP4.ADDRESS[1]:                         192.168.44.174/24
IP4.GATEWAY:                            192.168.44.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.44.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.44.1
DHCP4.OPTION[5]:                        ip_address = 192.168.44.174
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.44.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.44.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 2984
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.44.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1634
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1493105529
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = Prisheen-One
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.44.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.44.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::9057:82c2:cc5e:9c3f/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx38a28c6f18c4
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.10.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx38a28c6f18c4' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/net/wlx38a28c6f18c4
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4a0f09af-88a3-43d0-86bb-05b5c6c11a25 | Prisheen

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Prisheen  <MAC 'Prisheen' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Prisheen]] (600 root)
[connection] id=Prisheen | type=wifi | permissions=user:rkhare:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Prisheen
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

bnep0     no frequency information.

wlx38a28c6f18c4  14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

bnep0     Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlx38a28c6f18c4  Scan completed :
          Cell 01 - Address: <MAC 'Prisheen' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Prisheen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dd70ac180
                    Extra: Last beacon: 384ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     4579E6203C3D3D3D7D7B53E
depends:        mac80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6FCDB39CB1DCCA0C9A450B2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0ADFC23D0B6BCD6916160E7
depends:        
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

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
blacklist rtl8723au
blacklist r8723au
blacklist rtl8723bu
blacklist r8723bu

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    9.797787] usb 1-4: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[   10.746750] rtl8xxxu 1-4:1.2 wlx38a28c6f18c4: renamed from wlan0
[   12.236492] IPv6: ADDRCONF(NETDEV_UP): wlx38a28c6f18c4: link is not ready (repeated 27 times)

########## wireless info END ############[/TD]
[/TR]
[/TABLE]

```[URL="http://paste.ubuntu.com/24452703/"]
[/URL]

---

### Post by rajnish-mumbai on 2017-04-25
Please ignore the above information, I have reinstalled everything from  scratch and here is the new link of the wireless info pastebin
[http://paste.ubuntu.com/24453795/](http://paste.ubuntu.com/24453795/)

---

### Post by wildmanne39 on 2017-04-25
The driver for your device comes in Ubuntu now but I do not think it works good, we need to modify a file since you are using 17.04 then we will go from their.

Open this file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0

```
Save and close file then reboot.

Unplug your wired connection.

---

### Post by rajnish-mumbai on 2017-04-26
Thanks, it worked like wonder but
When I initially rebooted my laptop (and after every restart) the wifi adapter doesn't seems to scan properly. As I can not see any devices in list. Enabling / Disabling from Network Manager also doesnt change the status. Only when I used laptop hardware key (In my case fn + F4) to switch off and then on wireless network, it started properly and now working perfectly.

---

### Post by wildmanne39 on 2017-04-26
Run the wireless script when you can not connect, before you push the hardware switch then post the output to pastebin and the link here.
Thanks

---

### Post by rajnish-mumbai on 2017-04-26
Here is the link [http://paste.ubuntu.com/24459963/](http://paste.ubuntu.com/24459963/)

---

### Post by wildmanne39 on 2017-04-26
Please post the output when it is working to so we can compare them and see if we see the little differences.
Thanks

---

### Post by rajnish-mumbai on 2017-04-26
here is the link with working wifi [http://paste.ubuntu.com/24461214/](http://paste.ubuntu.com/24461214/)

---

### Post by wildmanne39 on 2017-04-26
We are going to install the new driver, I believe you had it installed but removed it. Please do:
```
sudo apt update && sudo apt upgrade
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8723bu.git
```

Now compile the driver, then install it:
```
cd rtl8723bu
make
sudo make install
echo "blacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rv rtl8xxxu
sudo modprobe -v 8723bu

```
When the kernel receives an upgrade you will have to:
```
cd rtl8723bu
make clean
make
sudo make install
sudo modprobe -v 8723bu
```
Report back after you run the above commands, please watch for errors, if you still have issues there a couple of more things we can do.
Thanks

---

### Post by rajnish-mumbai on 2017-04-27
While I rand make command, got following error during the process which continued normally for rest of the part

> /home/rkhare/rtl8723bu/core/rtw_mlme.c: In function ‘rtw_restructure_ht_ie’:
/home/rkhare/rtl8723bu/core/rtw_mlme.c:3663:3: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
   if (stbc_rx_enable)
   ^~
/home/rkhare/rtl8723bu/core/rtw_mlme.c:3666:18:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
                  set_mcs_rate_by_mask(ht_capie.supp_mcs_set, MCS_RATE_1R);
                  ^~~~~~~~~~~~~~~~~~~~

and on 

> sudo modprobe -v 8723bu
modprobe: FATAL: Module 8723bu not found in directory /lib/modules/4.10.0-20-generic


After this it got disconnected and its not connecting now even after reboot and hardware switch.

Link to latest wireless script [http://paste.ubuntu.com/24465379/](http://paste.ubuntu.com/24465379/)

---

### Post by wildmanne39 on 2017-04-27
Do:
```
sudo sed 's/blacklist rtl8xxxu//' -i /etc/modprobe.d/blacklist.conf
sudo modprobe -v rtl8xxxu
```

Did the 8723bu driver install successfully the first time you tried it?

---

### Post by rajnish-mumbai on 2017-04-28
> **wildmanne39 said:**
> Do:
```
sudo sed 's/blacklist rtl8xxxu//' -i /etc/modprobe.d/blacklist.conf
sudo modprobe -v rtl8xxxu
```

This brings it back to original state where after hardware switch I could see my router listed in network manager but it doesn't connect. Also it disappears after trying to connect, whereas other networks in neighborhood are still visible. 
:confused:

>  Did the 8723bu driver install successfully the first time you tried it?

No it was having same issues as stated in my previous post

---

### Post by wildmanne39 on 2017-04-28
I have to leave town early in the morning and will be gone all day so hopefully someone will jump in and help if not I will check on this thread as soon as I get back.

The driver we tried to compile worked fine on my 16.04 Ubuntu, I imagine the driver is not updated for 17.04 yet.

---

### Post by wildmanne39 on 2017-04-28
Please run the wireless script again and post the output to pastbin so we can see the current state of your network.

---

### Post by rajnish-mumbai on 2017-04-29
Here is the link while I am connected using Blue tooth tethering [http://paste.ubuntu.com/24477215/](http://paste.ubuntu.com/24477215/)

---

### Post by rajnish-mumbai on 2017-05-01
> **wildmanne39 said:**
> The driver for your device comes in Ubuntu now but I do not think it works good, we need to modify a file since you are using 17.04 then we will go from their.

Open this file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0

```
Save and close file then reboot.

Unplug your wired connection.

After a fresh re install I did run only these 2 comands and for now I am happy to toggle hardware switch everytime I start my system (Normally once in few days as its mostly in sleep mode when I am not working). I am expecting the issue will be sorted out in due course with some kind of update. Thank you wildmanne for all your kind support. 
Going ahead and installing all other apps and transfering files to switch to Production mode. 
Note : I even tried installing 16.04 and there were many issues in 16.04 as well.

---

### Post by wildmanne39 on 2017-05-02
Your welcome! glad it is working well enough for you, we might be able to get it the way you want it but it might be a slow and painful process and you could lose internet again.

So if you are happy I would leave it for now.

---

