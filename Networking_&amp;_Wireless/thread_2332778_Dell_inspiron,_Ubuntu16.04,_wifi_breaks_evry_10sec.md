---
title: "Dell inspiron, Ubuntu16.04, wifi breaks evry 10secs. Intel DualBand AC 3160 [8086:847"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by jiimms on 2016-08-03
Hi,

I have tried almost all suggestions on the net but cant get the wifi to work. This is the third day of struggling with this issue.
Wireless-info-txt is 

```

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
    Kernel driver in use: iwlwifi

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:06b0]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 0c45:6710 Microdia 
Bus 002 Device 003: ID 1a2c:0021 China Resource Semico Co., Ltd Keyboard
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
snd_soc_rt5640        114688  0
iwlwifi               200704  1 iwlmvm
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF1]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212f:c2ce:4f19:baa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13991345 (13.9 MB)  TX bytes:1511019 (1.5 MB)

wlp6s0    Link encap:Ethernet  HWaddr <MAC 'wlp6s0' [IF2]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c98e:1c2e:3b05:aca3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:659463 (659.4 KB)  TX bytes:118831 (118.8 KB)

##### iwconfig ##########################

enp7s0    no wireless extensions.

lo        no wireless extensions.

NetworkManager

Running:

root      2648     1  0 04:39 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       enp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       110bde8b-ed9b-4d47-899c-00cf1f3b52a2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   110bde8b-ed9b-4d47-899c-00cf1f3b52a2 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1470352536
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = domain.name
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::212f:c2ce:4f19:baa5/64
IP6.GATEWAY:                            fe80::205:1dff:fe03:405

GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp6s0' [IF2]>


```

I have just installed and updated 16.04(started with 14.04 but messed it up somehow trying to get wifi to work and ended with blue screen) so I guess it is up to date. 
I have copied the  firmware from [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) but didnt work.

Three days old with Ubuntu, any help is greatly appreciated.
sorry if I have missed out any information

---

