---
title: "Unreliable work of the internet"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by ozramsay on 2018-01-16
I followed [these]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access") instructions and installed driver ```
[COLOR=#333333][FONT=UbuntuMono]firmware-b43-installer[/FONT][/COLOR]
```. However, the internet works very unreliable and sometimes very slow. I have a second OS - Windows 8 on the same laptop, it works fine. 

My ethernet connection also very unstable. At first, it didn't connect to some websites: I could open google, but not the links of the search result. Today it stopped to work at all: "Ethernet Network: device not managed".

My system is Xubuntu 16.04  (installed a week ago)

```
oz@aspire:~$ lspci -vnn -d 14e4:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] NetLink BCM57785 Gigabit Ethernet PCIe [1025:0504]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d1830000 (64-bit, prefetchable) [size=64K]
    Memory at d1840000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 9fb00000 [disabled] [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3


02:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] BCM57765/57785 SDXC/MMC Card Reader [1025:0504]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1800000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci


02:00.2 System peripheral [0880]: Broadcom Corporation BCM57765/57785 MS Card Reader [14e4:16be] (rev 10)
    Subsystem: Acer Incorporated [ALI] BCM57765/57785 MS Card Reader [1025:0504]
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d1810000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>


02:00.3 System peripheral [0880]: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader [14e4:16bf] (rev 10)
    Subsystem: Acer Incorporated [ALI] BCM57765/57785 xD-Picture Card Reader [1025:0504]
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d1820000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>


03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. BCM43227 802.11b/g/n [105b:e040]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: bcma, wl

```
```
oz@aspire:~$ apt-cache search broadcom-sta-dkms
broadcom-sta-dkms - dkms source for the Broadcom STA Wireless driver
broadcom-sta-source - Source for the Broadcom STA Wireless driver

```

```
oz@aspire:~$  iwconfig
lo        no wireless extensions.


enp2s0f0  no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"Ufanet_43"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 22:4A:03:77:BD:F0   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
I also received an error (attached) when I re-installed the driver after it had disappeared from 'additional drivers' . Despite the error, though, I have the 'additional drivers' page states that the driver is used.

---

### Post by ozramsay on 2018-01-17
OK, I have repaired the wired connection thanks to this[ instructions.]("https://www.youtube.com/watch?v=wjS4eBnR3q0")

However, now my Wi-Fi connection is completely lost: I see the network, but I can not connect to it (it just showing the spinning wheel every time). I also cannot change any proprietary driver: if I select another driver for Nvidia nothing changes, or if select 'do not use this device' for Broadcom also nothing changes.  The previously selected drivers are still marked as selected.

Could any please give me any advice?

---

### Post by Hadaka on 2018-01-17
Hi, From a Working wired connection..
please open a terminal...ctrl/alt/t..then Copy and paste..
```
sudo apt-get update
sudo apt-get remove --purge bcma
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
systemctl restart network-manager.service
```
Remove wired connection,reboot and test wireless.
*If you are still having difficulties then..
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the **wireless-info.txt**
Thanks.

---

### Post by ozramsay on 2018-01-17
> **Hadaka said:**
> Hi, From a Working wired connection..
please open a terminal...ctrl/alt/t..then Copy and paste..
```
sudo apt-get update
sudo apt-get remove --purge bcma
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
systemctl restart network-manager.service
```
Remove wired connection,reboot and test wireless.
*If you are still having difficulties then..
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the **wireless-info.txt**
Thanks.

HI, Hadaka!

Thank you  very much for the clear instructions and fast reply! The WiFi indeed started to work. Though the speed is 0,5 Mbps, whereas it is more than 5 Mbps on a wired connection in Ubuntu or on a wireless connection in Windows. 

I also received an error message (attached).

```


########## wireless info START ##########


Report from: 17 Jan 2018 20:45 +05 +0500


Booted last: 17 Jan 2018 00:00 +05 +0500


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################




02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] NetLink BCM57785 Gigabit Ethernet PCIe [1025:0504]
	Kernel driver in use: tg3


03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
	Subsystem: Foxconn International, Inc. BCM43227 802.11b/g/n [105b:e040]
	Kernel driver in use: wl


##### lsusb #############################


Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b21b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6447104  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
wmi_bmof               16384  0
cfg80211              614400  1 wl
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,acer_wmi,mxm_wmi,nouveau
video                  40960  3 acer_wmi,nouveau,i915


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /bin/ip link set enp2s0f0 up # line maintained by pppoeconf
provider dsl-provider


auto enp2s0f0
iface enp2s0f0 inet manual




##### ifconfig ##########################


enp2s0f0  Link encap:Ethernet  HWaddr b8:70:f4:ed:5e:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70645 (70.6 KB)  TX bytes:70645 (70.6 KB)


wlp3s0    Link encap:Ethernet  HWaddr cc:af:78:07:16:9e  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd79:588b:3ff6:0:ceaf:78ff:fe07:169e/64 Scope:Global
          inet6 addr: fe80::ceaf:78ff:fe07:169e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12156 errors:0 dropped:0 overruns:0 frame:5535
          TX packets:11150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11351223 (11.3 MB)  TX bytes:2770800 (2.7 MB)
          Interrupt:17 


##### iwconfig ##########################


enp2s0f0  no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"Ufanet_43"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 22:4A:03:77:BD:F0   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       952     1  0 20:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43227 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         CC:AF:78:07:16:9E
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
GENERAL.CONNECTION:                     Ufanet_43
GENERAL.CON-UUID:                       edd00664-e004-45a1-b56e-8d83317c0f5a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     5 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   edd00664-e004-45a1-b56e-8d83317c0f5a | Ufanet_43
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1516228873
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 25200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.33
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       wpad = a
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fd79:588b:3ff6:0:ceaf:78ff:fe07:169e/64
IP6.ADDRESS[2]:                         fe80::ceaf:78ff:fe07:169e/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fd79:588b:3ff6::/48, nh = fe80::424a:3ff:fe77:bdf3, mt = 600
IP6.ROUTE[2]:                           dst = fd79:588b:3ff6::/64, nh = ::, mt = 600
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_server_id = 0:3:0:1:40:4a:3:77:bd:f3
DHCP6.OPTION[3]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_client_id = 0:4:b7:b5:ae:c:1a:a4:91:2e:34:14:ff:58:a5:a:a8:f1


GENERAL.DEVICE:                         enp2s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM57785 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         B8:70:F4:ED:5E:60
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0f0
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




SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Ufanet_43  22:4A:03:77:BD:F0  Infra  10    2457 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
Ufanet_40  90:F6:52:B9:56:4C  Infra  9     2452 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
Domru-53   70:4F:57:2C:E1:49  Infra  10    2457 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        


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
managed=true


##### NetworkManager profiles ###########

```

---

### Post by Hadaka on 2018-01-17
Hi, Please open a terminal...ctrl/alt/t then Copy and Paste
```
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac" | sudo tee -a /etc/modeprobe.d/blacklist.conf
echo -e "blacklist ssb\nblacklist b43" | sudo tee -a /etc/modeprobe.d/blacklist.conf
```

 You did not supply a complete report.
    Please open a terminal...ctrl/alt/t then Copy and Paste .
    ```
 sudo rm -rf wireless-info.*
```
    ```
 wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./ wireless-info
```

    Then do..
```
cat wireless-info.txt | nc termbin.com 9999
```
    This will have an output that looks this...
    [http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
    copy and paste to your reply.
    Thank you

---

### Post by ozramsay on 2018-01-17
> **Hadaka said:**
> Hi, Please open a terminal...ctrl/alt/t then Copy and Paste
```
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac" | sudo tee -a /etc/modeprobe.d/blacklist.conf
echo -e "blacklist ssb\nblacklist b43" | sudo tee -a /etc/modeprobe.d/blacklist.conf
```

You did not supply a complete report.
Please open a terminal...ctrl/alt/t then Copy and Paste .
```
 sudo rm -rf wireless-info.*
```
```
 wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./ wireless-info
```

Then do..
```
cat wireless-info.txt | nc termbin.com 9999
```
This will have an output that looks this...
    [http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

[http://termbin.com/s4r1](http://termbin.com/s4r1). I have also attached the results. Thank you!

---

### Post by Hadaka on 2018-01-17
Hi, please Copy and paste to avoid input errors.
```
*Error [ipv6] method=ignore | method=auto
```
To correct..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
```
Then do..
```
echo "blacklist brcmwl" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get remove --purge brcmwl
sudo apt-get install --reinstall bcmwl-kernel-source
```
boot and test wireless

---

### Post by ozramsay on 2018-01-18
> **Hadaka said:**
> Hi, please Copy and paste to avoid input errors.
```
*Error [ipv6] method=ignore | method=auto
```
To correct..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
```
Then do..
```
echo "blacklist brcmwl" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get remove --purge brcmwl
sudo apt-get install --reinstall bcmwl-kernel-source
```
boot and test wireless

Hi, Hadaka! Unfortunately, no luck. I have rerun the script: [http://termbin.com/stoh](http://termbin.com/stoh). Thank you. 


```
oz@aspire:~$ ping ya.ru
ping: unknown host ya.ru
oz@aspire:~$ ping google.com
PING google.com (145.255.14.152) 56(84) bytes of data.
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=1 ttl=61 time=857 ms
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=2 ttl=61 time=1090 ms
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=3 ttl=61 time=647 ms
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=4 ttl=61 time=1176 ms
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=5 ttl=61 time=1734 ms
64 bytes from 145.255.14.152.dynamic.ufanet.ru (145.255.14.152): icmp_seq=6 ttl=61 time=2156 ms
^C
--- google.com ping statistics ---
9 packets transmitted, 6 received, 33% packet loss, time 9378ms
rtt min/avg/max/mdev = 647.618/1277.327/2156.791/516.463 ms, pipe 3
oz@aspire:~$ ping fb.com
PING fb.com (31.13.72.36) 56(84) bytes of data.
64 bytes from edge-star-mini-shv-01-arn2.facebook.com (31.13.72.36): icmp_seq=1 ttl=55 time=3740 ms
64 bytes from edge-star-mini-shv-01-arn2.facebook.com (31.13.72.36): icmp_seq=2 ttl=55 time=2811 ms
64 bytes from edge-star-mini-shv-01-arn2.facebook.com (31.13.72.36): icmp_seq=3 ttl=55 time=3218 ms
64 bytes from edge-star-mini-shv-01-arn2.facebook.com (31.13.72.36): icmp_seq=4 ttl=55 time=3071 ms
^C
--- fb.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 6200ms
rtt min/avg/max/mdev = 2811.023/3210.328/3740.246/338.954 ms, pipe 4

```
PS. The first line have returned an error:
```
oz@aspire:~$ *Error [ipv6] method=ignore | method=auto*Error: command not found
oz@aspire:~$ sudo *Error [ipv6] method=ignore | method=autosudo: *Error: command not found

```

---

### Post by Hadaka on 2018-01-18
Hi, this was NOT a command but pointing out an error you made 
attempting to type it in instead of copying and pasting.
Hence the word *Error...AND the Error is still there...
```
# *Error [ipv6] method=ignore | method=auto
```

and This command to Correct that error...
Please COPY and Paste. To correct the error.
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
```
Then post the output of...
```
sudo cat /etc/NetworkManager/system-connections/Ufanet_43 | grep -i method
```
once this is completed and posted we shall continue..
Awaiting your post
Thanks.

---

### Post by ozramsay on 2018-01-18
> **Hadaka said:**
> Hi, this was NOT a command but pointing out an error you made 
attempting to type it in instead of copying and pasting.
Hence the word *Error...AND the Error is still there...
```
# *Error [ipv6] method=ignore | method=auto
```

and This command to Correct that error...
Please COPY and Paste. To correct the error.
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43
```
Then post the output of...
```
sudo cat /etc/NetworkManager/system-connections/Ufanet_43 | grep -i method
```
once this is completed and posted we shall continue..
Awaiting your post
Thanks.

Oh, I see, sorry. I have suspected that I made an error, but I wasn't sure where exactly:)

method=auto
method=ignore
method=auto

Thank you!

---

### Post by ozramsay on 2018-01-18
Hadaka, thank you very much, it works. I really appreciate your time and effort!

Would you mind to outline what was wrong and what was the remedy? 

From my understanding, be the second command you have edited the Ufanet_43 file and switched off ipv6. The first command I do not understand
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Ufanet_43

---

### Post by Hadaka on 2018-01-18
Hi, the first command is a short version of..
```
#sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
iwconfig
```
displays the power management status ...ON..or..OFF
It was on and we turned it off.
Glad the wifi is more stable now. Please mark your thread Solved
by logging into your thread..first post and clicking **Thread Tools**
[on the right..just above..join date] and then choose **Solved**
Thank You
 p.s.
*If this command..
```
sudo cat /etc/NetworkManager/system-connections/Ufanet_43
```
shows 2 entries for [ipv6] delete the one that says auto. Ipv6 only...NOT Ipv4
[IPv4] should be auto.
by editor gedit..
```
sudo gedit  /etc/NetworkManager/system-connections/Ufanet_43
```
Save and close gedit.

---

### Post by ozramsay on 2018-01-19
> **Hadaka said:**
> Hi, the first command is a short version of..
```
#sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
iwconfig
```
displays the power management status ...ON..or..OFF
It was on and we turned it off.
Glad the wifi is more stable now. Please mark your thread Solved
by logging into your thread..first post and clicking **Thread Tools**
[on the right..just above..join date] and then choose **Solved**
Thank You
 p.s.
*If this command..
```
sudo cat /etc/NetworkManager/system-connections/Ufanet_43
```
shows 2 entries for [ipv6] delete the one that says auto. Ipv6 only...NOT Ipv4
[IPv4] should be auto.
by editor gedit..
```
sudo gedit  /etc/NetworkManager/system-connections/Ufanet_43
```
Save and close gedit.

Hi, Hadaka. The problem, well, was solved:) Yet today I lost all connections to the Internet, the wired opens only google and youtube. And changing /etc/resolvconf did not work out. So I am writing this mesaage from the phone

Thank you!

---

### Post by ozramsay on 2018-01-19
Now the WiFi connection has returned (but I didn't do anything). I deleted 'method=auto', so now it looks so (I deleted the line after the connection restored, so it has restored idependly): 

> [ipv4]
dns-search=
method=auto


[ipv6]
addr-gen-mode=eui64
dns-search=
ip6-privacy=0


Will update to newer version solve this problem. To 17.10? 

I have rerun the script: [http://termbin.com/w7mo](http://termbin.com/w7mo)

Thank you very much!

---

### Post by Hadaka on 2018-01-19
Hi, I doubt loading an expired no longer supported Ubuntu 17.10
will help.
You may also want to correct your Country code as it now says..US
```
sudo iw reg set RU
sudo sed -i 's/=.*/=RU/' /etc/default/crda
```
Thanks

---

### Post by ozramsay on 2018-01-20
> **Hadaka said:**
> Hi, I doubt loading an expired no longer supported Ubuntu 17.10
will help.
You may also want to correct your Country code as it now says..US
```
sudo iw reg set RU
sudo sed -i 's/=.*/=RU/' /etc/default/crda
```
Thanks

Hi, Hadaka. 

I have corrected the Country code. Yet both wired and wireless connections work very unreliably and could stop to work at any moment.

I am very sorry for bothering you so much, but is there anything else we can do?

Thank you for your time and patience!

---

### Post by ozramsay on 2018-01-20
[https://askubuntu.com/a/208027](https://askubuntu.com/a/208027)

As far as I understand, manually changing resolf.conf is not going to work.
I also followed these instructions, however, they didn't work. I also tried to edit connections manually, it also didn't work

---

### Post by Hadaka on 2018-01-20
Hi, In post # 11, you stated everything was working..
Then for some "unknown" reason it was not.
I suggested making a change to set 1pv6 to ignore..
this is your output..
```
# [ipv4]
dns-search=
method=auto 

$[ipv6]
addr-gen-mode=eui64
dns-search=
ip6-privacy=0 
```
This is the output from my computer..
```
[ipv4]
method=auto

[ipv6]
method=ignore
```
I would suggest editing the /etc/NetworkManager/system-connections/Ufanet_43 file
and correcting ..
```
sudo gedit/etc/NetworkManager/system-connections/Ufanet_43 
```
# * This is an indication that UEFI/secure boot is Enabled..
dmesg.
wl: module verification failed: signature and/or required key missing - tainting kernel

I suggest you access bios and disable UEFI/secure boot.

I have no idea why you are editing or attempting to edit "resolv.conf"
If you make any changes..please supply a new wireless infor report.
Thanks.

---

### Post by ozramsay on 2018-01-20
Hi, Hadaka.

I stated that the internet is working and at that time everything was fine. Then both wired and wireless connections ceased to work, so I unsuccessfully tried to post a message here for two days. Then I tried to repair at least the wired connection by editing resolv.conf to be able to post here. It started to work but very unreliable.  

OK, I have edited [COLOR=#000000]/etc/NetworkManager/system-connections/Ufanet_43 file as you described. 

[/COLOR]> [COLOR=#000000]I suggest you access bios and disable UEFI/secure boot[/COLOR]

Sorry, I was not able to find this message. 

[http://termbin.com/gr5g](http://termbin.com/gr5g)

Thank you!

---

### Post by Hadaka on 2018-01-20
Hi, it seems with each new wireless report the errors and AP changes..
We see the ethernet has an IP address of.. 
enp2s0f0  Link encap:Ethernet  HWaddr <MAC 'enp2s0f0' [IF1]>  
          inet addr:100.94.141.215  Bcast:100.94.255.255  Mask:255.255.0.0
And when it has an address, the wireless is:
wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0

Are the wired and wireless connected to the same router ?????

The latest dmesg errors are showing this...
[  465.645954] ERROR @wl_inform_single_bss :  (repeated 3 times)
[ 1635.376501] ERROR @wl_dev_intvar_get :
Let's see if you have an up to date WL dirver. Please post the output of..
```
sudo dpkg -s bcmwl-kernel-source | grep Version
```

Next..It was brought to my attention that the current kernel is..
 kernel 4.13.0-26:
There are major problems with that kernel, as noted here..
[https://askubuntu.com/questions/995819/touchpad-gestures-and-holding-keys-does-not-work/995948#995948](https://askubuntu.com/questions/995819/touchpad-gestures-and-holding-keys-does-not-work/995948#995948)
Boot the computer while holding down the shift key.
choose kernel 4.13.0-25 and see if there any improvements.
Thanks.

---

### Post by ozramsay on 2018-01-21
Hi, Hadaka!

The wired connection goes directly from the provider to my laptop without any routers on my side.
The wireless connection goes from the same provider to Zyxel router and then on Wi-Fi to the laptop.

Today I have my line checked by the provider. It is OK.

I also made some observations: the wired connections always works in Windows. In Ubuntu the wired connection always can access major sites such as google or yandex. However, sometimes it cannot access any other website except the mentioned ones, and sometimes it shows every website.

If the wireless connections works it always can access any website. However, if it does not work on the laptop, it also does not work on my phone.

So, I believe I have two separate problems:

You have helped me to set the wireless connection on the Ubuntu and it works well. The problem with the wireless connection is in my router, it's quite old. Due to the budget reasons, I will not buy a new one. 

The problem with the wired connection is in my Ubuntu, as it always works in Windows, and the line is OK. Could you please help me with this problem?

The earlier kernel in the list is 4.10.0.28. Do you want me to install the kernel you mentioned (if I am not mistaken I can do it via Synaptic)?


> oz@aspire:~$ sudo dpkg -s bcmwl-kernel-source | grep Version
[sudo] password for oz: 
Version: 6.30.223.271+bdcom-0ubuntu1~1.2


Thank you very much!

---

### Post by Hadaka on 2018-01-22
Hi, did the computer used to function correctly on the 4.10.0.28 kernel ?
*If yes...then boot to that kernel and see if all is well.
Thanks

---

### Post by ozramsay on 2018-01-22
Hi, so far it's OK.
Thanks

---

### Post by ozramsay on 2018-01-24
Thank you very much Hadaka for your invaluable help!

---

### Post by Hadaka on 2018-01-24
You are welcome, Enjoy !
Thank you for marking the thread Solved.

---

