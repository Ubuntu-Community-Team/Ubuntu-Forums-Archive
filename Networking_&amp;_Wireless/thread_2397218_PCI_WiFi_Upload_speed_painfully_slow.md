---
title: "PCI WiFi Upload speed painfully slow"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by salseng on 2018-07-26
I am running a Core2Duo processor with Gigabyte G41 Combo motherboard. I connect to wifi using a Tenda PCI wifi card. Download speed (around 74Mbps in speedtest) while the upload speed is painfully slow (never crosses 1Mbps mark). When speedtest is run on a MacBook Air, everything seems to be fine for the same server. I really need this to be fixed.

---

### Post by praseodym on 2018-07-28
Please run the wireless script from the sticky thread and show the outputs

---

### Post by salseng on 2018-08-02
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs

Here it is (sorry, I had replied, but as I am new here, I can't find my own reply)




]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n########## wireless info START ##########\n\n"


########## wireless info START ##########


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*/\1/p')
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 03 Aug 2018 00:31 +06 +0600


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 03 Aug 2018 00:00 +06 +0600


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 10 Jan 2018 20:04 UTC +0000
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### release ###########################\n\n"


##### release ###########################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ lsb_release -idrc
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### kernel ############################\n\n"


##### kernel ############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ uname -srvmpio
Linux 4.15.0-29-generic #31~16.04.1-Ubuntu SMP Wed Jul 18 08:54:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ echo


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### desktop ###########################\n\n"


##### desktop ###########################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Ubuntu
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### lspci #############################\n\n"


##### lspci #############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
	Subsystem: Gigabyte Technology Co., Ltd AR8151 v1.0 Gigabit Ethernet [1458:e000]
	Kernel driver in use: atl1c


04:00.0 Network controller [0280]: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]
	Subsystem: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]
	Kernel driver in use: rt2800pci
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### lsusb #############################\n\n"


##### lsusb #############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ lsusb
Bus 001 Device 004: ID 03f0:ac11 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 09da:77fb A4Tech Co., Ltd. 
Bus 005 Device 009: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0480:a202 Toshiba America Inc Canvio Basics HDD
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### PCMCIA card info ##################\n\n"


##### PCMCIA card info ##################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### rfkill ############################\n\n"


##### rfkill ############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### lsmod #############################\n\n"


##### lsmod #############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$) 
")
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ echo "$LSMOD"
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              622592  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### interfaces ########################\n\n"


##### interfaces ########################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ for IFACESFILE in $(find /etc/network/interfaces{,.d} -type f 2> /dev/null | sort); do
>     IFACESFLCNT=$(sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' $IFACESFILE)
>     if [ -n "$IFACESFLCNT" ]; then
> printf "[%s]\n%s\n\n" "$IFACESFILE" "$IFACESFLCNT"
>     fi
> done
[/etc/network/interfaces]
auto lo
iface lo inet loopback


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### ifconfig ##########################\n\n"


##### ifconfig ##########################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -x /sbin/ifconfig ]; then
>     IFCONFIG=$(ifconfig -a)
> else
>     IFCONFIG=$(ip address show)
> fi
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ echo "$IFCONFIG"
enp3s0    Link encap:Ethernet  HWaddr 1c:6f:65:76:79:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:284358 (284.3 KB)  TX bytes:284358 (284.3 KB)


wlp4s0    Link encap:Ethernet  HWaddr c8:3a:35:c0:00:f3  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::91b2:d4d9:3953:afa0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:157749658 (157.7 MB)  TX bytes:17446817 (17.4 MB)
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ IFCONFIG=$(sed -n '1h; 1!H; ${g;s/\n /\\ /g;p}' <<< "$IFCONFIG")
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p; s#^[0-9]\+: \([^ :]\+\):.* li 
nk/ether.*#\1#p' <<< "$IFCONFIG"))
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if (( ${#IFACESETH[@]} > 0 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### iwconfig ##########################\n\n"


##### iwconfig ##########################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ iwconfig
lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp4s0    IEEE 802.11  ESSID:"GS Residence"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: E8:DE:27:49:96:52   
          Bit Rate=81 Mb/s   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:124  Invalid misc:893   Missed beacon:0


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### route #############################\n\n"


##### route #############################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -x /sbin/route ]; then
>     route -n
> else
>     ip route show
> fi
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### resolv.conf #######################\n\n"


##### resolv.conf #######################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ grep -v '^#' /etc/resolv.conf
nameserver 127.0.1.1
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### network managers ##################\n\n"


##### network managers ##################


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "Installed:\n\n"
Installed:


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ for NETMGRNR in "${!NETMGRPATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
> NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
	NetworkManager
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRMATCHES// |/|}
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ NETMGRMATCHES="(${NETMGRMATCHES#|})"
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\nRunning:\n\n"


Running:


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"
root       779     1  0 Aug02 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### NetworkManager info ###############\n\n"


##### NetworkManager info ###############


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -x /usr/bin/nm-tool ]; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-manager\")."
> fi
GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3062 Wireless 802.11n 2T/2R
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.15.0-29-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         C8:3A:35:C0:00:F3
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     GS Residence 1
GENERAL.CON-UUID:                       6e1df127-0346-41e4-835b-d7121f942d3a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     81 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,4,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   54d9efad-9940-4160-aa1c-b824b47354bd | BBS-TT
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   41bfde57-87da-430e-99e7-4c05a60bafcc | BBS
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   6e1df127-0346-41e4-835b-d7121f942d3a | GS Residence 1
IP4.ADDRESS[1]:                         192.168.0.108/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1533239868
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.108
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::91b2:d4d9:3953:afa0/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v1.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         1C:6F:65:76:79:0D
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/enp3s0
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




SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
GS Residence  E8:DE:27:49:96:52  Infra  1     2412 MHz  54 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
BBS           4A:D9:E7:DB:18:5D  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
BBSBH         82:2A:A8:07:EE:91  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --         no        
BBS-TT        48:F8:B3:D3:8B:DB  Infra  9     2452 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### NetworkManager.state ##############\n\n"


##### NetworkManager.state ##############


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### NetworkManager.conf ###############\n\n"


##### NetworkManager.conf ###############


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ 
]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ printf "\n##### NetworkManager profiles ###########\n\n"


##### NetworkManager profiles ###########


]0;salseng@sengBuntu: ~[01;32msalseng@sengBuntu[00m:[01;34m~[00m$ if [ -d /etc/NetworkManager/system-connections ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDES 
UDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     ORIGIFS="$IFS"
>     IFS=$'\n'
>     for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
> 
Display all 2907 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
> 
Display all 2907 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
> 
Display all 2907 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
>     done
>     IFS="$ORIGIFS"
>     sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi
Sorry, try again.
Sorry, try again.
sudo: 2 incorrect password attempts

---

### Post by praseodym on 2018-08-02
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2.

Also deactivate the hardware encryption of the driver
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

---

### Post by salseng on 2018-08-04
> **praseodym said:**
> Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2.

Also deactivate the hardware encryption of the driver
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```


Deactivating the hardware encryption of the driver worked for me. Thank you so much.

---

### Post by praseodym on 2018-08-04
Great. Please mark the thread [SOLVED] using thread tools

---

### Post by salseng on 2018-08-06
Done, actually I was looking for the "Solved" thing, I'm new here, but enjoying. Thank you again :)

---

