---
title: "XPS 13 (9380) wifi dropping and crashing network-manager"
date: 2019-03-20
forum: Networking &amp; Wireless
---

### Post by funkymonk96 on 2019-03-20
I have dual booted my XPS13 with ubuntu 18.04.2 and since day 1 of using ubuntu I've had problems with the wifi randomly dropping, crashing the netwrok-manager and sometimes freezing the system (sudo hangs and system becomes unresponsive). I have tried updating the kernel and the ath10k firmware, as suggested in other posts, but I kept encountering the same problems. The wifi works perfectly on the windows partition.

This is the wireless info of my current drivers. I'm running kernel 5.0.3 as it is the one that has kept the wifi working for the longest so far.
 ```

########## wireless info START ##########

Report from: 20 Mar 2019 15:55 GMT +0000

Booted last: 20 Mar 2019 00:00 GMT +0000

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.0.3-050003-generic #201903191333 SMP Tue Mar 19 13:35:24 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:143a]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e0a2 Foxconn / Hon Hai 
Bus 001 Device 002: ID 0c45:6723 Microdia 
Bus 001 Device 004: ID 27c6:5385  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

dell_laptop            20480  0
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_hda_codec_realtek,dell_laptop
ath10k_pci             40960  0
ath10k_core           434176  1 ath10k_pci
dell_wmi               20480  0
dell_smbios            28672  2 dell_wmi,dell_laptop
ath                    36864  1 ath10k_core
mac80211              806912  1 ath10k_core
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
intel_wmi_thunderbolt    20480  0
wmi_bmof               16384  0
cfg80211              671744  3 ath,mac80211,ath10k_core
sparse_keymap          16384  2 intel_hid,dell_wmi
wmi                    28672  5 intel_wmi_thunderbolt,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  45056  3 dell_wmi,dell_laptop,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF1]> brd <MAC address>
    inet 192.168.1.9/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 86261sec preferred_lft 86261sec
    inet6 fd00:5a13:7f16:b700:e43b:a1ad:98ea:3518/64 scope global temporary dynamic 
       valid_lft 7062sec preferred_lft 3462sec
    inet6 fd00:5a13:7f16:b700:fb7:3ccf:77ad:f466/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 7062sec preferred_lft 3462sec
    inet6 fe80::4655:2a1f:cf8:651b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:"TALKTALK7F16B7"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'TALKTALK7F16B7' [AC1]>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

##### route #############################

default via 192.168.1.1 dev wlp2s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp2s0 scope link metric 1000 
192.168.1.0/24 dev wlp2s0 proto kernel scope link src 192.168.1.9 metric 600 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       873     1  0 15:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 5.0.3-050003-generic
GENERAL.FIRMWARE-VERSION:               RM.4.4.1.c2-00057-QCARMSWP-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TALKTALK7F16B7
GENERAL.CON-UUID:                       acbdaed4-6834-4aa3-ba78-833e104d64fe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     6 Mb/s
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
WIFI-PROPERTIES.5GHZ:                   yes
IP4.ADDRESS[1]:                         192.168.1.9/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        domain_name = lan
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1553183598
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.9
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[30]:                       requested_domain_name_servers = 1
IP6.ADDRESS[1]:                         fd00:5a13:7f16:b700:e43b:a1ad:98ea:3518/64
IP6.ADDRESS[2]:                         fd00:5a13:7f16:b700:fb7:3ccf:77ad:f466/64
IP6.ADDRESS[3]:                         fe80::4655:2a1f:cf8:651b/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fd00:5a13:7f16:b700::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[2]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:a6:0:5a:13:7f:16:b7
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:b3:3f:95:4c:16:4e:c7:45:39:b2:eb:74:11:7b:3:66
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   acbdaed4-6834-4aa3-ba78-833e104d64fe | TALKTALK7F16B7

SSID             BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
TALKTALK7F16B7   <MAC 'TALKTALK7F16B7' [AC2]>  Infra  1     2412 MHz  270 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no             
TALKTALK7F16B7   <MAC 'TALKTALK7F16B7' [AC1]>  Infra  44    5220 MHz  270 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     *      
PLUSNET-2NG5     <MAC 'PLUSNET-2NG5' [AC4]>  Infra  6     2437 MHz  130 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no             
--               <MAC '
```

I know Dell sells a Developer edition of this laptop (same hardware) that comes with Ubuntu preinstalled, so there must be a stable configuration for the wifi. If anyone knows what the kernel and drivers the 2019 XPS13 developer edition ships with, or how to fix the unstable wifi issue, it would be very helpful. Thank you.


To add a quick unrelated issue, I have partitioned the ssd and installed ubuntu without disabling bitlocker encryption, and on some boots into windows I am asked for my bitlocker key. Is it safe to unencrypt the ssd now, or is there a way to avoid having to type the key in?

---

### Post by jeremy31 on 2019-03-20
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) for some basic tricks for wifi

---

### Post by funkymonk96 on 2019-03-20
i followed the steps in the link, power saving was already disabled and the regulatory domain was already set to my region.  I have now set the IPv6 to ignore (even though this seems like a workaround that could have drawbacks). I can't access my router since I'm on uni wifi. I'll report if I encounter more crashes.

EDIT: wireless info is not complete in first post, but I'm not sure how to attach tar.gz files here (text file exceeds  size limit). lshw returns:
 configuration: broadcast=yes driver=ath10k_pci driverversion=5.0.3-050003-generic firmware=RM.4.4.1.c2-00057-QCARMSWP-1

---

### Post by funkymonk96 on 2019-03-21
I have followed the steps in the link but the connection dropped again. If I could get some info from someone who has boght the xps13 developer edition I think that would be very helpful

---

### Post by jeremy31 on 2019-03-21
You can run the wireless script and upload to a paste site with ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post termbin URL

It is possible that the developer edition uses different wifi cards

---

### Post by funkymonk96 on 2019-03-24
[https://termbin.com/itx5](https://termbin.com/itx5) for the wifi info

I am pretty confident that the developer edition has the same hardware (according to dell's website and a quick google search). If anyone with a developer 2019 xps 13 could reply it would be very helpful. Thank you!

---

### Post by jeremy31 on 2019-03-24
Can you change the encryption used on the router to just WPA2-PSK, TKIP causes problems with many wifi cards in Linux

---

### Post by funkymonk96 on 2019-03-25
Unfortunately the problem is present also when I am on university wifi, so I would not be able to change the encryption on that network. I will upload the wireless-info script on that network as soon as I connect to it

EDIT: checked my home router setting and I can't seem to be able to change the encryption from TKIP+AES (there is no other option).

---

### Post by noxpor on 2019-03-26
Hi !

I have the same kind of problem with my XPS (the 9360 version though): wifi dropping and NM hanging and freezing almost everything.
In my case, NM hang every time I connect to a 5ghz AP but if I connect to the same AP in 2.4Ghz, it's pretty stable.

Have you checked the bands used when NM crash ?

---

### Post by funkymonk96 on 2019-03-26
I have not checked but it is very possible that NM crashed when connecting to 5Ghz. How do you set it to only connect to 2.4Ghz?

---

### Post by noxpor on 2019-03-29
Not sure you can do it (simply). I just select a 2.4Ghz AP when connecting.

---

### Post by funkymonk96 on 2019-04-24
Only connecting to 2.4Ghz seems to be working so far (over ~1 day and 3 different networks), just wish there was an actual fix for the problem

---

