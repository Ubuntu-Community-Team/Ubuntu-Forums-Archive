---
title: "Unable to navigate on my wireless network and to change regulation"
date: 2017-02-15
forum: Networking &amp; Wireless
---

### Post by cunfusu on 2017-02-15
Hello.. I recently installed kubuntu on a refurbished laptop that cames with windows7pro
I cannot manage to have wifi working correctly.
I can connect to my network, I receive a valid ip but I'm not able to ping anything.

Initially I was thinking it was because of drivers but then I realized I could connect to the wifi network shared from my android phone without problems.
I excluded a hw failure because on windows wifi was working correctly

finally a friend suggested me that the problem could have been an incorrect setting of the regulation for wifi (i'm located in Italy right now) and he suggested to set it to 00.
That's my current situation:
```

&#10140;  ~ sudo iw reg get                                                                               
country US: DFS-FCC
        (2402 - 2472 @ 40), (N/A, 30), (N/A)
        (5170 - 5250 @ 80), (N/A, 17), (N/A)
        (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
        (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
        (5735 - 5835 @ 80), (N/A, 30), (N/A)
        (57240 - 63720 @ 2160), (N/A, 40), (N/A)

```

if i run ```
sudo iw set IT
``` or ```
sudo iw set 00
```

the regulation is changed only temporarily before returning after few seconds to US

On dmesg I can see this
```

[   18.927222] cfg80211: Regulatory domain changed to country: US
[   18.927225] cfg80211:  DFS Master region: FCC
[   18.927227] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   18.927229] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[   18.927231] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[   18.927234] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[   18.927235] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[   18.927237] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[   18.927238] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)

```

I also tried to edit the file */etc/default/crda* but no luck.

Now I don't know how and why.. but after a few changes my wireless connection is working even if configured to US but I'm pretty sure that after next reboot the problem will reappear.

last but not least here is the output of the script required to post in this section:
```

########## wireless info START ##########

Report from: 15 Feb 2017 17:05 CET +0100

Booted last: 15 Feb 2017 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

/usr/share/xsessions/plasma

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo 82579LM Gigabit Network Connection [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 5986:02d2 Acer, Inc 
Bus 001 Device 005: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 004: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

./wireless-info: line 186: pccardctl: command not found

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

./wireless-info: line 202: ifconfig: command not found

##### iwconfig ##########################

./wireless-info: line 211: iwconfig: command not found

##### route #############################

./wireless-info: line 214: route: command not found

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       967     1  0 16:14 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6205 [Taylor Peak] (Centrino Advanced-N 6205 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-62-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC address>
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
GENERAL.CONNECTION:                     goldengate
GENERAL.CON-UUID:                       fe9e6569-2215-47d0-9cdd-48a937e454d3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fe9e6569-2215-47d0-9cdd-48a937e454d3 | goldengate
IP4.ADDRESS[1]:                         192.168.1.105/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = TP-LINK
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.105
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 226800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 129600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1487430900
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc5
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::10bd:71fd:7ebf:1f5d/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
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

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
goldengate             <MAC 'goldengate' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
TP-LINK_Casa           <MAC 'TP-LINK_Casa' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
InfostradaWiFi-718527  <MAC 'InfostradaWiFi-718527' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/goldengate]] (600 root)
[connection] id=goldengate | type=wifi | permissions=user:corsair:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=goldengate
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/corsone]] (600 root)
[connection] id=corsone | type=wifi | permissions=user:corsair:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=corsone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GOLDENGATE 2]] (600 root)
[connection] id=GOLDENGATE 2 | type=wifi | permissions=user:corsair:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=GOLDENGATE 2
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

./wireless-info: line 282: iw: command not found

##### iwlist channels ###################

./wireless-info: line 293: iwlist: command not found

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'goldengate' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"goldengate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000056e7519ddf
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_Casa' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_Casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051dee38463
                    Extra: Last beacon: 5108ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_EFAC7F' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_EFAC7F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008106a6cec3
                    Extra: Last beacon: 5100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'InfostradaWiFi-718527' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"InfostradaWiFi-718527"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036d27a0767
                    Extra: Last beacon: 4908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

./wireless-info: line 324: modinfo: command not found
[iwldvm]

./wireless-info: line 324: modinfo: command not found
[mac80211]

./wireless-info: line 324: modinfo: command not found
[iwlwifi]

./wireless-info: line 324: modinfo: command not found
[cfg80211]

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############


```

how can I set the regulation parameter permanently?

---

### Post by cunfusu on 2017-02-15
As expected after reboot wifi is not working anymore
moreovere I noticed that regulation return to US when I try to connect to my network

---

### Post by chili555 on 2017-02-15
> Cell 01 - Address: <MAC 'goldengate' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"goldengate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000056e7519ddf
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKYour driver, your hardware and your Doc Chili hate hate hate TKIP.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:

```
sudo iw reg get
```
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

```
sudo iw reg set IS
```
Of course, substitute your country code if not Iceland. Set it permanently:

```
gksudo gedit /etc/default/crda
```
Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

```
REGDOMAIN=IS
```
Proofread carefully, save and close the text editor. I do not recommend setting any CRDA other than your actual location.

Next, I'd set IPv6 to Ignore in Network Manager:  [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) This example is for ethernet, but you want wireless.

After rebooting the computer and router, post back and tell us if the connectivity is improved.

PS - Did I say I hate TKIP??

---

### Post by chili555 on 2017-02-15
> ./wireless-info: line 202: ifconfig: command not foundHow on earth is ifconfig, iwconfig, iwlist, route, etc. missing? Is yours a failed install? Or what???

---

### Post by cunfusu on 2017-02-15
As I wrote on my first post I tried to set the regulation using

sudo iw reg set XX

where XX was IT or 00
In both cases this didn't work because as soon as I reconnect to my wireless network the regulations return to US :-(

and also editing  /etc/default/crda seems to have no effects even after reboot

my main problem is that currently I cannot change settings on my router because it's a tp-link something  that seems affected by a bug, web server goes down after few seconds after reboot and I cannot access the web interface or update the firmware that should fix this problem.

I think that  all the commands above are accessible only by sudoers....

---

### Post by cunfusu on 2017-02-15
I just noticed another thing.. if I first connect to another network, I have an access point in another room I can then connect to my main router even if the region remain US.
that's really weird..

---

### Post by cunfusu on 2017-02-16
I attached the output from the script with the missing commands (I had to run it with sudo)
I hope this will be helpful to discovere where is the problem

---

### Post by chili555 on 2017-02-16
> I think that all the commands above are accessible only by sudoers....Absolutely not. If simple commands like ifconfig and iwconfig are missing in your system, then you have much bigger problems than CRDA.

It also sounds like you have a faulty router. 

Until your system is operating correctly, I am not sure I have any other suggestions.

---

### Post by cunfusu on 2017-02-16
> **chili555 said:**
> Absolutely not. If simple commands like ifconfig and iwconfig are missing in your system, then you have much bigger problems than CRDA
Not so bad.. the problem was that /sbin and /usr/sbin where not in my .zshrc now they are thanks for pointing it out

---

### Post by cunfusu on 2017-02-17
So looking at the script output:
```


##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'goldengate' [AC1]>
                    [B]Channel:11
                    Frequency:2.462 GHz (Channel 11)[/B]
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"goldengate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000048d254f9f
                    Extra: Last beacon: 188ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```

my network is using the channel 11 at 2.462 GHz 

But I don't know how to read the following output.. is it this freq falling in the first range?
what are these numbers between parenthesis? 

```

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

country US: DFS-FCC
   ** (2402 - 2472 @ 40),** (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)


```

Is the following a list of supported channels? if yes mine should be supported.. or not?

```


##### iwlist channels ###################

lo        no frequency information.

enp0s25   no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          **Channel 11 : 2.462 GHz**
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          [B]Current Frequency:2.462 GHz (Channel 11)
[/B]

```

Thanks

---

### Post by chili555 on 2017-02-17
Yes, despite any issues with CRDA. your device and router both work well on channel 11. Your device doesn't work well at all with auto WPA/WPA2-TKIP.>  the problem was that /sbin and /usr/sbin where not in my .zshrc now they are thanks for pointing it outPart of me wants to know how you managed that; part of me is horrified at the possible answers!

---

### Post by cunfusu on 2017-02-17
Ok finally I manage to update firmware on my router. I took me several attempts and I had to reset several times the router but now it seems to work correctly.

I changed authentication method (byebye tkip) and I changed channel.

Result? I'm still unable to reach Internet using the wireless interface of my router.

Attached the output of the script wireless-info

---

### Post by chili555 on 2017-02-17
Please detach the ethernet, reboot and let us see:```
ifconfig
route -n
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by cunfusu on 2017-02-17
after first reboot wifi connection was working correctly but not after second..
so here is the output, as you can see I cannot even ping  the router..

```
&#10140;  ~ ifconfig
enp0s25   Link encap:Ethernet  HWaddr 3c:97:0e:86:a6:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:68526 (68.5 KB)  TX bytes:68526 (68.5 KB)

wlp3s0    Link encap:Ethernet  HWaddr 84:3a:4b:ae:f2:4a  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::10bd:71fd:7ebf:1f5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2916 (2.9 KB)  TX bytes:43887 (43.8 KB)

&#10140;  ~ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
&#10140;  ~ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

&#10140;  ~ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

&#10140;  ~ ping -c3 www.ubuntu.com
ping: unknown host www.ubuntu.com
```

---

### Post by chili555 on 2017-02-17
Interesting. Your ifconfig and route look great but nothing works. Let's dig deeper.```
cat /var/log/syslog | grep -e etwork -e wlp | tail -n20
```

---

### Post by cunfusu on 2017-02-18
```
&#10140;  ~ cat /var/log/syslog | grep -e etwork -e wlp | tail -n20
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1763] device (wlp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1769] device (wlp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1772] device (wlp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1774] manager: NetworkManager state is now CONNECTED_LOCAL
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1893] manager: NetworkManager state is now CONNECTED_GLOBAL
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1895] policy: set 'goldengate' (wlp3s0) as default for IPv4 routing and DNS
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1897] dns-plugin[0x1ad7560]: starting dnsmasq...
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.1915] dns-mgr: Writing DNS information to /sbin/resolvconf
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.3020] device (wlp3s0): Activation: successful, device activated.
Feb 18 08:14:27 dude NetworkManager[944]: <info>  [1487402067.3094] dnsmasq[0x1ad7560]: dnsmasq appeared as :1.51
Feb 18 08:14:27 dude systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/2
Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/2
Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/2
Feb 18 08:14:27 dude systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 18 08:14:27 dude nm-dispatcher: req:1 'up' [wlp3s0]: new request (1 scripts)
Feb 18 08:14:27 dude nm-dispatcher: req:1 'up' [wlp3s0]: start running ordered scripts...
Feb 18 08:14:28 dude avahi-daemon[946]: Joining mDNS multicast group ohttps://web.whatsapp.com/n interface wlp3s0.IPv6 with address fe80::10bd:71fd:7ebf:1f5d.
Feb 18 08:14:28 dude avahi-daemon[946]: New relevant interface wlp3s0.IPv6 for mDNS.
Feb 18 08:14:28 dude avahi-daemon[946]: Registering new address record for fe80::10bd:71fd:7ebf:1f5d on wlp3s0.*.
```

---

### Post by chili555 on 2017-02-18
This is interesting:> Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/2
Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/2
Feb 18 08:14:27 dude whoopsie[948]: [08:14:27] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/2Whoopsie is:> It's the "Ubuntu Error Reporting" daemon, and is installed by default in both desktop/server installations.
When something crashes, whoopsie does two things:
Collects the crash report generated by Apport and
Can send them to Ubuntu/Canonical (specifically to [https://daisy.ubuntu.com](https://daisy.ubuntu.com) :)
[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

We'd love to see and fix whatever crashed.```
cat /var/log/syslog | grep whoopsie
cat /var/log/apport
```The log actually looks like the wireless connected correctly. Can you give us another when it does not?

---

### Post by cunfusu on 2017-02-20
> **chili555 said:**
> The log actually looks like the wireless connected correctly. Can you give us another when it does not?

I can ensure that when I took the log, I was not connected via ethernet but ony via wifi.. despite I was connected and I get the address and all the rest I'm not able to navigate and I cannot even ping my gateway.


anyway.. this is the log you asked:
```
&#10140;  ~ cat /var/log/syslog | grep whoopsie
Feb 20 08:50:02 dude whoopsie[875]: [08:50:02] offline
Feb 20 09:39:29 dude whoopsie[970]: [09:39:29] Using lock path: /var/lock/whoopsie/lock
Feb 20 09:39:29 dude whoopsie[970]: [09:39:29] Could not get the Network Manager state:
Feb 20 09:39:29 dude whoopsie[970]: [09:39:29] GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] offline
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] Cannot reach: https://daisy.ubuntu.com
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 20 09:39:32 dude whoopsie[970]: [09:39:32] online
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] offline
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] online
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] offline
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/4
Feb 20 09:52:23 dude whoopsie[970]: [09:52:23] online
&#10140;  ~ cat /var/log/apport
cat: /var/log/apport: No such file or directory
&#10140;  ~ cat /var/log/apport.log
&#10140;  ~ cat /var/log/apport.log.1
ERROR: apport (pid 14513) Sun Feb 19 22:44:39 2017: another apport instance is already running, aborting
ERROR: apport (pid 14510) Sun Feb 19 22:44:39 2017: called for pid 1569, signal 11, core limit 0
ERROR: apport (pid 14510) Sun Feb 19 22:44:39 2017: executable: /usr/bin/kwin_x11 (command line "kwin_x11 -session 1064756465000148708218300000031410001_1487429912_655744")
ERROR: apport (pid 14510) Sun Feb 19 22:44:39 2017: gdbus call failed, cannot determine running session: [Errno 2] No such file or directory: '/usr/bin/gdbus'
ERROR: apport (pid 14510) Sun Feb 19 22:44:39 2017: apport: report /var/crash/_usr_bin_kwin_x11.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

```

---

