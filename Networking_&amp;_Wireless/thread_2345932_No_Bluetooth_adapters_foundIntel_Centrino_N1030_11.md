---
title: "No Bluetooth adapters found/Intel Centrino N1030 11230BNHMW"
date: 2016-12-09
forum: Networking &amp; Wireless
---

### Post by thesuffering on 2016-12-09
[COLOR=#111111][FONT=Ubuntu]Laptop[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Gateway NE56R41u
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Wireless Card[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]PCIe half mini Intel Centrino N-1030 11230BNHMW
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I took this Intel Centrino card out of my Dell Inspiron N4110 to replace with something compatible for wifi with OSX for hackintosh. I want to add bluetooth to my Gateway NE56R41U, so I took the existing PCIe half mini card out, and put this one in. Wifi works great in Ubuntu, but bluetooth tells me no bluetooth adapters found and rfkill list displays only this:[/FONT][/COLOR]
```

0:  phy0:  Wireless LAN
         Soft blocked:  no
         Hard blocked: no
1:  acer-wireless:  Wireless LAN
         Soft blocked:  no
         Hard blocked: no

```
[COLOR=#111111][FONT=Ubuntu]Nothing bluetooth wise shows up in there. I looked in the BIOS and its pretty bare bones and limited, no options for anything USB or Bluetooth in there at all.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas on how to get bluetooth working?[/FONT][/COLOR]

---

### Post by thesuffering on 2016-12-09
Additional info:
```

########## wireless info START ##########

Report from: 09 Dec 2016 09:53 MST -0700

Booted last: 09 Dec 2016 00:00 MST -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 003: ID 0781:5598 SanDisk Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b374 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
video                  40960  2 i915,acer_wmi
wmi                    20480  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp3s0    Link encap:Ethernet  HWaddr 4c:eb:42:05:24:18  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a5a3:b5ad:1416:deaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1338875 (1.3 MB)  TX bytes:34742 (34.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlp3s0    IEEE 802.11bgn  ESSID:"dd-wrt24"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 48:F8:B3:F1:4C:9A   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:137   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       909     1  0 09:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 1030 [Rainbow Peak] (Centrino Wireless-N 1030 BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-53-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         4C:EB:42:05:24:18
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     dd-wrt24 1
GENERAL.CON-UUID:                       2d94da32-e886-45b5-ac87-87eb0153ae58
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2d94da32-e886-45b5-ac87-87eb0153ae58 | dd-wrt24 1
IP4.ADDRESS[1]:                         192.168.1.148/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.148
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = Home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1481387681
DHCP4.OPTION[22]:                       host_name = emulationstation
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::a5a3:b5ad:1416:deaf/64
IP6.GATEWAY:                            


SSID                            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
CenturyLink3327                 10:5F:06:8E:BD:C5  Infra  1     2412 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
dd-wrt24                        48:F8:B3:F1:4C:9A  Infra  2     2417 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
CenturyLink7077                 5C:F4:AB:2B:84:F1  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
WelcometoHogwarts               20:76:00:5A:AF:A5  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
26F77E                          A4:2B:8C:26:F7:7E  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
Peters61                        20:76:00:17:6E:68  Infra  3     2422 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
DIRECT-D2-HP ENVY 5660 series   FC:3F:DB:16:99:D3  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
delock_24                       40:8B:07:C0:48:35  Infra  4     2427 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
Don Cramer's Network            28:CF:DA:BA:23:69  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
Don Cramer's Guest Network      2A:CF:DA:BA:23:6A  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
2DDEAD                          5C:8F:E0:2D:DE:AD  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
Chewy                           14:91:82:40:C5:5A  Infra  8     2447 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
CenturyLink2556                 20:76:00:87:A0:95  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
HP-Print-44-Photosmart 7520     88:51:FB:FD:CD:44  Infra  3     2422 MHz  54 Mbit/s  32      &#9602;&#9604;__  --         no        
HP-Print-64-Officejet Pro 8600  2C:41:38:52:9E:64  Infra  8     2447 MHz  54 Mbit/s  30      &#9602;___  --         no        
Fernandez                       50:6A:03:D2:AB:26  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
CenturyLink0248                 E8:37:7A:E2:EA:E1  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
DIRECT-60-HP ENVY 5540 series   30:8D:99:7E:FC:61  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
D9B20F                          10:0D:7F:D9:B2:0F  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
CenturyLink6178                 1C:74:0D:6A:08:FD  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
NETGEAR25-GN                    84:1B:5E:3A:A2:2A  Infra  7     2442 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        
HP-Print-95-ENVY 4500 series    9C:B6:54:9C:DC:95  Infra  9     2452 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        
591F87                          5C:8F:E0:59:1F:87  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
HP-Print-C3-ENVY 4500 series    D0:BF:9C:A8:C1:C3  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
Supersipe old                   B0:7F:B9:B6:34:5E  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        

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

##### NetworkManager profiles ###########




```

---

### Post by thesuffering on 2016-12-28
[COLOR=#2C2C2C][FONT=&quot]found the answer to this....electrical tape...[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&quot]see post #50[/FONT][/COLOR]
[https://communities.intel.com/thread/31247?start=45&tstart=0](https://communities.intel.com/thread/31247?start=45&tstart=0)

[COLOR=#2C2C2C][FONT=&quot]turns out if you just cover a certain pin, it enables bluetooth. Its working now for me.[/FONT][/COLOR]

---

