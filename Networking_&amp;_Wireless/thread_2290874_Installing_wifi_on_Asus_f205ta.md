---
title: "Installing wifi on Asus f205ta"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by Publius_Quinctiliu on 2015-08-16
Hello Everyone,
 i am a newbie, but so far have successfully installed Ubuntu 15.04 next to Windows 8.1 on my Asus f205ta. Now im trying to get the wifi working following this guide: [https://wiki.debian.org/InstallingDebianOn/Asus/X205TA](https://wiki.debian.org/InstallingDebianOn/Asus/X205TA)
I have upgraded to Kernel 4.1.5, but whenever i try the last command ( cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43340-sdio.txt ) Ubuntu can not find the nvram-file. In fact there is no file in the efivars-directory beginning with nvram (i have used "ls /sys/firmware/efi/efivars/" for this, i hope that is right).
Can anyone try to assist me please? By the way, could it have anything to do with a rather complicated installation of grub in 32bit efi mode for 64 bit ubuntu (installing windows in 64 bit is not possible since the drivers are only available for 32 bit)? also, my model is called f205ta instead of x205ta, but the specs are completely the same(i guess i got the european version or something like that). Wifi is working flawlessly in Windows. Any help would be much appreciated.
here some things that might be of interest to you:

uname -r :
Linux BabsMini 4.1.5-040105-generic #201508101730 SMP Mon Aug 10 21:31:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

hwfinfo (i am using a usb-wifi-stick right now so i guess that is the last entry?!) :
```
description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1935MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1068MHz
          capacity: 1832MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0f
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:207 memory:90000000-903fffff memory:80000000-8fffffff ioport:1000(size=8)
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:205 memory:90700000-907fffff memory:90600000-906fffff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx Series USB EHCI
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:201 memory:9080d000-9080d3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.1.5-040105-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.01
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Video
                      product: USB2.0 VGA UVC WebCam
                      vendor: Chicony Electronics Co., Ltd
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 99.14
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
                 *-usb:1
                      description: USB hub
                      product: USB2.0 Hub
                      vendor: Genesys Logic, Inc.
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 32.98
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Mouse
                         product: AND
                         vendor: MOON
                         physical id: 1
                         bus info: usb@1:1.2.1
                         version: 0.10
                         serial: @
                         capabilities: usb-1.00
                         configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
                    *-usb:1
                         description: Generic USB device
                         product: RTL8188S WLAN Adapter
                         vendor: Manufacturer Realtek
                         physical id: 2
                         bus info: usb@1:1.2.2
                         version: 2.00
                         serial: 00e04c000001
                         capabilities: usb-2.00
                         configuration: driver=r8712u maxpower=500mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.2.2
       logical name: wlan0
       serial: 00:0c:f6:ef:b1:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.3 multicast=yes wireless=IEEE 802.11bg
```

output of ls /sys/firmware/efi/efivars/

```
AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e
AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
AEDID-75860b2c-f315-4ff1-9e19-029ad0129dba
AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34
ASUSFactoryControl-8be4df61-93ca-11d2-aa0d-00e098032b8c
ASUSSetupDefault-f1920447-7a78-4c0d-a028-ba9d003985e8
ASUSTPType-8be4df61-93ca-11d2-aa0d-00e098032b8c
BDADDR-74b00bd9-805a-4d61-b51f-43268123d113
Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
db-d719b2cb-3d3a-4596-a3bc-dad00e67656f
dbx-d719b2cb-3d3a-4596-a3bc-dad00e67656f
DefaultBootOrder-45cf35f6-0d6e-4d04-856a-0370a5b16f53
DriverHealthCount-7459a7d4-6533-4480-bba7-79e25a4443c9
DriverHlthEnable-0885f288-418c-4be1-a6af-8bad61da08fe
EcUpdate-1c02afc1-dd2d-49a9-b7f2-9836f61d763f
EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15
ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
FastBootOption-b540a530-6978-4da7-91cb-7207d764d262
FPDT_Variable-01368881-c4ad-4b1d-b631-d57a8ec8db6b
GPTHDD_PRESENT-8be4df61-93ca-11d2-aa0d-00e098032b8c
KEK-8be4df61-93ca-11d2-aa0d-00e098032b8c
LastBoot-b540a530-6978-4da7-91cb-7207d764d262
MemoryOverwriteRequestControl-e20939be-32d4-41be-a150-897f85d49829
MemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa
MonotonicCounter-01368881-c4ad-4b1d-b631-d57a8ec8db6b
MSDMTBL-01368881-c4ad-4b1d-b631-d57a8ec8db6b
NetworkStackVar-d1405d16-7afc-4695-bb12-41459d3695a2
OA3MSDMvariable-01368881-c4ad-4b1d-b631-d57a8ec8db6b
OsIndications-8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c
PBRDevicePath-a9b5f8d2-cb6d-42c2-bc01-b5ffaae4335e
PK-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
PreviousMemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa
S3SS-4bafc2b4-02dc-4104-b236-d6f1b98d9e84
SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c
SecureFlashSetupVar-35c936af-e1e1-441a-bad1-e1544e9d97a6
Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
SetupMode-8be4df61-93ca-11d2-aa0d-00e098032b8c
SignatureSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824
TcgInternalSyncFlag-f3ed95df-828e-41c7-bca0-16c41965a634
Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c
TrEEPhysicalPresence-f24643c2-c622-494e-8a0d-4632579c2d5b
UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
WriteOnceStatus-4b3082a3-80c6-4d7e-9cd0-583917265df1


```

---

### Post by jeremy31 on 2015-08-16
Post the result of ```
lspci -nnk | grep -iA2 net
```

---

### Post by Publius_Quinctiliu on 2015-08-16
your command does not do anything. i tried lspci -nn -k, here is the result:
```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:18cd]
    Kernel driver in use: iosf_mbi_pci
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:18cd]
    Kernel driver in use: i915
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:182d]
    Kernel driver in use: mei_txe
00:1d.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB EHCI [8086:0f34] (rev 0f)
    Subsystem: Device [e286:890e]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:182d]
    Kernel driver in use: lpc_ich 
```

---

### Post by jeremy31 on 2015-08-16
Follow the instructions on running the wireless script and posting the results [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Publius_Quinctiliu on 2015-08-16
```
 [B]
########## wireless info START ##########

Report from: 16 Aug 2015 13:24 CEST +0200

Booted last: 16 Aug 2015 12:58 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 4.1.5-040105-generic #201508101730 SMP Mon Aug 10 21:31:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

##### lsusb #############################

Bus 001 Device 008: ID 13ee:0001 MosArt 
Bus 001 Device 007: ID 0df6:005b Sitecom Europe B.V. 
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8712u                184320  0 
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
brcmfmac              278528  0 
brcmutil               16384  1 brcmfmac
cfg80211              552960  1 brcmfmac
wmi                    20480  1 asus_wmi
video                  20480  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4208 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4560810 (4.5 MB)  TX bytes:572618 (572.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"home3"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC '**home3**' [AC1]>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       610     1  0 12:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Manufacturer Realtek 
GENERAL.PRODUCT:                        RTL8188S WLAN Adapter 
GENERAL.DRIVER:                         r8712u
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     **home3**
GENERAL.CON-UUID:                       ebf20889-96e2-4d78-b4ce-652aa0361d10
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ebf20889-96e2-4d78-b4ce-652aa0361d10 | **home3**
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.3/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1439810348
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.3
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WLAN-676EDD     <MAC 'WLAN-676EDD' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
EasyBox-509738  <MAC 'EasyBox-509738' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
**home3**      <MAC '**home3**' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/**home3**]] (600 root)
[connection] id=**home3** | type=wifi
[wifi] ssid=**home3** | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '**home3**' [AC1]>
                    ESSID:"**home3**"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'WLAN-676EDD' [AC2]>
                    ESSID:"WLAN-676EDD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 03 - Address: <MAC 'EasyBox-509738' [AC3]>
                    ESSID:"EasyBox-509738"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2020050f20401000050f2020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Signal level=7/100  

##### module infos ######################

[r8712u]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     A0DDC386F212DB329A49CC5
depends:        
staging:        Y
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

[brcmfmac]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.txt
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.txt
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.txt
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.txt
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     26663514B5D324624B97E03
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/4.1.5-040105-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

[brcmfmac]
debug: 0
fcmode: 0
roamoff: 0

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.711165] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 43340 rev 2 pmurev 20
[    4.770067] brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2
[    5.733748] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    5.735340] r8712u: register rtl8712_netdev_ops to netdev_ops
[    5.735347] usb 1-1.2.2: r8712u: USB_SPEED_HIGH with 4 endpoints
[    5.735857] usb 1-1.2.2: r8712u: Boot from EFUSE: Autoload OK
[    6.358165] usb 1-1.2.2: r8712u: CustomerID = 0x0000
[    6.358174] usb 1-1.2.2: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[    6.358179] usb 1-1.2.2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    7.729268] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[    8.341379] r8712u 1-1.2.2:1.0 wlan0: 1 RCR=0x153f00e
[    8.342118] r8712u 1-1.2.2:1.0 wlan0: 2 RCR=0x553f00e
[    8.740763] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[ 1241.745114] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1241.745130] usb 1-1.2.1: r8712u: USB_SPEED_HIGH with 4 endpoints
[ 1241.746931] usb 1-1.2.1: r8712u: Boot from EFUSE: Autoload OK
[ 1242.348481] usb 1-1.2.1: r8712u: CustomerID = 0x0000
[ 1242.348490] usb 1-1.2.1: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[ 1242.348495] usb 1-1.2.1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1244.138912] r8712u 1-1.2.1:1.0 wlan0: 1 RCR=0x153f00e
[ 1244.140766] r8712u 1-1.2.1:1.0 wlan0: 2 RCR=0x553f00e

########## wireless info END ############
[/B] 
```

---

### Post by jeremy31 on 2015-08-16
Go to [http://packages.ubuntu.com/wily/all/linux-firmware/download](http://packages.ubuntu.com/wily/all/linux-firmware/download) and select a download site and install the deb file, reboot

If it still doesn't work, run the script again and post the new results

---

### Post by praseodym on 2015-08-16
```
Bus 001 Device 007: ID 0df6:005b Sitecom Europe B.V. 
```
There it is, the right driver r8712u is loaded, but additionally a Broadcom driver (brcmfmac), too.
```

echo "blacklist brcmfmac" | sudo tee /etc/modprobe.d/blacklist-bradcom.conf
```
Reboot

---

### Post by Publius_Quinctiliu on 2015-08-16
i still could not find any nvram in /sys/firmware/efi/efivars, so here is the new output of the script:

```

########## wireless info START ##########

Report from: 16 Aug 2015 14:05 CEST +0200

Booted last: 16 Aug 2015 14:01 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 4.1.5-040105-generic #201508101730 SMP Mon Aug 10 21:31:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

##### lsusb #############################

Bus 001 Device 006: ID 13ee:0001 MosArt 
Bus 001 Device 005: ID 0df6:005b Sitecom Europe B.V. 
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8712u                184320  0 
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
brcmfmac              278528  0 
brcmutil               16384  1 brcmfmac
cfg80211              552960  1 brcmfmac
wmi                    20480  1 asus_wmi
video                  20480  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1130 errors:0 dropped:34 overruns:0 frame:0
          TX packets:1236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:757440 (757.4 KB)  TX bytes:252489 (252.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wlan0"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'wlan0' [AC1]>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=98/100  Signal level=59/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       667     1  0 14:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Manufacturer Realtek 
GENERAL.PRODUCT:                        RTL8188S WLAN Adapter 
GENERAL.DRIVER:                         r8712u
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     wlan0
GENERAL.CON-UUID:                       ebf20889-96e2-4d78-b4ce-652aa0361d10
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ebf20889-96e2-4d78-b4ce-652aa0361d10 | wlan0
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.3/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1439812902
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.3
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
WLAN-676EDD  <MAC 'WLAN-676EDD' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
wlan0   <MAC 'wlan0' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/wlan0]] (600 root)
[connection] id=wlan0 | type=wifi
[wifi] ssid=wlan0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'wlan0' [AC1]>
                    ESSID:"wlan0"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'WLAN-676EDD' [AC2]>
                    ESSID:"WLAN-676EDD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=7/100  

##### module infos ######################

[r8712u]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     A0DDC386F212DB329A49CC5
depends:        
staging:        Y
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

[brcmfmac]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.txt
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.txt
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.txt
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.txt
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     26663514B5D324624B97E03
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/4.1.5-040105-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

[brcmfmac]
debug: 0
fcmode: 0
roamoff: 0

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.670594] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done for chip 43340 rev 2 pmurev 20
[    4.752863] brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2
[    5.168975] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    5.172224] r8712u: register rtl8712_netdev_ops to netdev_ops
[    5.172231] usb 1-1.2.1: r8712u: USB_SPEED_HIGH with 4 endpoints
[    5.172889] usb 1-1.2.1: r8712u: Boot from EFUSE: Autoload OK
[    5.745877] usb 1-1.2.1: r8712u: CustomerID = 0x0000
[    5.745881] usb 1-1.2.1: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[    5.745883] usb 1-1.2.1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    7.681039] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[    8.564126] r8712u 1-1.2.1:1.0 wlan0: 1 RCR=0x153f00e
[    8.566641] r8712u 1-1.2.1:1.0 wlan0: 2 RCR=0x553f00e
[    8.697378] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50

########## wireless info END ############


```

---

### Post by Publius_Quinctiliu on 2015-08-16
> **praseodym said:**
> ```
Bus 001 Device 007: ID 0df6:005b Sitecom Europe B.V. 
```
There it is, the right driver r8712u is loaded, but additionally a Broadcom driver (brcmfmac), too.
```

echo "blacklist brcmfmac" | sudo tee /etc/modprobe.d/blacklist-bradcom.conf
```
Reboot

i did that, but with no change. at least i don't see the nvram-file in /efivars/

---

### Post by praseodym on 2015-08-16
Try these module parameters

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
And deactivate IPv6 in the network-manager profile. Check afterwards:
```

iwconfig
dmesg | egrep 'wlan|r8'
sudo iwlist scan
route -n
```

---

### Post by Publius_Quinctiliu on 2015-08-16
how do i open the network manager profile? i have set ipv6 to "ignore" in the wifi-network-properties, but i doubt that this is what you meant, is it? do i have to restart after executing the first three commands you gave to me?

Edit: i have now done your commands, but it is still not showing up.

---

### Post by jeremy31 on 2015-08-16
Is your BIOS the newest version?

And post the results of ```
cat [COLOR=#000000] /sys/bus/platform/drivers/sdhci-acpi/INT33BB\:00/power/control 
```[/COLOR]

---

### Post by Publius_Quinctiliu on 2015-08-16
My Bios is the most recent version, when i tried to flash it in windows it told me that just a few days back. For your command it only gives out "auto" as the only result.

---

### Post by praseodym on 2015-08-16
Check in your BIOS if you can permanently activate wireless there. Check also if you can boot the network before the OS

---

### Post by jeremy31 on 2015-08-16
Check out this thread, it is a bit long as there is info for things other than wifi [http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)
[http://ubuntuforums.org/showthread.php?t=2254322&p=13301726#post13301726](http://ubuntuforums.org/showthread.php?t=2254322&p=13301726#post13301726) should be the info you need to make your [COLOR=#000000]brcmfmac43340-sdio.txt
change ```
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]macaddr=02:0A:F7:2A:3B:4C
``` to whatever the MAC address of the wifi card is, it might be printed on the laptop on a sticker but it should be on the card itself as WFM or similar[/FONT][/COLOR]

---

### Post by Publius_Quinctiliu on 2015-08-16
thanks for your help, but unfortunately that thread does not give me any further help. the problem is still that i don't see the /sys/firmware/efi/efivars/nvram*-entry, so i can not copy it to /lib/firmware/brcm/brcmfmac43340-sdio.txt.

---

### Post by jeremy31 on 2015-08-16
The poster in the second link had the same issue and all that was needed for the /lib/firmware/brcm/brcmfmac43340-sdio.txt was
```
[COLOR=#000000][FONT=Ubuntu Mono]manfid=0x2d0
[/FONT][/COLOR]prodid=0x0653
vendid=0x14e4
devid=0x4386
boardtype=0x0653
boardrev=0x1203
boardnum=22
macaddr=02:0A:F7:2A:3B:4C
sromrev=3
boardflags=0x0090201
xtalfreq=37400
nocrc=1
ag0=255
aa2g=1
aa5g=1
ccode=ALL
pa0itssit=0x20
pa0b0=6747
pa0b1=-808
pa0b2=-178
tssifloor2g=69
rssismf2g=0xf
rssismc2g=0x8
rssisav2g=0x1
cckPwrOffset=3
rssismf5g=0xf
rssismc5g=0x7
rssisav5g=0x3
pa1lob0=5659
pa1lob1=-693
pa1lob2=-178
tssifloor5gl=93
pa1b0=5172
pa1b1=-671
pa1b2=-212
tssifloor5gm=77
pa1hib0=5320
pa1hib1=-663
pa1hib2=-179
tssifloor5gh=74
rxpo5g=0
maxp2ga0=0x4E
cck2gpo=0x0000
ofdm2gpo=0x42000000
mcs2gpo0=0x2222
mcs2gpo1=0x7662
maxp5ga0=0x46
maxp5gla0=0x46
maxp5gha0=0x46
ofdm5gpo=0x52222222
ofdm5glpo=0x52222222
ofdm5ghpo=0x52222222
mcs5gpo0=0x0000
mcs5gpo1=0x8550
mcs5glpo0=0x0000
mcs5glpo1=0x8550
mcs5ghpo0=0x0000
mcs5ghpo1=0x8550
swctrlmap_2g=0x00080008,0x00100010,0x00080008,0x011010,0x11f
swctrlmap_5g=0x00020002,0x00040004,0x00020002,0x011010,0x2fe
gain=32
triso2g=8
triso5g=8
loflag=0
iqlocalidx5g=40
dlocalidx5g=70
iqcalidx5g=50
lpbckmode5g=1
txiqlopapu5g=0
txiqlopapu2g=0
dlorange_lowlimit=5
txalpfbyp=1
txalpfpu=1
dacrate2xen=1
papden2g=1
papden5g=1
gain_settle_dly_2g=4
gain_settle_dly_5g=4
noise_cal_po_2g=-1
noise_cal_po_40_2g=-1
noise_cal_high_gain_2g=73
noise_cal_nf_substract_val_2g=346
noise_cal_po_5g=-1
noise_cal_po_40_5g=-1
noise_cal_high_gain_5g=73
noise_cal_nf_substract_val_5g=346
cckpapden=0
paparambwver=1
```

And change macaddr to your MAC address

---

### Post by Publius_Quinctiliu on 2015-08-16
sorry jeremy, i did not realise those were 2 links. i copied the file and changed the mac-adress, but unfortunately there is still no wifi.

I have installed kernel 4.1.5; one poster said that kernel 4.1 RC7 is working; is this kernel newer than mine?

---

### Post by jeremy31 on 2015-08-16
4.1 RC7 is older than yours, RC means Release Candidate and there was some info on using commands like ```
echo on | sudo tee [COLOR=#000000][FONT=Ubuntu Mono]/sys/bus/platform/drivers/sdhci-acpi/INT33BB\:00/power/control
sudo modprobe -r brcmfmac
sudo modprobe brcmfmac
```
Then check ```
dmesg | tail
``` to see if the error is still there [/FONT][/COLOR]

---

### Post by Publius_Quinctiliu on 2015-08-16
Yes, i just came back to say that, too. after randomly trying sudo modprobe brcmfmac it finally worked! Even though i have to do this now after every boot i am more than happy! Thank you so much for your help!! Edit: do you know a way that i can execute the command after every login automatically?

---

### Post by jeremy31 on 2015-08-16
It can be automated at boot by adding to the rc.local file
```
gksudo gedit /etc/rc.local
``` and place the following commands above exit 0
```
[COLOR=#000000]rmmod brcmfmac [/COLOR]
[COLOR=#000000]rmmod brcmutil [/COLOR]
[COLOR=#000000]echo on > /sys/bus/platform/drivers/sdhci-acpi/INT33BB\:00/power/control [/COLOR]
[COLOR=#000000]modprobe brcmfmac[/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

Save, exit gedit, and reboot to test[/FONT][/COLOR]

---

### Post by Publius_Quinctiliu on 2015-08-16
thank you, it works now after adding just modprobe brcmfmac to rc.local. with the other entries it did not. Thank you for your help and time!!!

---

### Post by jeremy31 on 2015-08-16
You might be able to remove the line from rc.local after
```
sudo rm [COLOR=#000000][FONT=Ubuntu Mono]/etc/modprobe.d/blacklist-bradcom.conf
```

Unless it is blacklisted somewhere else also[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-08-16
If you have speed or other issues with wifi, change the wifi router encryption settings to WPA2-AES, WPA2-PSK, or WPA2 only.  Now it has TKIP enabled and that usually causes issues.  The wireless script showed
```
**Cell 01 - Address: <MAC '[B]home3**' [AC1]>[/B]**                    ESSID:"[B]home3**"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
```

You really just want to see CCMP for the group and pairwise cipher[/B]

---

### Post by Publius_Quinctiliu on 2015-08-16
> **jeremy31 said:**
> If you have speed or other issues with wifi, change the wifi router encryption settings to WPA2-AES, WPA2-PSK, or WPA2 only.  Now it has TKIP enabled and that usually causes issues.

Thanks, just did that as well. Good night! ):P

---

