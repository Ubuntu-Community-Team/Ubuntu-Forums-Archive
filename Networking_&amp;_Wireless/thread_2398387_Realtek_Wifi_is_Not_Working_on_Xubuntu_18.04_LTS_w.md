---
title: "Realtek Wifi is Not Working on Xubuntu 18.04 LTS with RTL8723BU"
date: 2018-08-11
forum: Networking &amp; Wireless
---

### Post by boundule on 2018-08-11
I have just installed latest **Xubuntu 18.04 LTS **on my new purchased low config laptop along side Windows 10 (duel boot). Everything of Installation was working fine but the Wifi is not working. Sometimes (rarely) i was able to connect to my wifi router but the network strength is too much week. **My laptop uses realtek driver (may be RTL8723BU) for wifi.** It is working fine in Windows 10 system. From inxi -Fxz command I found that my Network card not installed somehow. In Xumuntu I am now totally without internet. Here I want to add that I have no Wired LAN option in this laptop. 


[SIZE=3][COLOR=#ff0000]**How can I fix / solve this wifi / network card problem??**[/COLOR][/SIZE]

[SIZE=2]**inxi -Fxz**[/SIZE]
```

System:    Host: BUDDY Kernel: 4.15.0-30-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31)
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Walton product: Prelude R1 serial: N/A
           Mobo: N/A model: N/A serial: N/A
           UEFI: American Megatrends v: WH-BI-14-Y116AR120-105-C date: 03/13/2018
CPU:       Dual core Intel Celeron N3350 (-MCP-) arch: N/A cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 4377
           clock speeds: max: 2400 MHz 1: 869 MHz 2: 861 MHz
Graphics:  Card: Intel Device 5a85 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 500 (Broxton 2x6)
           version: 4.5 Mesa 18.0.5 Direct Render: Yes
Audio:     Card Intel Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster
           driver: snd_hda_intel bus-ID: 00:0e.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-30-generic
Network:   Card: Failed to Detect Network Card!
Drives:    HDD Total Size: 1008.2GB (1.2% used)
           ID-1: /dev/sda model: HGST_HTS541010B7 size: 1000.2GB
           ID-2: USB /dev/sdb model: Transcend_8GB size: 8.0GB
Partition: ID-1: / size: 19G used: 4.6G (27%) fs: ext4 dev: /dev/sda7
           ID-2: /home size: 35G used: 51M (1%) fs: ext4 dev: /dev/sda9
           ID-3: swap-1 size: 6.14GB used: 0.00GB (0%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 166 Uptime: 37 min Memory: 397.8/3778.5MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

[SIZE=2]**lspci; lsusb**[/SIZE]
```

00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)
00:00.1 Signal processing controller: Intel Corporation Device 5a8c (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 5a85 (rev 0b)
00:0e.0 Audio device: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b)
00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)
00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)
00:16.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #1 (rev 0b)
00:16.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #2 (rev 0b)
00:16.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #3 (rev 0b)
00:16.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #4 (rev 0b)
00:17.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #5 (rev 0b)
00:17.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #6 (rev 0b)
00:17.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #7 (rev 0b)
00:17.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series I2C Controller #8 (rev 0b)
00:18.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #1 (rev 0b)
00:18.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #2 (rev 0b)
00:18.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #3 (rev 0b)
00:18.3 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series HSUART Controller #4 (rev 0b)
00:19.0 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #1 (rev 0b)
00:19.1 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #2 (rev 0b)
00:19.2 Signal processing controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SPI Controller #3 (rev 0b)
00:1c.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 09da:c10a A4Tech Co., Ltd. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**usb-devices | awk '/b720/' RS=**
```

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=04 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b720 Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8xxxu

```

---

### Post by kc1di on 2018-08-11
Is it possible to connect that machine via Ethernet cable?

---

### Post by praseodym on 2018-08-11
If LAN works, try

```
sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
iwconfig
```

---

### Post by jeremy31 on 2018-08-11
Download [https://www.dropbox.com/s/pog7bujlmap5mn4/8723bu.ko?dl=0](https://www.dropbox.com/s/pog7bujlmap5mn4/8723bu.ko?dl=0) in windows and copy the file to Ubuntu desktop, then in terminal
```
sudo cp 8723bu.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a

```

Reboot and wifi should work, then do
```
sudo apt install git build-essential dkms
git clone https://github.com/lwfinger/rtl8723bu.git
sudo dkms add rtl8723bu
```

Then it should build when new kernels are installed

---

### Post by boundule on 2018-08-11
the out put..

> 


########## wireless info START ##########


Report from: 11 Aug 2018 19:37 +06 +0600


Booted last: 11 Aug 2018 00:00 +06 +0600


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.15.0-30-generic #32-Ubuntu SMP Thu Jul 26 17:42:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Xubuntu


##### lspci #############################




##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 058f:5608 Alcor Micro Corp. 
Bus 001 Device 004: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 09da:c10a A4Tech Co., Ltd. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
cfg80211              622592  2 8723bu,mac80211


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback




##### ifconfig ##########################


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6482  bytes 390514 (390.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6482  bytes 390514 (390.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx88835db994da: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.207  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::bf36:f88b:db7e:26c5  prefixlen 64  scopeid 0x20<link>
        ether 88:83:5d:b9:94:da  txqueuelen 1000  (Ethernet)
        RX packets 76  bytes 37970 (37.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 113  bytes 20222 (20.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


wlx88835db994da  IEEE 802.11  ESSID:"buddy7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 3E:97:0F:B5:03:E0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:32   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    600    0        0 wlx88835db994da
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx88835db994da
192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlx88835db994da


##### resolv.conf #######################




nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root       577     1  0 18:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx88835db994da
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.15.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         88:83:5D:B9:94:DA
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/usb1/1-7/1-7:1.2/net/wlx88835db994da
GENERAL.IP-IFACE:                       wlx88835db994da
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     buddy7
GENERAL.CON-UUID:                       e5fe578a-d3aa-4f7c-ab00-a0a747b5d870
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
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
IP4.ADDRESS[1]:                         192.168.43.207/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.43.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.43.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.207
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1533998195
DHCP4.OPTION[20]:                       host_name = BUDDY
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::bf36:f88b:db7e:26c5/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e5fe578a-d3aa-4f7c-ab00-a0a747b5d870 | buddy7




SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
buddy7  3E:97:0F:B5:03:E0  Infra  6     2437 MHz  65 Mbit/s  48      &#9602;&#9604;__  WPA2      yes     *      


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########




---

### Post by boundule on 2018-08-16
> **jeremy31 said:**
> Download [https://www.dropbox.com/s/pog7bujlmap5mn4/8723bu.ko?dl=0](https://www.dropbox.com/s/pog7bujlmap5mn4/8723bu.ko?dl=0) in windows and copy the file to Ubuntu desktop, then in terminal
```
sudo cp 8723bu.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a

```

Reboot and wifi should work, then do
```
sudo apt install git build-essential dkms
git clone https://github.com/lwfinger/rtl8723bu.git
sudo dkms add rtl8723bu
```

Then it should build when new kernels are installed


The wifi signal is so weak. sometimes not connected. if router is only 1 m distance then it work only

---

### Post by boundule on 2018-09-04
[COLOR=#242729][FONT=Arial]**My problem was solved by Following way:**

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]**1st Step:**[/FONT][/COLOR]
```
sudo apt install build-essential dkms
sudo apt install git
git clone [https://github.com/lwfinger/rtl8723bu.git](https://github.com/lwfinger/rtl8723bu.git)
sudo apt install libelf-dev
```
[COLOR=#242729][FONT=Arial]**2nd Step:**[/FONT][/COLOR]
```
sudo -i
echo blacklist rtl8xxxu >> /etc/modprobe.d/blacklist.conf
exit
```
[COLOR=#242729][FONT=Arial]This ensured that the old driver was not be used for my device. In my case the problematic driver was rtl8xxxu. So I black listed it.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial][B]
3rd Step:[/B] Now I disabled a line in the makefile of the new driver, because without this hack, two instances of the wireless chipset was shown in Network Manager[/FONT][/COLOR]
```
cd rtl8723bu
nano Makefile
```
[COLOR=#242729][FONT=Arial]Go down to line 21 and change this line:[/FONT][/COLOR]
```
EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
```
[COLOR=#242729][FONT=Arial]To comment it out, like this:[/FONT][/COLOR]
```
#EXTRA_CFLAGS += -DCONFIG_CONCURRENT_MODE
```
[COLOR=#242729][FONT=Arial]Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]
4th Step:[/B] Now build and install the driver:[/FONT][/COLOR]
```
source dkms.conf
sudo mkdir /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION
sudo cp -r core hal include os_dep platform dkms.conf Makefile rtl8723b_fw.bin /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION
sudo dkms add $PACKAGE_NAME/$PACKAGE_VERSION
sudo dkms autoinstall $PACKAGE_NAME/$PACKAGE_VERSION
```
[COLOR=#242729][FONT=Arial]**5th Step:** Finally, install the compiled module with this command:[/FONT][/COLOR]
```
make
sudo make install
```
[COLOR=#242729][FONT=Arial]***Reboot your computer.***[/FONT][/COLOR]

---

### Post by ludwig00 on 2018-09-21
Hi, I have the same problem. I try to use your method, but I'm blocked at "source dkms.conf". Bash can't find it...

---

### Post by jeremy31 on 2018-09-21
Try
```
cd ~
sudo dkms add rtl8723bu
sudo dkms install rtl8723bu/4.3.6.11_12942.20141204_BTCOEX20140507-4E40
cd rtl8723bu
sudo cp rtl8723*.bin /lib/firmware/rtlwifi/
```
Reboot

---

