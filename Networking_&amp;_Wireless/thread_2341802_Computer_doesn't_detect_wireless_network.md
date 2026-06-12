---
title: "Computer doesn't detect wireless network"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by Don Martin on 2016-10-31
I've not had this problem before in 7 years.

My daughter's wireless network does not show up on the list of available networks when I attempt to connect.  It also does not show up on the list of networks in the wireless-info.txt file below.  It is as though my computer does not see it.

Don Martin

```
########## wireless info START ##########

Report from: 31 Oct 2016 18:03 EDT -0400

Booted last: 31 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:05 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8181]
    Kernel driver in use: rtl8192ce

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems AR8152 v2.0 Fast Ethernet [1179:fc50]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              53248  0
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        49152  1 rtl8192ce
rtlwifi                69632  3 rtl_pci,rtl8192c_common,rtl8192ce
mac80211              659456  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              499712  2 mac80211,rtlwifi
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr e8:9a:8f:f1:0b:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr 74:de:2b:40:24:08  
          inet addr:192.168.43.34  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::a167:f9d9:7e1b:41ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31713569 (31.7 MB)  TX bytes:2223402 (2.2 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Coolpad 3622A 7781"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D0:37:42:C0:78:67   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:178   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       779     1  0 16:43 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188CE 802.11b/g/n WiFi Adapter
GENERAL.DRIVER:                         rtl8192ce
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         74:DE:2B:40:24:08
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Coolpad 3622A 7781
GENERAL.CON-UUID:                       e6238218-40c0-47de-bde1-40ce3184cf78
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{31,19,12,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d21f062f-a1c4-40fe-ae3d-d5dad06e0560 | Tristana-Pitt
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   744ba079-943d-4db6-b2c8-395cc65a6fe8 | Tristana-Pitt 1
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   e6238218-40c0-47de-bde1-40ce3184cf78 | Coolpad 3622A 7781
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   b3057a74-4700-47bb-a204-2fead7a7bdfe | FiOS-A3YVA
IP4.ADDRESS[1]:                         192.168.43.34/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.34
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3029
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1679
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1477954680
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = don-Satellite-L750
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::a167:f9d9:7e1b:41ca/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8152 v2.0 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         E8:9A:8F:F1:0B:C3
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/net/enp3s0
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


SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Coolpad 3622A 7781  D0:37:42:C0:78:67  Infra  6     2437 MHz  54 Mbit/s  76      &#9602;&#9604;&#9606;_  WPA2       yes     * 
shop                00:13:10:43:3E:57  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1       no        
--                  32:86:8C:4F:7D:94  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
--                  12:86:8C:4F:7D:94  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
GreyGoose-2.4       10:86:8C:4F:7D:94  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
--                  5A:23:8C:E8:3C:34  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
HOME-3C33           58:23:8C:E8:3C:33  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        
xfinitywifi         5A:23:8C:E8:3C:35  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  --         no        
xfinitywifi         22:86:8C:4F:7D:94  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  --         no        
DIRECT-8C583F16     66:EB:8C:58:BF:16  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
FiOS-A3YVA          48:5D:36:08:F5:28  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
xfinitywifi         22:86:8C:C5:D0:F2  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  --         no        
PMVW8               F8:E4:FB:4A:5F:7E  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
NA656               00:26:62:9D:75:24  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WEP        no        
--                  32:86:8C:C5:D0:F2  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
WiFi Hotspot 3997   78:61:7C:45:45:18  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
Bantha-Private      20:25:64:FF:60:90  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
xfinitywifi         20:25:64:FF:60:92  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  --         no        
YK8DR               00:7F:28:E6:71:5E  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
inSpaktorGadget     00:18:01:FE:AD:60  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WEP        no        
LKPM4               00:1F:90:DC:B5:0C  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WEP        no        
--                  BE:34:26:9D:2F:76  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
--                  9E:34:26:9D:2F:76  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        

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
```

---

### Post by Randy_Bass on 2016-11-01
I had the same problem with a Realtek USB WIFI adapter. My problems actually started in an update to 14.04 LTS. The last kernel version I was able to use was 3.13.0-77. I remember it well because I had to create a grub entry to boot into that kernel explicitly to be able to use my wifi. When I upgraded to 16.04, I thought it would be fixed, but the WIFI still wouldn't work. The problem is that when the system updated to a new kernel version, it would rebuild the WIFI module (driver in Windows lingo) from the old kernel, but install it in the new kernel. So if I tried to up update the module with the new kernel, I got a message stating that the module already existed (hence, no update). Simply removing the module didn't work either, because it was installed using dkms. 

You can confirm that this is the issue by running the command
```
modinfo 8188ce
```
The first line will be something like 
```
filename:       /lib/modules/4.4.0-36-generic/updates/dkms/8188ce.ko
```
The 4.4.0-36-generic will be the current kernel you are running. The 8188ce.ko (or something similar) is the module installed for your hardware. Now scroll down a number of lines and look for the line

```
vermagic:       4.4.0-34-generic SMP mod_unload modversions 686
```

This is copied from my own example, but it shows that the kernel it was built under (4.4.0-34) was not the same one it is running under. Yours should show something similar.

So what you need to do is download the source code for your module from here:

[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

[COLOR=#111111][FONT=Ubuntu]Download the zip file to your selected directory and extract it there. Navigate down one directory. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]dkms (dynamic kernel module support) needs to be installed. If you don't have it, run:
[/FONT][/COLOR]```
sudo apt-get install dkms
```
[COLOR=#111111][FONT=Ubuntu]The following 2 commands only need to be run once for the module. Please note that I'm guessing your module name based on the model of your Realtek device. It'd be best for you to check your usr/src directory, as it should be something similar to this. If it is different, modify the commands accordingly. The first line will copy the source code and subdirectories to the usr/src directory appropriate for your module. Also make sure you delete any directories for old 8188ce modules. The second will remove the currently installed module from the kernel. 
[/FONT][/COLOR]```
sudo cp -R . /usr/src/8188ce-1.0
sudo dkms add -m 8188ce -v 1.0

```
[COLOR=#111111][FONT=Ubuntu]The next two commands will need to be run any time you need to rebuild and reinstall the driver (e.g., after a kernel update that doesn't work with the previous module). The first command will build your module using dkms. The second command will add the new module (built in the current kernel) to the current kernel, again with dkms.[/FONT][/COLOR]
```
sudo dkms build -m 8812au -v 1.0
sudo dkms install -m 8812au -v 1.0

```
After all that, things should be looking good, but chances are your WIFI is not working yet. Enter this command
```
ifconfig wlan0 up
```
As mine was a USB adapter, I had to then unplug it and plug it back in again, and then it worked fine. As yours is a pci card, if it's not working yet, try a reboot. 

The good news is, that since I did that (actually twice), the module has now been updating properly with each new kernel update. So hopefully if you do this once, you'll be all set. You can read about my efforts here, but I tried to modify them to fit your particular instance.

[http://askubuntu.com/questions/777696/xubuntu-wifi-driver-not-working-after-update/813683#813683](http://askubuntu.com/questions/777696/xubuntu-wifi-driver-not-working-after-update/813683#813683)

---

### Post by Hadaka on 2016-11-01
Hi the driver for your Ubuntu 16.04 looks correct, let's verify..
please open a terminal and do..
```
modinfo rtl8192ce
```
it should have an output line that reads...
```
alias:   pci:v0000[COLOR=#ff0000]10EC[/COLOR]d0000[COLOR=#ff0000]8176[/COLOR]sv*sd*bc*sc*i*
```
*If true then do..
```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce 
sudo modprobe -v rtl8192ce
```
boot...can you see that wireless access point now??
*If not try power cycling the computer and your router.
thanks.

---

