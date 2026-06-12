---
title: "very weak wifi signal in ubuntu 18.04 when using TP-link USB wifi dongle"
date: 2018-09-23
forum: Networking &amp; Wireless
---

### Post by surya.durgaputra on 2018-09-23
Hello, 
I am using a TP-link USB 2.0 wifi dongle. Model TL-WN823N (FCC-ID has WN823NV2). My PC shows extremely weak wifi signal strength. Looking around I realized that this is a very well known issue on ubuntu (my PC is dual boot, windows-10 side gets full strength wifi signal).
Here's what I did:
[LIST=1]
[*]Went to manufacturer's website to look for drivers at [https://www.tp-link.com/us/download/TL-WN823N_V2.html](https://www.tp-link.com/us/download/TL-WN823N_V2.html) . But the downloaded drivers don't compile. They fail at make stage. Also, the readme mentions that the driver is only tested with ubuntu14.04.
[*]already done : sudo apt-get install git linux-headers-generic build-essential dkms
[/LIST]

Advise needed on what more to do.

For more info, I am running Ubuntu 18.04. running *uname-r *shows 4.15.0-34-generic as my kernel version. I don't have an ethernet connection in this place at all. So connecting via wifi is the only option.

Thanks,
Surya

---

### Post by chili555 on 2018-09-23
Please run and post:```
lsusb | grep rtl
```

---

### Post by surya.durgaputra on 2018-09-23
Hello chili555,
 I ran 

lsusb | grep rtl

But it returned an empty response.

I then ran this (with my USB wifi dongle connected)

helios@helios:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 008: ID 2357:0109  
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and then I removed the usb wifi dongle and reran lsusb and got this:

[COLOR=#000000][INDENT]helios@helios:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[/INDENT]
[/COLOR]Looks like the wifi-dongle is showing up as:
Bus 001 Device 008: ID 2357:0109

---

### Post by chili555 on 2018-09-23
Sorry for my mis-step. I've adjusted my spectacles and ask that you show:```
lsmod | grep rtl
```

---

### Post by surya.durgaputra on 2018-09-23
Hello chili555,
 Here is what I get:

helios@helios:~$ lsmod | grep rtl
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu

Please note that I don't have a wifi card on my motherboard. Only ethernet. Hence the wifi usb dongle.

I am attaching some more detailed info:
```
##### kernel ############################


Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 008: ID 2357:0109  
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


5: phy5: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              622592  1 mac80211
wmi_bmof               16384  0
mxm_wmi                16384  0
wmi                    24576  3 asus_wmi,wmi_bmof,mxm_wmi
video                  45056  2 asus_wmi,i915


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### iwconfig ##########################


lo        no wireless extensions.

##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx7c8bca1af6be
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek 
GENERAL.PRODUCT:                        802.11n NIC 
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11:1.0/net/wlx7c8bca1af6be
GENERAL.IP-IFACE:                       wlx7c8bca1af6be
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HUAWEI-BUSG
GENERAL.CON-UUID:                       6551db5d-7c9c-4a25-b695-5544eb903b6c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.100.4/24
IP4.GATEWAY:                            192.168.100.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.100.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.100.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.100.1
DHCP4.OPTION[1]:                        network_number = 192.168.100.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1537965986
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.100.1
DHCP4.OPTION[14]:                       ip_address = 192.168.100.4
DHCP4.OPTION[15]:                       dhcp_lease_time = 259200
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.100.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.100.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.100.1
IP6.ADDRESS[1]:                         fe80::a14f:2293:36f8:5238/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = ::/0, nh = fe80::1, mt = 600
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:c7:92:bc:99:48:ad:8:d6:40:18
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:31:98:3b:3e:6a:44:3e:3b:56:f7:4e:b4:be:8e:28:9b
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6551db5d-7c9c-4a25-b695-5544eb903b6c | HUAWEI-BUSG


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID         BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
HUAWEI-BUSG  <MAC 'HUAWEI-BUSG' [AC2]>  Infra  11    2462 MHz  130 Mbit/s  30      &#9602;___  WPA1 WPA2  yes     *      
HUAWEI-tbrh  <MAC 'HUAWEI-tbrh' [AC1]>  Infra  11    2462 MHz  65 Mbit/s   10      &#9602;___  WPA1 WPA2  no   



enp2s0    no wireless extensions.


wlx7c8bca1af6be  IEEE 802.11  ESSID:"HUAWEI-BUSG"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HUAWEI-BUSG' [AC2]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```

---

### Post by chili555 on 2018-09-23
I suggest that we try a different driver. From the terminal:

```
sudo apt-get update
sudo apt-get install git build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0
sudo modprobe 8192eu

```
And blacklist the current driver:

```
sudo -i
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit

```Reboot and tell us if there is any improvement.

---

### Post by surya.durgaputra on 2018-09-23
Hello chili555,
 You sir are amazing!!  It is working now. \\:D/\\:D/\\:D/\\:D/
The driver change + reboot fixed the issue of weak wifi.

If it does not take much time, would you please give me some pointers on why [COLOR=#000000][FONT=&amp]rtl8192eu . Its a great learning opprtunity :). Need not be detailed pointers. I can fill in the blanks via google. [/FONT][/COLOR]

Best Regards,
Surya

---

### Post by chili555 on 2018-09-24
> **surya.durgaputra said:**
> Hello chili555,
 You sir are amazing!!  It is working now. \\:D/\\:D/\\:D/\\:D/
The driver change + reboot fixed the issue of weak wifi.

If it does not take much time, would you please give me some pointers on why [COLOR=#000000][FONT=&amp]rtl8192eu . Its a great learning opprtunity :). Need not be detailed pointers. I can fill in the blanks via google. [/FONT][/COLOR]

Best Regards,
SuryaAwesome! Glad it's working.

All I know is that from experience here and on other forums, the built-in driver rtl8xxxu does a lousy job for your chipset and that for your exact device, 2357:0109, the compiled 8192eu does a much better job.

I wish I had a scientific answer involving examining the .c code and packet RX and TX and so on, but I am not an engineer. I am a tinkerer with greasy hands and a hacksaw. Almost everything I post is based on experience or Google results. 

This is the real Chili: [https://mediadc.brightspotcdn.com/dims4/default/696406e/2147483647/strip/true/crop/939x939+0+0/resize/939x939!/quality/90/?url=https%3A%2F%2Fmediadc.brightspotcdn.com%2F54%2F30%2F4527d5abe9eb6e59080f8c765f8b%2Ff0e5c4079ed756eeb3e2500e9b855b95.jpg](https://mediadc.brightspotcdn.com/dims4/default/696406e/2147483647/strip/true/crop/939x939+0+0/resize/939x939!/quality/90/?url=https%3A%2F%2Fmediadc.brightspotcdn.com%2F54%2F30%2F4527d5abe9eb6e59080f8c765f8b%2Ff0e5c4079ed756eeb3e2500e9b855b95.jpg)

---

### Post by zzz... on 2018-09-25
> **chili555 said:**
> I suggest that we try a different driver. From the terminal:

```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0
sudo modprobe 8192eu

```
And blacklist the current driver:

```
sudo -i
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit

```Reboot and tell us if there is any improvement.

This worked for me as well thank you so much. I was using TL-Wn821N V5 on Ubuntu 18.04 LTS

---

### Post by tburgess604 on 2018-12-01
Worked for me on Ubuntu 18.10 - Thanks.

---

### Post by tusharsonawane on 2019-08-16
Thank you soo soo much for this. My tplink 823n v2 working perfectly on Ubuntu 18.04 on 17th august 2019

---

### Post by linux-bioinfo on 2020-02-26
Can anyone please help me with the same problem. This is output for the command lsmod | grep rtl. 
btrtl                  20480  1 btusb
bluetooth             573440  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm


PS my desktop has Intel dual band wireless - AC 3168 hardware. kindly help

---

### Post by wildmanne39 on 2020-02-26
Hello and welcome to the forum linux-bioinfo, please create your own thread, this is an old thread and we do not know if your device and issue is the exact same as this users.

Post the results of the wireless script in my signature in your thread.

Old thread closed!

Thanks

---

