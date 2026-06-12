---
title: "Cannot connect to wifi properly"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by lukas26 on 2015-10-16
I am almost new to Linux and completely new to Lubuntu. I bought an used laptop and removed the Windows XP system and installed Lubuntu 15.04. It works very well, but it cannot connect to wifi properly what means, that it connects after boot but disconnects immediately and cannot connecr again.

I read something about missing drivers, but nothing helped. The problem is, that I do not have access to internet apart from this wifi and cannot install packages or something which requires internet.

Has anyone an idea how to fix this?

Thanks, Lukas

---

### Post by Hadaka on 2015-10-16
Hi,looks like we may have to use the magic,smoke and mirrors method
open a terminal ctrl/atl/t and then copy and paste the commands one at a time,
```
lspci -n | awk '/0280/ {print$3}'
lsmod | grep mac80211
rfkill list all | grep yes
```
post the output

---

### Post by lukas26 on 2015-10-17
Thank you for the quick response.

Here is the output:
```

lspci -n | awk '/0280/ {print$3}'
1814:0302


_____________________________________________


lsmod | grep mac80211
mac80211              626688  2 rt2x00lib,rt2x00pci
cfg80211              462848  2 mac80211,rt2x00lib


_____________________________________________


rfkill list all | grep yes
	Hard blocked: yes

```

Hard blocked: yes sounds problematic :)

---

### Post by Hadaka on 2015-10-17
hi , yes it is..Hardblocked is usually the result of a physical switch being in the off position.
look around on your computer find it, turn it on.
also you may have a keyboard wifi switch, as in fn..+ ?
Dell it is fn f2. What is the exact model and type of your computer??

---

### Post by lukas26 on 2015-10-18
Thank you for help. FN+F2 is working and after a dist-upgrade and a install of the b43 driver's newer version everything is working.

---

### Post by Hadaka on 2015-10-18
Great! you are welcome,glad it's working.

---

### Post by lukas26 on 2015-10-19
I don't know what happend, but after the next restart it was the same problem as before, but the hard block is set to NO. Any other suggestions what could be the problem?

---

### Post by Hadaka on 2015-10-19
hi, well..you can remove the b43 driver as you dont have a broadcom card.
i was surprised you wifi was working. so thy this..
```
sudo apt-get remove --purge firmware-b43-installer
```
reboot..and test wireless.
*IF wireless is now working do.
```
sudo apt-get update
sudo apt-get autoremove && sudo apt-get autoclean
```

---

### Post by lukas26 on 2015-10-19
It is not working :( It is like before:
I can connect once, than it works for a couple of minutes and disconnects itself. After that I cannot connect again. That does not seems to be logical to me...

---

### Post by Hadaka on 2015-10-19
next time its working, or if you have a way via usb stick or whatever..
please do and post..
```
lspic -nnk | grep -iA2 net
lsmod
cat /etc/modules
```
it doesnt have to be connected to the internet to get these results
but you need to find a way to post them
thanks.

---

### Post by lukas26 on 2015-10-19
The output:

```

lspci -nnk | grep -iA2 net

09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: NEC Corporation Device [1033:c026]
    Kernel driver in use: 8139too
09:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
    Subsystem: Device [18e8:6194]
    Kernel driver in use: rt61pci

```

```

lsmod

Module                  Size  Used by
ctr                    16384  0 
ccm                    20480  0 
arc4                   16384  2 
rt61pci                32768  0 
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              49152  3 rt61pci,rt2x00pci,rt2x00mmio
snd_hda_codec_realtek    73728  1 
mac80211              626688  2 rt2x00lib,rt2x00pci
radeon               1429504  2 
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
snd_hda_intel          32768  1 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
cfg80211              462848  2 mac80211,rt2x00lib
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
eeprom_93cx6           16384  1 rt61pci
snd_seq_midi           16384  0 
crc_itu_t              16384  1 rt61pci
snd_seq_midi_event     16384  1 snd_seq_midi
ttm                    86016  1 radeon
snd_rawmidi            28672  1 snd_seq_midi
drm_kms_helper        106496  1 radeon
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm                   286720  5 ttm,drm_kms_helper,radeon
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
i2c_algo_bit           16384  1 radeon
snd                    69632  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0 
coretemp               16384  0 
serio_raw              16384  0 
soundcore              16384  2 snd,snd_hda_codec
shpchp                 32768  0 
i2c_piix4              20480  0 
video                  20480  0 
ati_agp                16384  0 
8250_fintek            16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                40960  3 lp,ppdev,parport_pc
autofs4                40960  2 
pata_acpi              16384  0 
8139too                32768  0 
8139cp                 28672  0 
psmouse               106496  0 
mii                    16384  2 8139cp,8139too
pata_atiixp            16384  2 

```



The last file is apart from 4 comment lines empty. Wrong, is'nt it? There should be an autoloaded kernel?

---

### Post by Hadaka on 2015-10-19
Hi, your wifi driver is...RT61PCI..
sooo..let's do this. The file in /etc/modules
you say ,,,isnt there. or it is empty..here is mine..
```
hadaka@noc:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


```
notice i just have one module,,lp...which is I "think"  for line printer....who knows?
so COPY and paste this command,,
```
echo -e "lp\nrt61pci" | sudo tee -a /etc/modules
```
then verify that it was written..
```
cat /etc/modules
```
then remove the wired cable if it is attached,,,reboot and test wireless
*If you get online..you REALLY need to do..
```
sudo apt-get update && sudo apt-get upgrade
```
also please do..
```
modinfo rt61pci
```
one of the output lines should say..
```
alias:          pci:v0000[COLOR=#ff0000]1814[/COLOR]d0000[COLOR=#ff0000]0302[/COLOR]sv*sd*bc*sc*i*
```
verify that it does,
```
ALSO: Please learn and use CODE TAGS  ->http://ubuntuforums.org/showthread.php?p=12776168#post12776168
```

good luck

---

### Post by lukas26 on 2015-10-19
I run all the statements as you said and the modules file looks the way you said and the modjnfo statement gives me the correct line. The apt update worked but during the upgrade it got disconnected. in the end, it does not work at all :(

---

### Post by Hadaka on 2015-10-19
Hi, not having a solid wired access to load your updates is not
ideal. Those updates really need to be error free. Try to borrow
a solid connection and run them. also a full look at you system
would be nice,,go here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
follow directions and post the wireless-info.txt file that will be created in you
home directory, mean time. please post this,,,
```
cat /etc/modules
```
thanks.

---

### Post by lukas26 on 2015-10-20
The wireless-info.txt content is:

```


########## wireless info START ##########

Report from: 20 Oct 2015 18:47 BST +0100

Booted last: 20 Oct 2015 18:42 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: NEC Corporation Device [1033:c026]
    Kernel driver in use: 8139too

09:04.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
    Subsystem: Device [18e8:6194]
    Kernel driver in use: rt61pci

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt61pci                32768  0 
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              49152  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              626688  2 rt2x00lib,rt2x00pci
cfg80211              462848  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt61pci
crc_itu_t              16384  1 rt61pci

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.14.120  Bcast:192.168.14.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:222 errors:0 dropped:1 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71462 (71.4 KB)  TX bytes:33762 (33.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Bethany"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'Bethany' [AC1]>   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:37  Invalid misc:1840   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.14.254  0.0.0.0         UG    1024   0        0 wlan0
192.168.14.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       505     1  0 18:43 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT2561/RT61 rev B 802.11g
GENERAL.DRIVER:                         rt61pci
GENERAL.DRIVER-VERSION:                 3.19.0-15-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:09:04.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Bethany
GENERAL.CON-UUID:                       2678eb29-92df-4c85-a821-f11591c2fe31
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     11 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2678eb29-92df-4c85-a821-f11591c2fe31 | Bethany
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.14.120/24, gw = 192.168.14.254
IP4.DNS[1]:                             192.168.14.254
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_netbios_scope = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        host_name = lukasDev
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1445449499
DHCP4.OPTION[10]:                       domain_name = home
DHCP4.OPTION[11]:                       next_server = 192.168.14.254
DHCP4.OPTION[12]:                       broadcast_address = 192.168.14.255
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       routers = 192.168.14.254
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       ip_address = 192.168.14.120
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       requested_domain_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.14.254
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       network_number = 192.168.14.0
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.14.254
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:09:02.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
BTHub4-GCR2      <MAC 'BTHub4-GCR2' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2         no        
BTWifi-X         <MAC 'BTWifi-X' [AC4]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
TALKTALK8EDE3E   <MAC 'TALKTALK8EDE3E' [AN3]>  Infra  9     2452 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2         no        
BTWifi-with-FON  <MAC 'BTWifi-with-FON' [AC3]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  --                no        
BTWiFi-with-FON  <MAC 'BTWiFi-with-FON' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --                no        
BTWiFi-with-FON  <MAC 'BTWiFi-with-FON' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --                no        
Bethany          <MAC 'Bethany' [AC1]>  Infra  4     2427 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA1 WPA2         yes     * 
BTHub3-6W3Z      <MAC 'BTHub3-6W3Z' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2         no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bethany]] (600 root)
[connection] id=Bethany | type=wifi | permissions=user:lukas:;
[wifi] ssid=Bethany | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

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
          Current Frequency=2.427 GHz (Channel 4)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Bethany' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Bethany"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c9e95f04c0
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTHub4-GCR2' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-GCR2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8004697dd663457e
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8004697dd6632168
                    Extra: Last beacon: 24ms ago
          Cell 04 - Address: <MAC 'BTWifi-X' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8004697dd662cd29
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[rt61pci]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FE55283B9821614A74CA3E3
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00pci]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        9B:23:C1:1A:9A:02:C7:1E:89:32:8F:2A:B2:1D:0A:23:AF:16:D7:ED
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt61pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rt61pci

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0302 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   26.100377] 8139too 0000:09:02.0 eth0: link down
[   26.117491] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561.bin'
[   26.163060] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[  114.749421] wlan0: authenticate with <MAC 'Bethany' [AC1]>
[  114.756195] wlan0: send auth to <MAC 'Bethany' [AC1]> (try 1/3)
[  114.758313] wlan0: authenticated
[  114.760223] wlan0: associate with <MAC 'Bethany' [AC1]> (try 1/3)
[  114.762376] wlan0: RX AssocResp from <MAC 'Bethany' [AC1]> (capab=0x411 status=0 aid=2)
[  114.762464] wlan0: associated
[  133.504095] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 3 times)

########## wireless info END ############


```

And the modules file is as follows:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt61pci

```

And I run all updates

---

### Post by Hadaka on 2015-10-20
Hi, your wireless is connecting ,but your router is set to TKIP
and is most likely the reason it keeps disconnecting. If possible
it needs to be removed and set to wpa2 aes
and please COPY and paste.
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
i have no further suggestions for you, untill TKIP is changed
thanks.

---

### Post by lukas26 on 2015-10-21
I ran the statements, but I don't know how to change the routers settings.

---

### Post by Hadaka on 2015-10-21
Hi, you can access your router by typing in
192.168.14.254  in your browser.

i suggest you google your router for the manual on how to configure it.

also..please post the output of,
```
sudo iw reg get
```
thanks

---

### Post by lukas26 on 2015-10-22
The output is as follows:

```

country IN: DFS-JP
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 20), (N/A)

```

I cannot change the router settings, because I am not the administrator and there is no chance to get access...

---

### Post by Hadaka on 2015-10-22
Thanks, please do..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
then post..
```
sudo iw reg get
```
thanks.

---

