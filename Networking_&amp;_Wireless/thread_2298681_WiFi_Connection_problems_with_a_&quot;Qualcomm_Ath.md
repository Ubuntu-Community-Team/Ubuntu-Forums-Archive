---
title: "WiFi Connection problems with a &quot;Qualcomm Atheros AR9485 Wireless Network Adapter&quot;"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by nickshears on 2015-10-13
I'm quite new to Ubuntu, and I have done a lot of research to try and fix this problem, but I'm having no luck. 

The wireless network adapter that i'm using is "Qualcomm Atheros AR9485 Wireless Network Adapter"

I am managing to have a stable WiFi connection for around 20 minutes or so, and after which it just simply stops working, and the only thing I can do to get connected again is by restarting the laptop. Disabling and re-enabling WiFi or networking has no effect.

Is there any kind of command that I can use before and after the problem appears to try and troubleshoot this?

Any advice would be massively appreciated.

---

### Post by nickshears on 2015-10-13
After the wireless disconnects and I can no longer scan for any networks, if I run the following command "Dmesg" I receive these errors:

```
ath: phy0: Failed to wakeup in 500us
ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
```

---

### Post by jeremy31 on 2015-10-13
It could be an issue with power management, open a terminal window(CTRL + t) and enter
```
iwconfig
```

Post the results

---

### Post by nickshears on 2015-10-13
Thanks for the reply! here's the results:

```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by jeremy31 on 2015-10-13
What version of Ubuntu, if you are using 15.04, I would suggest trying 14.04.  It may be a kernel regression from a bug that was fixed over 2 years ago

---

### Post by nickshears on 2015-10-14
Thanks for the suggestion, I did read about this somewhere actually, and I'm using Ubuntu version 14.04 so I'm surprised this is an issue. Anything else that you could suggest I do?

---

### Post by jeremy31 on 2015-10-14
What kernel? ```
uname -a
``` you could try ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
``` then reboot

---

### Post by nickshears on 2015-10-15
Kernel

```
Linux nick-X550CA 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I'll give the nohwcrypt solution a go now, thanks.

I'm not sure if I'm just having bad luck with network adapters on Linux, or if there is some underlying issue which is affecting all the wireless networking, but I have a TP-Link TL-WN725N wireless adapter which is also having problems. It doesn't disable until a reboot like the onboard Realtek adapter, but it is just generally very unstable, it permanently stays connected to the router, but there will be no internet connection for 4-5 minutes until it starts receiving data again.

Very frustrating, do you think there could possibly be some kind of driver conflict between the two? Or are these two adapters known for having issues with Linux/Ubuntu? Thanks a lot for your help so far :) [COLOR=#000000][FONT=Ubuntu Mono]


[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-10-15
I have the Atheros AR9485 in a Lenovo and it works well as long as I have the wifi encryption on the router set to WPA2 only.

Put the TP Link in and post the result of ```
lsusb
``` as there might be a fix

---

### Post by nickshears on 2015-10-15
```
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 13d3:5188 IMC Networks 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 010: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

The result of "lsusb". The TP adapter is detected as a Realtek device which is strange.

---

### Post by jeremy31 on 2015-10-15
This should work for the TP Link ```
sudo apt-get install linux-headers-$(uname -r) git build-essential
git clone https://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo modprobe 8188eu
```

---

### Post by nickshears on 2015-10-16
Thanks for that potential solution. Been trying it out for an hour or so, the loss of connection appears to be less frequent, but it's still happening from time to time unfortunately - I still have to re-enable WiFi for the connection to come back. 

When the loss of internet occurs, are there any diagnostic commands I can run to check to see exactly where the problem is?

---

### Post by jeremy31 on 2015-10-16
You could check ```
dmesg | tail
``` or ```
cat /var/log/syslog | tail
```

It might be worth checking the regulatory setting
```
iw reg get
```

If it matches your country you should be ok, if it doesn't check [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) to find your two letter country code and set it with
```
sudo if reg set US
```

Replace US with your own if you aren't in the US

---

### Post by nickshears on 2015-10-16
Thanks for the tips, I'll run these soon. Earlier today I bought another new wireless adapter just because I thought it would be a quicker and simpler solution to all of this, as I'm trying to get this fixed asap - this is my work laptop. Unfortunately the issues persist even with another adapter, so in total, that is now 3 network adapters that are constantly disconnecting over the wireless. 

I think there has to be something very wrong going on here that's not adapter specific. Any chance there could be some kind of conflicts between the drivers or something like that? It's really weird.

---

### Post by jeremy31 on 2015-10-16
You could run the wireless script from the sticky post "Before posting in Networking and Wireless" and post the results

---

### Post by nickshears on 2015-10-21
Hey, Im still having issues with networking capabilities. Ive completely reinstalled Ubuntu, removed Ubuntu 14 and installed 15 on a brand new format.

The 2 network adapters that Im using cant even connect to any wireless router now. Heres the result of the network diagnostic script, would massively appreciate any advice. 

```

########## wireless info START ##########

Report from: 21 Oct 2015 11:20 BST +0100

Booted last: 21 Oct 2015 11:12 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:1186]
    Kernel driver in use: ath9k

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 13d3:5188 IMC Networks 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8188eu               471040  0 
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              724992  1 ath9k
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  1 asus_wmi
video                  20480  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16901216 (16.9 MB)  TX bytes:2045045 (2.0 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       625     1  0 11:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       789fcf40-7b37-4b8b-a702-577a98eddecd
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   789fcf40-7b37-4b8b-a702-577a98eddecd | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.10/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.10
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1445508786
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:30:30:32:33:34:38:5:f:4c:4b:30:39:32:35:32:44:50:32:37:30:31:32:38:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 3.19.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6ae7c64c-1605-47bc-89c2-4fc7bf193376 | Livebox-de66
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

GENERAL.DEVICE:                         wlan1
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlan1
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Livebox-de66            <MAC 'Livebox-de66' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
Livebox-AE66            <MAC 'Livebox-AE66' [AC19]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Livebox-DC70            <MAC 'Livebox-DC70' [AC21]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
freebox_JUVDVY          <MAC 'freebox_JUVDVY' [AC3]>  Infra  3     2422 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1         no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AC24]>  Infra  13    2472 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X  no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AC5]>  Infra  3     2422 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X  no        
Freebox-5EC783          <MAC 'Freebox-5EC783' [AC22]>  Infra  13    2472 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AC7]>  Infra  5     2432 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AC20]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X  no        
freebox_DYOVSH          <MAC 'freebox_DYOVSH' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1         no        
Livebox-99fc            <MAC 'Livebox-99fc' [AC14]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2    no        
ITO                     <MAC 'ITO' [AC8]>  Infra  5     2432 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
ITOOOOOO                <MAC 'ITOOOOOO' [AC9]>  Infra  5     2432 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
Bbox-D7F09F             <MAC 'Bbox-D7F09F' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        
Livebox-cb02            <MAC 'Livebox-cb02' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2    no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AN16]>  Infra  2     2417 MHz  54 Mbit/s  15      &#9602;___  WPA2 802.1X  no        
CriValBen               <MAC 'CriValBen' [AN17]>  Infra  2     2417 MHz  54 Mbit/s  14      &#9602;___  WEP          no        
orange                  <MAC 'orange' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
orange                  <MAC 'orange' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
FreeWifi                <MAC 'FreeWifi' [AC23]>  Infra  13    2472 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
FreeWifi                <MAC 'FreeWifi' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  42      &#9602;&#9604;__  --           no        
FreeWifi                <MAC 'FreeWifi' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
orange                  <MAC 'orange' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
FreeWifi                <MAC 'FreeWifi' [AC6]>  Infra  5     2432 MHz  54 Mbit/s  25      &#9602;___  --           no        
FreeWifi                <MAC 'FreeWifi' [AC18]>  Infra  11    2462 MHz  54 Mbit/s  19      &#9602;___  --           no        
Bouygues Telecom Wi-Fi  <MAC 'Bouygues Telecom Wi-Fi' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  --           no        

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
freebox_JUVDVY   <MAC 'freebox_JUVDVY' [AC3]>  Infra  3     2422 MHz  16 Mbit/s  0       ____  WPA1         no        
Livebox-99fc     <MAC 'Livebox-99fc' [AC14]>  Infra  6     2437 MHz  2 Mbit/s   0       ____  WPA1 WPA2    no        
Livebox-02B6     <MAC 'Livebox-02B6' [AC31]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA1 WPA2    no        
Livebox-DC70     <MAC 'Livebox-DC70' [AC21]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  WPA1 WPA2    no        
freebox_DYOVSH   <MAC 'freebox_DYOVSH' [AC16]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  WPA1         no        
Freebox-5EC783   <MAC 'Freebox-5EC783' [AC22]>  Infra  13    2472 MHz  16 Mbit/s  0       ____  WPA2         no        
FreeWifi_secure  <MAC 'Freebox-5EC783' [AN33]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA1 802.1X  no        
FreeWifi         <MAC 'FreeWifi' [AC4]>  Infra  3     2422 MHz  16 Mbit/s  0       ____  --           no        
orange           <MAC 'FreeWifi' [AN35]>  Infra  6     2437 MHz  2 Mbit/s   0       ____  --           no        
orange           <MAC 'orange' [AC2]>  Infra  6     2437 MHz  2 Mbit/s   0       ____  --           no        
orange           <MAC 'orange' [AC11]>  Infra  6     2437 MHz  2 Mbit/s   0       ____  --           no        
orange           <MAC 'orange' [AC17]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  --           no        
FreeWifi         <MAC 'FreeWifi' [AC15]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  --           no        
FreeWifi         <MAC 'FreeWifi' [AC23]>  Infra  13    2472 MHz  16 Mbit/s  0       ____  --           no        

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

[[/etc/NetworkManager/system-connections/Bbox-925EBCE9]] (600 root)
[connection] id=Bbox-925EBCE9 | type=wifi
[wifi] ssid=Bbox-925EBCE9 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-de66]] (600 root)
[connection] id=Livebox-de66 | type=wifi
[wifi] ssid=Livebox-de66 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi
[wifi] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-de66 1]] (600 root)
[connection] id=Livebox-de66 1 | type=wifi
[wifi] ssid=Livebox-de66 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

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
wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      5   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.432 GHz (Channel 5)
      14   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      19   APs on   Frequency:2.462 GHz (Channel 11)
      9   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Livebox-de66' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Livebox-de66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000390a8aa145
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'orange' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000390a91afcb
                    Extra: Last beacon: 52ms ago
          Cell 03 - Address: <MAC 'freebox_JUVDVY' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"freebox_JUVDVY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002673d72c452
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'FreeWifi' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002673d725487
                    Extra: Last beacon: 52ms ago
          Cell 05 - Address: <MAC 'FreeWifi_secure' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002673d70fc86
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'FreeWifi' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b6053e16c
                    Extra: Last beacon: 52ms ago
          Cell 07 - Address: <MAC 'FreeWifi_secure' [AC7]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b605370c1
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'ITO' [AC8]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"ITO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b6054524a
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ITOOOOOO' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ITOOOOOO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000079ac57f4c
                    Extra: Last beacon: 708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Bbox-D7F09F' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Bbox-D7F09F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000090280ce13f
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'orange' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051cc230388
                    Extra: Last beacon: 640ms ago
          Cell 12 - Address: <MAC 'Bouygues Telecom Wi-Fi' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000090280eab17
                    Extra: Last beacon: 52ms ago
          Cell 13 - Address: <MAC 'Livebox-cb02' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Livebox-cb02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000051cc238a1b
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Livebox-99fc' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Livebox-99fc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014b2b1c70d
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'FreeWifi' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d7135ae9f1
                    Extra: Last beacon: 52ms ago
          Cell 16 - Address: <MAC 'freebox_DYOVSH' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"freebox_DYOVSH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d7135bd492
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'orange' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=320000334e2e82ba
                    Extra: Last beacon: 52ms ago
          Cell 18 - Address: <MAC 'FreeWifi' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000387115c83e8
                    Extra: Last beacon: 220ms ago
          Cell 19 - Address: <MAC 'Livebox-AE66' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Livebox-AE66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000334e2e6e89
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'FreeWifi_secure' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d7135b2383
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'Livebox-DC70' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Livebox-DC70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001594ae3917
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'Freebox-5EC783' [AC22]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Freebox-5EC783"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038a25194e3
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'FreeWifi' [AC23]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038a251427f
                    Extra: Last beacon: 52ms ago
          Cell 24 - Address: <MAC 'FreeWifi_secure' [AC24]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038a250c9d4
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 25 - Address: <MAC 'NUMERICABLE-CD58' [AC25]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"NUMERICABLE-CD58"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002e84748d364
                    Extra: Last beacon: 936ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'FreeWifi_secure' [AC26]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000286a4b5815f
                    Extra: Last beacon: 920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 27 - Address: <MAC 'SFR-7a08' [AC27]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SFR-7a08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c293c5b14
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'FreeWifi_secure' [AC28]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d0a80670
                    Extra: Last beacon: 844ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 29 - Address: <MAC 'HP-Print-52-Officejet Pro 8600' [AC29]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-52-Officejet Pro 8600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c4375171
                    Extra: Last beacon: 656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'PETRA' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"PETRA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000901aa7675b
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'Livebox-02B6' [AC31]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Livebox-02B6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004f555101d60
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'FreeWifi_secure' [AC32]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001277ff88160
                    Extra: Last beacon: 464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 33 - Address: <MAC 'TNCAP16A407' [AC33]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TNCAP16A407"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000243a2035bf
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'freebox_TJRQMK' [AC34]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"freebox_TJRQMK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000387115b9757
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 35 - Address: <MAC 'FreeWifi_secure' [AC35]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000387115c12eb
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 36 - Address: <MAC 'freebox_LGXWQM' [AC36]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"freebox_LGXWQM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d46cc3174
                    Extra: Last beacon: 208ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 37 - Address: <MAC '' [AC37]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d46cc3b4d
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 38 - Address: <MAC 'FreeWifi' [AC38]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d46cc4487
                    Extra: Last beacon: 204ms ago
          Cell 39 - Address: <MAC 'FreeWifi_secure' [AC39]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d46cc4d50
                    Extra: Last beacon: 200ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Bbox-925EBCE9' [AC1]>
                    ESSID:"Bbox-925EBCE9"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 02 - Address: <MAC 'freebox_JUVDVY' [AC3]>
                    ESSID:"freebox_JUVDVY"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 03 - Address: <MAC 'FreeWifi' [AC4]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC 'orange' [AC2]>
                    ESSID:"orange"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:130 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC 'Livebox-de66' [AC1]>
                    ESSID:"Livebox-de66"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 06 - Address: <MAC 'Livebox-99fc' [AC14]>
                    ESSID:"Livebox-99fc"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 07 - Address: <MAC 'Bouygues Telecom Wi-Fi' [AC12]>
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 08 - Address: <MAC 'Livebox-DC70' [AC21]>
                    ESSID:"Livebox-DC70"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 09 - Address: <MAC 'orange' [AC17]>
                    ESSID:"orange"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 10 - Address: <MAC 'Livebox-AE66' [AC19]>
                    ESSID:"Livebox-AE66"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 11 - Address: <MAC 'freebox_TJRQMK' [AC34]>
                    ESSID:"freebox_TJRQMK"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 12 - Address: <MAC 'FreeWifi' [AC15]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 13 - Address: <MAC 'FreeWifi' [AC13]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 14 - Address: <MAC 'FreeWifi' [AC18]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 15 - Address: <MAC 'Livebox-11BC' [AC15]>
                    ESSID:"Livebox-11BC"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 16 - Address: <MAC 'FreeWifi_secure' [AC16]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Quality:0  Signal level:0  Noise level:0
          Cell 17 - Address: <MAC 'Freebox-5EC783' [AC22]>
                    ESSID:"Freebox-5EC783"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 18 - Address: <MAC 'FreeWifi' [AC23]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0

##### module infos ######################

[r8188eu]
filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     34A0B1E82EAAF2ACEFE001B
depends:        
staging:        Y
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

[ath9k]
filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        08:41:1D:D6:68:C2:66:D5:9A:96:C6:25:B3:01:24:97:B2:35:15:42
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   10.873805] ath: phy0: Disable PLL PowerSave
[   10.880569] ath: phy0: Enable LNA combining
[   10.881825] ath: phy0: ASPM enabled: 0x42
[   10.881828] ath: EEPROM regdomain: 0x60
[   10.881829] ath: EEPROM indicates we should expect a direct regpair map
[   10.881832] ath: Country alpha2 being used: 00
[   10.881833] ath: Regpair used: 0x60
[   12.044044] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   27.570502] r8169 0000:03:00.2 eth0: link down (repeated 2 times)
[   29.262472] r8169 0000:03:00.2 eth0: link up

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-10-21
Since you reinstalled follow instructions from [http://ubuntuforums.org/showthread.php?t=2298681&p=13373517#post13373517](http://ubuntuforums.org/showthread.php?t=2298681&p=13373517#post13373517) to get the USB wifi going.  It appears one of the access points you are trying to connect to is on a very crowded channel and is using TKIP instead of WPA2 only.  
```
[COLOR=#000000][FONT=Ubuntu Mono]ell 01 - Address: <MAC 'Livebox-de66' [AC1]>[/FONT][/COLOR]                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Livebox-de66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000390a8aa145
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

Can you change the channel to 4, 7 or 8 and set the encryption to WPA2 only?

---

### Post by nickshears on 2015-10-31
Hey again, I'm done with trying other wireless adapters, the connection is so intermittent with both the TP-Link and the Netgear when connected to any router. The best connection I have is with the Atheros, it's always a stable connection and fast, but it still randomly powers off, and there's no way of getting a connection again until the computer is rebooted. Here's the output from Dmesg just now after it happened:

```
[ 2227.887263] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up[ 2228.079564] ath: phy0: Chip reset failed
[ 2228.079570] ath: phy0: Unable to reset channel, reset status -22
[ 2228.298681] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 2228.310956] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2228.946398] irq 17: nobody cared (try booting with the "irqpoll" option)
[ 2228.946406] CPU: 3 PID: 0 Comm: swapper/3 Tainted: G           OE  3.19.0-31-generic #36~14.04.1-Ubuntu
[ 2228.946409] Hardware name: ASUSTeK COMPUTER INC. X550CA/X550CA, BIOS X550CA.205 04/17/2013
[ 2228.946411]  ffff8800d5dbd0a4 ffff88011ef83e18 ffffffff817af3fb 0000000000000001
[ 2228.946415]  ffff8800d5dbd000 ffff88011ef83e48 ffffffff810ce596 ffff88011ef83e48
[ 2228.946418]  ffff8800d5dbd000 0000000000000011 0000000000000000 ffff88011ef83e98
[ 2228.946422] Call Trace:
[ 2228.946424]  <IRQ>  [<ffffffff817af3fb>] dump_stack+0x45/0x57
[ 2228.946438]  [<ffffffff810ce596>] __report_bad_irq+0x36/0xd0
[ 2228.946442]  [<ffffffff810ceacc>] note_interrupt+0x24c/0x2a0
[ 2228.946447]  [<ffffffff814c570a>] ? add_interrupt_randomness+0x3a/0x1e0
[ 2228.946451]  [<ffffffff810cc1be>] handle_irq_event_percpu+0xae/0x1a0
[ 2228.946455]  [<ffffffff810cc2f1>] handle_irq_event+0x41/0x70
[ 2228.946459]  [<ffffffff810ceef2>] handle_fasteoi_irq+0x82/0x140
[ 2228.946463]  [<ffffffff81017682>] handle_irq+0x22/0x40
[ 2228.946467]  [<ffffffff817b9d61>] do_IRQ+0x51/0xf0
[ 2228.946472]  [<ffffffff817b7b6d>] common_interrupt+0x6d/0x6d
[ 2228.946473]  <EOI>  [<ffffffff8164ff10>] ? cpuidle_enter_state+0x70/0x170
[ 2228.946482]  [<ffffffff8164fefd>] ? cpuidle_enter_state+0x5d/0x170
[ 2228.946486]  [<ffffffff816500c7>] cpuidle_enter+0x17/0x20
[ 2228.946490]  [<ffffffff810b5424>] cpu_startup_entry+0x334/0x3d0
[ 2228.946494]  [<ffffffff810e9d83>] ? clockevents_register_device+0xe3/0x140
[ 2228.946499]  [<ffffffff81048b97>] start_secondary+0x197/0x1c0
[ 2228.946501] handlers:
[ 2228.946516] [<ffffffffc0883520>] ath_isr [ath9k]
[ 2228.946518] Disabling IRQ #17
[ 2230.710768] ath: phy0: Failed to wakeup in 500us
[ 2230.722796] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 2230.722811] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
[ 2230.911473] ath: phy0: Chip reset failed



```

Will massively appreciate any help! :)

---

### Post by nknwn on 2015-10-31
I wonder if there's a firmware update available for your router?
This was suggested here:
[https://bbs.archlinux.org/viewtopic.php?id=137643](https://bbs.archlinux.org/viewtopic.php?id=137643)

Our router updates automatically so yours may be the same.
However if it is not, it might be worth doing.

---

### Post by nickshears on 2015-10-31
Thanks for your help, but this really isn't router specific. I've been using a lot of different routers lately, and the problem exists with all of them. I've tried disabling power saving for the adapter, the nocrypt solution, and I even tried out a fresh installation on Ubuntu 15 the other week. Nothing works. 

Anything else you suggest that I could try? I'm out of ideas, and have been researching this problem on the internet for weeks.

Also, do you have any suggestions for a reliable usb network adapter that's guaranteed to work with Linux/Ubuntu?

Cheers.

---

### Post by nknwn on 2015-11-01
You could try a Windows XP driver if there is one available for your device.
Here's a list of  USB wifi adapters supported by ndiswrapper:
[http://ndiswrapper.sourceforge.net/wiki/index.php/Category:USB](http://ndiswrapper.sourceforge.net/wiki/index.php/Category:USB)
and for PCI:
[http://ndiswrapper.sourceforge.net/wiki/index.php/Category:PCI](http://ndiswrapper.sourceforge.net/wiki/index.php/Category:PCI)

If you find a driver, give it a try
Here's a procedure for installing the driver using **ndisgtk**:
[http://ubuntuforums.org/showthread.php?t=2226109&p=13032905#post13032905](http://ubuntuforums.org/showthread.php?t=2226109&p=13032905#post13032905)

One other thought I had was that you might update your computer's BIOS/EFI
Of course the usual serious and dire warning apply for that.

---

### Post by jeremy31 on 2015-11-01
There was an error that said to boot using irqpoll option, so lets try it
```
sudo gedit /etc/default/grub
```

Find the line that looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Make it be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"
```

Save, exit gedit, then in terminal do 
```
sudo update-grub
```

Reboot

---

### Post by nickshears on 2015-11-05
I think it might be worth updating BIOS actually. There is some underlying issue that's affecting all wireless network capability, I bought the Asus USB-N13 which is meant to be highly compatible with Linux, plugged it in and it worked straight away, but then after 10 mins I was experiencing the loss of connection again - This happens with every single USB network adapter I try. The only one netwrok adapter that's "stable" before it shuts down all together of course, is the built in Atheros. 

Do you think it would be worth updating the BIOS even though everything worked fine when I was using a Windows OS? My laptop is an Asus x550c by the way. 

Cheers for your help and suggestions so far.

---

### Post by nickshears on 2015-11-05
> **jeremy31 said:**
> There was an error that said to boot using irqpoll option, so lets try it
```
sudo gedit /etc/default/grub
```

Find the line that looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Make it be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"
```

Save, exit gedit, then in terminal do 
```
sudo update-grub
```

Reboot

Thanks for this suggestion. I followed these steps and it did appear to have fixed the issue. The laptop was running non stop for 24 hours or so without the adapter going down - until I unplugged it from the power cable, and the same error occurred again. I'm going to continue testing this out and I'll let you know how it goes, thanks :)

---

### Post by nickshears on 2015-11-05
The irqpoll idea didn't work, it was just a lucky 24 hours, it happens from time to time where the adapter won't go down for a long time. I've now just updated the bios to the latest version - there's actually been about 7-8 bios updates since I got this laptop. Let's hope this works - otherwise this thing is going out the window ;) 

Cheers guys.

---

### Post by nickshears on 2015-11-06
> **nknwn said:**
> You could try a Windows XP driver if there is one available for your device.
Here's a list of  USB wifi adapters supported by ndiswrapper:
[http://ndiswrapper.sourceforge.net/wiki/index.php/Category:USB](http://ndiswrapper.sourceforge.net/wiki/index.php/Category:USB)
and for PCI:
[http://ndiswrapper.sourceforge.net/wiki/index.php/Category:PCI](http://ndiswrapper.sourceforge.net/wiki/index.php/Category:PCI)

If you find a driver, give it a try
Here's a procedure for installing the driver using **ndisgtk**:
[http://ubuntuforums.org/showthread.php?t=2226109&p=13032905#post13032905](http://ubuntuforums.org/showthread.php?t=2226109&p=13032905#post13032905)

One other thought I had was that you might update your computer's BIOS/EFI
Of course the usual serious and dire warning apply for that.

Problem appears to be fixed! Since updating the BIOS version everything has been working without any problems. Thanks a lot for the suggestion.

---

### Post by nknwn on 2015-11-06
Good to hear. :)

---

### Post by cartajenaa on 2015-11-06
I have the same issu with the same driver. I can't update nothing or auto disconnet my WiFi. I just see my printer wifi and any wifi of the neighbord...

And when I am online, the internet if ****ing slow.

I will try following this finals steps...

---

### Post by nickshears on 2015-11-07
> **nknwn said:**
> Good to hear. :)


Well, I spoke too soon. The adapter didn't go down for almost 2 days, and throughout that time the laptop went into hibernation, and had power cable disconnects etc.. so I assumed everything was fixed as it had never been stable for that long before. But a couple of hours ago the exact same error happened.. I really am out of ideas now. I tried with my other wireless usb adapters and they still have the same issue of working for 10 mins or so until the connection drops with them. 

Everything was working fine on Windows 7, so I'm thinking for now, as much as I'd hate to, I'm possibly going to have to go back to Windows :\

---

