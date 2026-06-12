---
title: "wifi keeps on falling and disconnecting"
date: 2017-07-21
forum: Networking &amp; Wireless
---

### Post by ardouronerous on 2017-07-21
The laptop is a Dell Inspiron E1505.

The wifi speed falls, sometimes going down to 'Unknown' and the wifi disconnects and reconnects.

I've already done some solutions that I found on Google.

I disabled 802.11n and I disabled IPv6 via the IPv6 Settings, setting the 'Method' to Ignore.
Here's my /etc/modprobe.d/iwlwifi.conf:

```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
```

But the problem keeps on reoccurring.

---

### Post by wildmanne39 on 2017-07-21
*Thread moved to **Networking & Wireless**.*

---

### Post by BenginM on 2017-07-21
Salutations!

which firmware is used,  maybe it's broken! , check with dmesg | grep iwlwifi

you should also run the wierless info script from the stick thread ..

---

### Post by ardouronerous on 2017-07-21
I tried dmesg | grep iwlwifi on the Terminal, it doesn't show anything, even tried sudo dmesg | grep iwlwifi, it still shows no input, is that a bad sign?

Wireless info script, do you mean lspci -nn -d 14e4: ?

I used that to figure out what driver to install to enable the wifi on my laptop, here's the output:

```
lspci -nn -d 14e4:
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

The driver I'm using is firmware-b43-installer.

---

### Post by vasa1 on 2017-07-21
> **ardouronerous said:**
> ...

Wireless info script, do you mean [FONT=courier new]lspci -nn -d 14e4:[/FONT]

...
No, please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) for information about the script.

---

### Post by alanmoehammad on 2017-07-21
I thing you should read this answers from [https://wireless.wiki.kernel.org/en/users/Drivers/b43](https://wireless.wiki.kernel.org/en/users/Drivers/b43)

1. Install the b43-fwcutter package.
2. Download the driver and then extract and install.
Type in the terminal "rfkill list all" to see if the wifi condition is blocked or not.
4. If it is blocked, "rfkill unblock all"
5. Try logout / restart, then browse. If lum can continue the following steps.
6. Type "sudo gedit /etc/modprobe.d/blacklist.conf", take a look at what b43 section is blacklisted, usually 'blacklist bcm43xx'
7. Try again, if not not solved can be attached again "sudo gedit / etc / network / interfaces" what content.

---

### Post by ardouronerous on 2017-07-21
I've ran the script:

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

But I'm not sure if I want to post the entire thing, I've checked the info and it contains sensitive information about my MAC and the MACs of my neighboors WIFIs.

Within wireless-info.txt, what should I copy and paste on here?

> **alanmoehammad said:**
> I thing you should read this answers from [https://wireless.wiki.kernel.org/en/users/Drivers/b43](https://wireless.wiki.kernel.org/en/users/Drivers/b43)

1. Install the b43-fwcutter package.
2. Download the driver and then extract and install.
Type in the terminal "rfkill list all" to see if the wifi condition is blocked or not.
4. If it is blocked, "rfkill unblock all"
5. Try logout / restart, then browse. If lum can continue the following steps.
6. Type "sudo gedit /etc/modprobe.d/blacklist.conf", take a look at what b43 section is blacklisted, usually 'blacklist bcm43xx'
7. Try again, if not not solved can be attached again "sudo gedit / etc / network / interfaces" what content.

Please note I'm using the WIFI right now, but the problem of disconnecting comes and goes.

I have b43-fwcutter package already, it comes as a dependency of firmware-b43-installer.

Here's the output of rfkill unblock all:
```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by vasa1 on 2017-07-21
> It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.
You apparently didn't read carefully enough ;)

---

### Post by ardouronerous on 2017-07-21
Then how come my MAC and the MACs of my neighbors are included in the file?

What I mean by MAC is that their ESSIDs are seen.

---

### Post by wildmanne39 on 2017-07-21
They should not be includes unless something strange happened, there is information in place of the numbers but it is not sensitive, if you want to pm the part to me that shows the mac address I will take a look since I am the person that started the script and insures it is maintained.
Thanks

---

### Post by wildmanne39 on 2017-07-21
That is just filler that is needed to help us help you but it is not sensitive.

---

### Post by Hadaka on 2017-07-21
Hi, the wireless script provides NO sensitive data..the ssid is seen by the world .
the wifi card is nothing more than a 2 way radio..an it broadcasts its id unless you tell it
not to. That script has been used been here and adapted to other linux forums for years
and is very careful to not display ANY sensitive data. It is your choice to post the data or not,
without it, it it very difficult to get an accurate idea of your problem. I can tell you from what
you have posted you don't have an iwlwifi driver..that is for an intel wificard...you have broadcom.
and usually very easy to fix if we have good data. 
Thanks

wildmanne39 is quick !

---

### Post by BenginM on 2017-07-21
you got us all confused in your first post by pasting  /etc/modprobe.d/iwlwifi.conf:

**iwlwifi** is the wireless driver for Intel's current wireless chips , has nothing to do with your case ..! which i thought you had 

you think someone here will crack your wifi! 

please follow instructions if you want assistance.

---

### Post by ardouronerous on 2017-07-21
> **Hadaka said:**
> Hi, the wireless script provides NO sensitive data..the ssid is seen by the world .
the wifi card is nothing more than a 2 way radio..an it broadcasts its id unless you tell it
not to. That script has been used been here and adapted to other linux forums for years
and is very careful to not display ANY sensitive data. It is your choice to post the data or not,
without it, it it very difficult to get an accurate idea of your problem. I can tell you from what
you have posted you don't have an iwlwifi driver..that is for an intel wificard...you have broadcom.
and usually very easy to fix if we have good data. 
Thanks

wildmanne39 is quick !

My login username is also shown, isn't that sensitive information?
And also, after slimming through the file, my region, country and timezone is also included which will reveal my location, isn't that sensitive information?

> **BenginM said:**
> you got us all confused in your first post by pasting  /etc/modprobe.d/iwlwifi.conf:

**iwlwifi** is the wireless driver for Intel's current wireless chips , has nothing to do with your case ..! which i thought you had 

you think someone here will crack your wifi! 

please follow instructions if you want assistance.

I was looking for a solution for the falling WIFI speeds and I discovered the iwlwifi solution.

No, I do not thing someone will crack my WIFI, but I cannot follow instructions that will reveal my timezone and region and also the wifi names of my neighbors, I owe it to them to protect their privacies.

```
########## wireless info START ##########

Report from: 21 Jul 2017 14:04 PHT +0800

Booted last: 21 Jul 2017 00:00 PHT +0800

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.10.0-27-generic #30~16.04.2-Ubuntu SMP Thu Jun 29 16:09:18 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 18f8:0f99  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_laptop            20480  0
dell_smbios            16384  1 dell_laptop
b43                   397312  0
bcma                   57344  1 b43
mac80211              700416  1 b43
cfg80211              532480  2 b43,mac80211
ssb_hcd                16384  0
ssb                    57344  3 b43,ssb_hcd,b44
video                  40960  2 dell_laptop,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:94241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126196286 (126.1 MB)  TX bytes:7471884 (7.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:516790 (516.7 KB)  TX bytes:516790 (516.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::3efa:7cb0:47b4:d1e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86418899 (86.4 MB)  TX bytes:5307102 (5.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"PROLINK_H5004NK_6A8CD"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:121  Invalid misc:334   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    600    0        0 wlan0
192.168.254.0   0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

    NetworkManager

Running:

root       660     1  0 11:39 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4311 802.11b/g WLAN (Wireless 1390 WLAN Mini-Card)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.10.0-27-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     PROLINK_H5004NK_6A8CD
GENERAL.CON-UUID:                       ca9b2f3c-1d7a-4da5-8016-a83ca032a2f1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/9
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ca9b2f3c-1d7a-4da5-8016-a83ca032a2f1 | PROLINK_H5004NK_6A8CD
IP4.ADDRESS[1]:                         192.168.254.4/24
IP4.GATEWAY:                            192.168.254.254
IP4.DNS[1]:                             192.168.254.254
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
DHCP4.OPTION[10]:                       expiry = 1500701071
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.254.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.254.4
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = domain.name
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.254.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.254.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.254.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.254.254
IP6.ADDRESS[1]:                         fe80::3efa:7cb0:47b4:d1e2/64
IP6.GATEWAY:                            fe80::9261:cff:fe26:a8cd
IP6.ROUTE[1]:                           dst = fe80::9261:cff:fe26:a8cd/128, nh = ::, mt = 600

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6400)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
sonny                  <MAC 'sonny' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       no        
SummerFibr             <MAC 'SummerFibr' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
PROLINK_H5004NK_6A8CD  <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2       yes     * 
tan_family             <MAC 'tan_family' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/PROLINK_H5004NK_6A8CD]] (600 root)
[connection] id=PROLINK_H5004NK_6A8CD | type=wifi | permissions=user:~:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=PROLINK_H5004NK_6A8CD
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Manila (based on set time zone)

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

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"PROLINK_H5004NK_6A8CD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000015897fc51
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'sonny' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"sonny"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002003114d3
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SummerFibr' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SummerFibr"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002730cd06aa
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'tan_family' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"tan_family"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f7854173
                    Extra: Last beacon: 464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/4.10.0-27-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5F955FFEA61C80144A2B433
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.10.0-27-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C645ADA4C8790A787B7C8E9
depends:        
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 

[mac80211]
filename:       /lib/modules/4.10.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.10.0-27-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 

[ssb]
filename:       /lib/modules/4.10.0-27-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-27-generic SMP mod_unload 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

apt-get update
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 1238.072870] wlan0: send auth to <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 1238.076368] wlan0: authenticated
[ 1238.080182] wlan0: associate with <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 1238.152488] wlan0: RX AssocResp from <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (capab=0x411 status=0 aid=2)
[ 1238.152923] wlan0: associated
[ 1238.152981] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1262.587820] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=28330 PROTO=2 
[ 1322.450173] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=28962 PROTO=2 
[ 1355.618809] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=172.217.20.78 DST=192.168.254.4 LEN=115 TOS=0x00 PREC=0x00 TTL=46 ID=58972 PROTO=TCP SPT=443 DPT=56688 WINDOW=188 RES=0x00 ACK PSH URGP=0 
[ 1365.057199] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=172.217.20.78 DST=192.168.254.4 LEN=115 TOS=0x00 PREC=0x00 TTL=46 ID=63653 PROTO=TCP SPT=443 DPT=56688 WINDOW=188 RES=0x00 ACK PSH URGP=0 
[ 1379.703040] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=172.217.20.78 DST=192.168.254.4 LEN=115 TOS=0x00 PREC=0x00 TTL=46 ID=7192 PROTO=TCP SPT=443 DPT=56688 WINDOW=188 RES=0x00 ACK PSH URGP=0 
[ 1382.355557] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=29648 PROTO=2 
[ 1409.034833] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=172.217.20.78 DST=192.168.254.4 LEN=115 TOS=0x00 PREC=0x00 TTL=46 ID=23241 PROTO=TCP SPT=443 DPT=56688 WINDOW=188 RES=0x00 ACK PSH URGP=0 
[ 1447.942112] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=30264 PROTO=2 
[ 1507.369879] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=30758 PROTO=2 
[ 1551.924439] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=120.28.5.8 DST=192.168.254.4 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=80 DPT=60254 WINDOW=28960 RES=0x00 ACK URGP=0  (repeated 4 times)
[ 1562.122067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31242 PROTO=2 
[ 1587.155382] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=173.194.152.106 DST=192.168.254.4 LEN=1450 TOS=0x00 PREC=0x00 TTL=55 ID=22361 PROTO=TCP SPT=443 DPT=55598 WINDOW=127 RES=0x00 ACK URGP=0 
[ 1587.157526] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=173.194.152.106 DST=192.168.254.4 LEN=1450 TOS=0x00 PREC=0x00 TTL=55 ID=24369 PROTO=TCP SPT=443 DPT=55598 WINDOW=127 RES=0x00 ACK URGP=0 
[ 1587.159270] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=173.194.152.106 DST=192.168.254.4 LEN=1450 TOS=0x00 PREC=0x00 TTL=55 ID=25438 PROTO=TCP SPT=443 DPT=55598 WINDOW=127 RES=0x00 ACK URGP=0 
[ 1587.463361] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=173.194.152.106 DST=192.168.254.4 LEN=52 TOS=0x00 PREC=0x00 TTL=55 ID=33257 PROTO=TCP SPT=443 DPT=55598 WINDOW=127 RES=0x00 ACK URGP=0 
[ 1588.032227] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 1588.032232] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 1588.032388] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1596.840203] wlan0: deauthenticating from <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3292.616192] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 3292.772253] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 3297.164088] wlan0: authenticate with <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>
[ 3297.180260] wlan0: send auth to <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 3297.181938] wlan0: authenticated
[ 3297.184207] wlan0: associate with <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 3297.187255] wlan0: RX AssocResp from <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (capab=0x411 status=0 aid=3)
[ 3297.187678] wlan0: associated
[ 3297.188346] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3328.580003] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=4460 PROTO=2 
[ 3388.490059] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=4952 PROTO=2 
[ 3432.349195] wlan0: deauthenticating from <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4238.016118] b44 ssb1:0 eth0: Link is down
[ 4243.008209] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[ 4243.008213] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[ 6233.024131] b44 ssb1:0 eth0: Link is down
[ 6278.968147] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 6279.124196] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 6281.936912] wlan0: authenticate with <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>
[ 6282.004244] wlan0: send auth to <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 6282.007396] wlan0: authenticated
[ 6282.012183] wlan0: associate with <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (try 1/3)
[ 6282.020073] wlan0: RX AssocResp from <MAC 'PROLINK_H5004NK_6A8CD' [AC1]> (capab=0x411 status=0 aid=3)
[ 6282.020493] wlan0: associated
[ 6282.020550] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6326.204760] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=31882 PROTO=2 
[ 6383.956845] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32260 PROTO=2 
[ 6443.866213] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=32912 PROTO=2 
[ 6503.775529] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=33518 PROTO=2 
[ 6563.684809] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=34092 PROTO=2 
[ 6623.594102] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=34672 PROTO=2 
[ 6683.507391] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35114 PROTO=2 
[ 6743.412845] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=35550 PROTO=2 
[ 6803.322106] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36124 PROTO=2 
[ 6863.231454] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=36708 PROTO=2 
[ 6923.140768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=37384 PROTO=2 
[ 6983.051582] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=37988 PROTO=2 
[ 7042.959395] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=38304 PROTO=2 
[ 7102.895417] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=38890 PROTO=2 
[ 7162.780313] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39478 PROTO=2 
[ 7222.687411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=40094 PROTO=2 
[ 7282.596585] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=40666 PROTO=2 
[ 7342.505905] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=41118 PROTO=2 
[ 7402.419995] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=41592 PROTO=2 
[ 7462.324476] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=42184 PROTO=2 
[ 7522.233705] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=42776 PROTO=2 
[ 7582.142986] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=43360 PROTO=2 
[ 7642.052284] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=43962 PROTO=2 
[ 7701.961610] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=44264 PROTO=2 
[ 7761.870843] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=44862 PROTO=2 
[ 7821.780086] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=45454 PROTO=2 
[ 7881.689326] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46050 PROTO=2 
[ 7941.635031] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=46662 PROTO=2 
[ 8001.542291] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47092 PROTO=2 
[ 8061.417318] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47526 PROTO=2 
[ 8121.326777] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=48094 PROTO=2 
[ 8181.236035] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=48670 PROTO=2 
[ 8241.145283] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=49290 PROTO=2 
[ 8301.056655] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=49910 PROTO=2 
[ 8360.966407] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=50216 PROTO=2 
[ 8420.873299] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=50798 PROTO=2 
[ 8480.782640] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51376 PROTO=2 
[ 8540.691939] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51966 PROTO=2 
[ 8600.601218] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=52550 PROTO=2 
[ 8660.510470] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=52980 PROTO=2 

########## wireless info END ############
```

As of right now, my wifi connection is fine, speed is at 54 Mb/s and not disconnecting.
But as I said, the problem comes and goes, sometimes I experience days without problem.

I just want to know if my WIFI card is failing, it's quite old since I bought this laptop in 2007, and if it is failing, what options do I have?

Okay, internet speed going up and down.
It goes from 24 Mb/s, 36 Mb/s, 48 Mb/s and 54 Mb/s and back down again.

What could be causing this?

---

### Post by Hadaka on 2017-07-22
Hi, 2 possibilities may be affecting your connection speed..
 1. the Country code is UNSET and using default code 00 a catch all world wide code.
    the country code determines what frequencies and channels the
    wifi card can legally use for the country it is operating in. That is
    why the region and country is on the wireless diagnostic tool we use.
To make correct please copy and paste , one line at a time to a terminal.
```
sudo iw reg set PH
sudo sed -i 's/=.*/=PH/' /etc/default/crda
```
Next the report shows exess printout of...

[UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51376 PROTO=2 
[ 8540.691939] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51966 PROTO=2 

This is cause by a router setting called..IGMP...IGMP is not used in home routers, google your router on how to disable.

any questions or concerns please let us know.
Thanks

---

### Post by ardouronerous on 2017-07-22
> **Hadaka said:**
> Hi, 2 possibilities may be affecting your connection speed..
 1. the Country code is UNSET and using default code 00 a catch all world wide code.
    the country code determines what frequencies and channels the
    wifi card can legally use for the country it is operating in. That is
    why the region and country is on the wireless diagnostic tool we use.
To make correct please copy and paste , one line at a time to a terminal.
```
sudo iw reg set PH
sudo sed -i 's/=.*/=PH/' /etc/default/crda
```


Okay, I've done the 
```
sudo iw reg set PH
sudo sed -i 's/=.*/=PH/' /etc/default/crda
```

Here's my /etc/default/crda:
```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=PH
```

I'm still experiencing Internet drops.

> **Hadaka said:**
> Next the report shows exess printout of...

[UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF2]>:<MAC  'PROLINK_H5004NK_6A8CD' [AC1]>:08:00 SRC=192.168.254.254  DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51376 PROTO=2 
[ 8540.691939] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0'  [IF2]>:<MAC 'PROLINK_H5004NK_6A8CD' [AC1]>:08:00  SRC=192.168.254.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1  ID=51966 PROTO=2 

This is cause by a router setting called..IGMP...IGMP is not used in home routers, google your router on how to disable.

any questions or concerns please let us know.
Thanks

I'm not sure if I'm allowed to edit the router settings because this router isn't owned by me, it's owned by the ISP provider.

I've checked the router settings and IGMP Snooping is set to disabled.

---

### Post by vasa1 on 2017-07-22
I really don't know much about these things, but is contention ratio an issue here? In other words, if someone else on the same network (LAN?) is doing something intensive, could your speed be affected?

---

### Post by ardouronerous on 2017-07-22
My sister is using her smartphone on the same wireless router.

---

### Post by jeremy31 on 2017-07-22
I would disable UFW and see if the wireless performs better

---

### Post by ardouronerous on 2017-07-22
> **jeremy31 said:**
> I would disable UFW and see if the wireless performs better

Isn't disabling the firewall dangerous?

---

### Post by jeremy31 on 2017-07-22
I haven't used UFW since I started using Linux.  It is just for a test, if it works you may have to adjust the UFW settings

---

### Post by ardouronerous on 2017-07-22
I disabled the Firewall, still the same, the WIFI speed goes from 48 to 36 Mb/s

But it wasn't as bad as yesterday though, yesterday the WIFI speeds goes down to 'Unknown' and it was disconnecting, as in the laptop was telling me that I was disconnected from the wireless.

That's why my first impression is that it's a hardware issue.

---

### Post by jeremy31 on 2017-07-22
Network Manager may be trying to enable wireless power save also, see if disabling it helps
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
systemctl restart network-manager.service
```

---

### Post by ardouronerous on 2017-07-22
Isn't power save already disabled? Because according to iwconfig power management is off.

```
lo        no wireless extensions. 
eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"PROLINK_H5004NK_6A8CD"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'PROLINK_H5004NK_6A8CD' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:121  Invalid misc:334   Missed beacon:0
```

---

### Post by Hadaka on 2017-07-22
Hi, I have an older Dell Inspiron as well, with the same 
Broadcom cards....b44...b43 drivers and a fiber optic wifi connection
at idol my connect speed variies between 36 and 48...once I access the
internet it jumps to the maximum it can handle...54...here are screen shots of idol and active..
[ATTACH=CONFIG]276095[/ATTACH][ATTACH=CONFIG]276096[/ATTACH]
I suspect you do not have a fiber optic connection, so what you are seeing for speeds is normal
for the older 2.4 GHz Broadcom cards. The drops and UFW errors are most likely a result of some 
router setting..connection..or ISP induced...I suspect from the wirless report it is an ISP issue..not yours.
Thanks.

---

### Post by ardouronerous on 2017-07-22
When the laptop had Windows XP, I had issues with the WIFI losing connection and the only way to resolve the issue was to repair the Internet Connection, like this:
 
 
[LIST=1]
[*]Click on **Start**.     

[*]Click on **Control Panel**.     

[*]Click on **Network Connection**.     

[*]Right-click on the *LAN or Internet connection * you wish to repair.     

[*]Click **Repair** from the drop-down menu. 
[/LIST]
[IMG]https://kb.wisc.edu/images/group1/1846/repair.gif[/IMG]
If successful you should receive a message indicating that the repair is completed. 
[IMG]https://kb.wisc.edu/images/group1/1846/complete.gif[/IMG]

And it always works in restoring my Internet connectivity, any similar steps in doing this in Lubuntu?

---

### Post by vasa1 on 2017-07-22
FWIW, here's a post from 2008 that gives an explanation of what "repair the connection" does: [https://ubuntuforums.org/showthread.php?t=931492&p=5864716#post5864716](https://ubuntuforums.org/showthread.php?t=931492&p=5864716#post5864716)

---

### Post by wildmanne39 on 2017-07-22
I just want to let you know that I did not intentionally abandon your issue, I can not help at the moment I can not open any files with libreoffice it is broken.

---

### Post by ardouronerous on 2017-07-22
> **vasa1 said:**
> FWIW, here's a post from 2008 that gives an explanation of what "repair the connection" does: [https://ubuntuforums.org/showthread.php?t=931492&p=5864716#post5864716](https://ubuntuforums.org/showthread.php?t=931492&p=5864716#post5864716)

So is
```
sudo /etc/init.d/networking restart 
```
the same thing as repair in Windows XP.

Please note this never happened in Windows XP, the disconnecting I mean, but there are occasionally issues with the WIFI that I remedied with repairing the Internet connection, but not disconnecting.

Could the disconnecting be ISP related, as in the settings imposed by the ISP on the router? I don't think so, because we've had this router for a couple of years now, we've never had issues with it before, and my main desktop is connected physically to this router, and experiences no problems.

This leads me to believe this is a either a driver issue or a hardware issue.

> **wildmanne39 said:**
> I just want to let you know that I did not  intentionally abandon your issue, I can not help at the moment I can not  open any files with libreoffice it is broken.

That's cool. :)

Right now, there's internet on my laptop, so I'm monitoring my internet connection.

It happened again.

[ATTACH=CONFIG]276107[/ATTACH]

I do believe it's an ISP issue, because even my wireless bridge didn't work in restoring my connection.

I shutdown the router and turned it on again, and now the internet is back.

But my question is, is this normal? That I get disconnected and prompted for my WIFI password?

---

