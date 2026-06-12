---
title: "rfkill does not list my wireless LAN"
date: 2018-01-01
forum: Networking &amp; Wireless
---

### Post by tylernaes on 2018-01-01
Im running Ubuntu 16.04 on my laptop and now I cannot enable my wifi. I believe the issue is that when i run **rfkill list all**, my wireless LAN does not even show up. It is not an issue with my laptop having a physical switch on my laptop that enables/disables my wifi (I checked this). In "additional drivers" in "Software and updates" my wireless card is not even listed. I am posting below some terminal commands I have seen needed in previous forums for insight of my issue. Thank you in advance if anyone knows what I need to do.

```
~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
~$ lspci -knn | grep Net -A2
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel modules: rtl8821ae
```

```
~$ iwconfig
enp2s0    no wireless extensions.

lo        no wireless extensions.
```

```
~$ iwlist scan
enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```

---

### Post by Hadaka on 2018-01-02
Hi, we are ...confused ??
 The wireless card does show up..you posted it...
```
[COLOR=#000000][FONT=&amp]~$ lspci -knn | grep Net -A2[/FONT][/COLOR]03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482] [COLOR=#000000][FONT=&amp]    Kernel modules: rtl8821ae[/FONT][/COLOR]
```
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the **wireless-info.txt**
thanks.

---

### Post by tylernaes on 2018-01-02
I guess that is what I am confused about but shouldn't **rfkill list all** list a wireless LAN as well? It only lists the bluetooth.

Here are the contents from the wireless-info.txt document as requested:

```

########## wireless info START ##########

Report from: 02 Jan 2018 14:41 EST -0500

Booted last: 02 Jan 2018 00:00 EST -0500

Script from: 05 Dec 2017 03:13 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: XAVi Technologies Corp. RTL8821AE 802.11ac PCIe Wireless Network Adapter [1b9a:2482]
    Kernel modules: rtl8821ae

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID b49a:04f2  
Bus 001 Device 003: ID 0bda:57de Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mac80211              782336  0
cfg80211              602112  1 mac80211
wmi                    16384  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:10.0.0.86  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4458:d1a:8af7:1ee7/64 Scope:Link
          inet6 addr: 2601:cf:8080:a37f::e552/128 Scope:Global
          inet6 addr: 2601:cf:8080:a37f:e4f:93a7:6ebe:6317/64 Scope:Global
          inet6 addr: 2601:cf:8080:a37f:9d05:906e:1dda:5faa/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58568 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62635939 (62.6 MB)  TX bytes:7952538 (7.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1901086 (1.9 MB)  TX bytes:1901086 (1.9 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp2s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ga.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       817     1  0 Jan01 ?        00:00:22 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       1345e007-69e1-40b3-8f75-467e488c30c6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1345e007-69e1-40b3-8f75-467e488c30c6 | Auto Ethernet
IP4.ADDRESS[1]:                         10.0.0.86/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.ga.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 10.0.0.86
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.0.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 10.0.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hsd1.ga.comcast.net
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1515526773
DHCP4.OPTION[21]:                       host_name = tylernaes-X555UA
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.0.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.0.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
IP6.ADDRESS[1]:                         2601:cf:8080:a37f::e552/128
IP6.ADDRESS[2]:                         2601:cf:8080:a37f:9d05:906e:1dda:5faa/64
IP6.ADDRESS[3]:                         2601:cf:8080:a37f:e4f:93a7:6ebe:6317/64
IP6.ADDRESS[4]:                         fe80::4458:d1a:8af7:1ee7/64
IP6.GATEWAY:                            fe80::250:f1ff:fe80:0
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:61:73:aa:6b:42:df:41:4:3e:87:62:31:35:38:d:ea
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        rebind = 483840
DHCP6.OPTION[4]:                        max_life = 604800
DHCP6.OPTION[5]:                        preferred_life = 604800
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        life_starts = 1514770117
DHCP6.OPTION[9]:                        dhcp6_status_code = success Assigned an address.
DHCP6.OPTION[10]:                       ip6_address = 2601:cf:8080:a37f::e552
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 302400
DHCP6.OPTION[13]:                       starts = 1514770117
DHCP6.OPTION[14]:                       iaid = c2:04:45:dc
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:1:0:1:21:be:d0:be:0:50:f1:80:0:0

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/mike2cindy]] (600 root)
[connection] id=mike2cindy | type=wifi | permissions=
[wifi] bssid=<MAC address> | mac-address=B0:C0:90:4C:08:04 | mac-address-blacklist= | ssid=mike2cindy
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/FCPLUnplugged]] (600 root)
[connection] id=FCPLUnplugged | type=wifi | permissions=user:tylernaes:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FCPLUnplugged
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="r8169 enp2s0"

##### udev rules ########################

##### dmesg #############################

[ 5104.612203] rtlwifi: version magic '4.10.0-28-generic SMP mod_unload ' should be '4.10.0-42-generic SMP mod_unload '
[ 9661.519182] [drm] GuC firmware load skipped
[ 9661.531582] r8169 0000:02:00.0 enp2s0: link down
[ 9664.053705] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 9664.075321] r8169 0000:02:00.0 enp2s0: link down
[ 9664.075451] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 9666.944717] r8169 0000:02:00.0 enp2s0: link up
[ 9666.944744] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-01-02
What are the results for ```
dkms status
```

---

### Post by tylernaes on 2018-01-02
dkms wasn't installed when I tried so I installed it and rebooted my laptop (not sure if i needed to or not). When I tried **dkms status** it did not return anything.

```

tylernaes@tylernaes-X555UA:~$ dkms status
tylernaes@tylernaes-X555UA:~$
```

---

### Post by jeremy31 on 2018-01-02
Ok, then try
```
sudo apt-get install --reinstall linux-image-extra-$(uname -r)
```
Reboot

---

### Post by tylernaes on 2018-01-03
Sorry for the late response to your suggestion but I encountered a lot of issues. So after I ran **sudo apt-get install --reinstall linux-image-extra-$(uname -r)** and rebooted, I was able to use my wifi. However, I was only able to use my wifi for a couple minutes, then my laptop would disconnect from the network and I couldn't reconnect to the network unless I rebooted my laptop. Apparently this is a known issue and I found forums that had the same issues as I did and the solution was to install the various realtek drivers (it includes my rtl8821ae) by:

```

sudo apt-get install linux-headers-generic build-essential git git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make 
sudo make install

```
and then reboot.

This did allow me to connect to my network via wifi however after a couple of minutes All of the memory was taken up in my computer. It turns out that there is an error being written in the syslog and kern.log files at a rate of about 30 Gb/min. I am posting what is contained in the files below:

What is being written constantly in the syslog and kern.log~
```

Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395722] pcieport 0000:00:1c.5:    [ 0] Receiver Error        
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395726] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395734] pcieport 0000:00:1c.5: can't find device of ID00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395736] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395740] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395742] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395743] pcieport 0000:00:1c.5:    [ 0] Receiver Error        
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395747] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395755] pcieport 0000:00:1c.5: can't find device of ID00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395757] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395762] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395763] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00000001/00002000
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395765] pcieport 0000:00:1c.5:    [ 0] Receiver Error        
Jan  3 19:30:23 tylernaes-X555UA kernel: [  252.395768] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
...

```

Suggestions?

---

