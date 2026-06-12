---
title: "Wifi Connection disconnects and reconnects + Wifi is slow"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by UltimatePredator on 2016-08-06
First up sorry for the length of this post, and my newbieness, although I've been a user of lubuntu for a while, I'm still pretty new to a lot of it's inner workings. I currently have lubuntu 16.04.1 installed on a HP Compaq nc6220 laptop.

Anyway, I noticed a few months ago (quite possibly when I upgraded to 16.04, but I can't be sure to be honest) that my wifi connection has a habit of disconnecting itself then reconnecting. I also noticed that my connection is quite slow - based on speedtest.net my girlfriends laptop next to me always gets at least 10mbps download speeds, whilst I vary between 4mbps al the way through to 10mbps.

After looking at other threads here I tried to install wicd and remove network manager as I heard that can help, but made some mistakes along the way and somehow removed the ability to connect to the internet (or I just didn't know enough to fix it myself!). So I though I'd do a clean install of 16.04.1 (erased everything on the drive after backing up), but alas the same problems persist.

I went through this article here about speeding up internet on ubuntu, but none of it works for me; [https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)

Solution 1: For Slow WiFi in Atheros Wireless Network Adaptors - I don't think I have atheros based on the output  from **lshw -C network** below so doesn't apply;

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: enp16s0
       version: 11
       serial: 00:15:60:b7:6e:b0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5751m-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlp2s4
       version: 05
       serial: 00:16:6f:52:cd:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.8 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:d0400000-d0400fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

Solution 2: Disable 802.11n - Running **sudo rmmod iwlwif** results in:
```
rmmod: ERROR: Module iwlwif is not currently loaded
```

Solution 3: Fix the bug in Debian Avahi-daemon - /etc/nsswitch.conf doesn't have the problems listed (it says hosts:          files dns as it should do)

Solution 4: Disable IPv6 support - I went through the instructions and disabled IPV6 support but it didn't change the speed (is it problematic that IPv6 is now disabled?

Solution 5: Ditch default network manager and embrace Wicd - this could work but I don't know how to do it successfully without stopping my wifi from working completely!

Solution 6: More power to wireless adaptor - Running **sudo iwconfig** results in;

```
enp16s0   no wireless extensions.

lo        no wireless extensions.

wlp2s4    IEEE 802.11bg  ESSID:"waytogo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:60:64:80:04:2C   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:3A05-1AA3-BB12-E65E-7C31-4B96-2BDE-BD83   Security mode:open
          Power Management:on
          Link Quality=75/100  Signal level=-54 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:8
```

I can turn the power managment off using  **sudo iwconfig wlp2s4 power off**, but it doesn't speed up the internet, and upon reboot power management is back on (as you can see above!).

Finally, in case this helps, here is the output from running the wireless info script:

```

########## wireless info START ##########

Report from: 06 Aug 2016 23:19 NZST +1200

Booted last: 06 Aug 2016 00:00 NZST +1200

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################


02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company nc6120/nx8220/nw8240 [103c:12f6]
    Kernel driver in use: ipw2200

10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
    Subsystem: Hewlett-Packard Company NetXtreme BCM5751M Gigabit Ethernet PCI Express [103c:0944]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ipw2200               143360  0
libipw                 36864  1 ipw2200
cfg80211              499712  2 libipw,ipw2200
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp16s0   Link encap:Ethernet  HWaddr 00:15:60:b7:6e:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlp2s4    Link encap:Ethernet  HWaddr 00:16:6f:52:cd:6f  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f8e7:eca6:a4c4:4920/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13453768 (13.4 MB)  TX bytes:1956262 (1.9 MB)

##### iwconfig ##########################

enp16s0   no wireless extensions.

lo        no wireless extensions.

wlp2s4    IEEE 802.11bg  ESSID:"waytogo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:60:64:80:04:2C   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/100  Signal level=-48 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:31


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s4
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s4

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2198     1  0 22:37 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s4
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 2200BG [Calexico2] Network Connection (nc6120/nx8220/nw8240)
GENERAL.DRIVER:                         ipw2200
GENERAL.DRIVER-VERSION:                 1.2.2kmprq
GENERAL.FIRMWARE-VERSION:               ABG:9.0.5.27 (Dec 12 2007)
GENERAL.HWADDR:                         00:16:6F:52:CD:6F
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/net/wlp2s4
GENERAL.IP-IFACE:                       wlp2s4
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     waytogo
GENERAL.CON-UUID:                       7bba30cc-de0f-463a-96aa-f686713fea37
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7bba30cc-de0f-463a-96aa-f686713fea37 | waytogo
IP4.ADDRESS[1]:                         192.168.1.8/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1470566254
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.8
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
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
IP6.ADDRESS[1]:                         fe80::f8e7:eca6:a4c4:4920/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp16s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5751M Gigabit Ethernet PCI Express
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5751m-v3.29a
GENERAL.HWADDR:                         00:15:60:B7:6E:B0
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:10:00.0/net/enp16s0
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


SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TNCAP4172A7      A4:B1:E9:41:72:A7  Infra  11    2462 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
waytogo          00:60:64:80:04:2C  Infra  11    2462 MHz  54 Mbit/s  78      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Orcon-Wireless   78:A0:51:20:FD:FB  Infra  10    2457 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Roxburgh Queens  18:F1:45:24:9E:1D  Infra  1     2412 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
Tech_D0020719    B0:C2:87:D5:12:F4  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
BankOfNigeria    18:F1:45:2A:8D:F6  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
TNCAP5D54B5      58:98:35:5D:54:B5  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
vodafoneVMNQ     00:0E:8F:BB:B9:DC  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
TP-LINK_D4E0     F4:F2:6D:85:D4:E0  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
Marjorie         00:0E:8F:B4:9E:18  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
vodafone7T53     00:0E:8F:B3:38:02  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
Tech_D0022324    B0:C2:87:D5:1F:7E  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
SPARK-CAAZ7V     48:DB:50:78:9A:60  Infra  7     2442 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        

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

Any thoughts people? Would greatly appreciate it.

---

### Post by howefield on 2016-08-06
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by UltimatePredator on 2016-08-06
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum.

Cheers!

---

### Post by wildmanne39 on 2016-08-06
There may be a couple of thing but I would like to see the whole output the wireless script created it will tell us a lot more.
Thanks

---

### Post by UltimatePredator on 2016-08-07
No thank you for helping! Crap, didn't realise I hadn't done it properly, here it is attached!

---

### Post by wildmanne39 on 2016-08-07
It looks like you have a firmware issue.  Please download the attached file to your desktop. Right-click it and select Extract Here Then in a terminal do:
```
sudo cp Desktop/22002/* /lib/firmware
```
Reboot if it does not work post the output of:
```
dmesg | grep ipw
```
Thanks to chili555 for the firmware.

You probably should use the second firmware I uploaded it may be a newer version, I am having a computer issue and could not check the first version.

Also it shows that your firewall is blocking your connection.

---

### Post by UltimatePredator on 2016-08-08
> **Wild Man said:**
> It looks like you have a firmware issue.  Please download the attached file to your desktop. Right-click it and select Extract Here Then in a terminal do:
```
sudo cp Desktop/22002/* /lib/firmware
```
Reboot if it does not work post the output of:
```
dmesg | grep ipw
```
Thanks to chili555 for the firmware.

You probably should use the second firmware I uploaded it may be a newer version, I am having a computer issue and could not check the first version.

Also it shows that your firewall is blocking your connection.

EDIT: Just tried to do as you say, but upon trying to extract the archive it says **An error occurred while loading the archive**.

EDIT: Ignore below comment, internet just disconnected and reconnected, about to try and apply firmware now.

You won't believe it but since my first post I haven't had any problems, the speed of the internet is consistenly around 10mbps and I'm yet to have it disconnect on me. Still not 100% sure the issues are resolved so I'll keep an eye on it over the next couple of days. If the issues have righted themselves, is there anything I could have done from, and including the first post, that could have righted it?





In regards to the firewall, I simply activated it through sudo ufw enable, the output of ufw is as follows:

```
ian@ian-HP-Compaq-nc6220-PU982AW-ABU:~$  sudo ufw status verbose
[sudo] password for ian: 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

Is this wrong? Do you think I should disable the firewall? Thank you for your time.

---

### Post by UltimatePredator on 2016-08-11
Any news? Thank you.

---

