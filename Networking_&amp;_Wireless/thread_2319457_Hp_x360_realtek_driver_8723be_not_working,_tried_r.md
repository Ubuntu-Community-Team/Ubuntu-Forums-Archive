---
title: "Hp x360 realtek driver 8723be not working, tried rtlwifi"
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by Karolina.K on 2016-04-04
Hej I installed ubuntu on my hp pavilion x360 and the wifi didn't work. did a google search and found many solutions, did them but none seems to work. i got the wifi working for 30min but then next time i started the computer it was completly gone, now i cant even see wifi as an option in the network menu. please help, i have tried all solutions i can find, and it seems to not solve anything.

---

### Post by chili555 on 2016-04-04
So that we can diagnose the issue fully, please provide the result of the wireless script from here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Karolina.K on 2016-04-04
okej, here the result is :) 



```
########## wireless info START ##########


Report from: 04 Apr 2016 15:44 CEST +0200


Booted last: 04 Apr 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:8074]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:804c]


04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 007: ID 0fce:71ba Sony Ericsson Mobile Communications AB 
Bus 001 Device 002: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl_pci                40960  0
rtlwifi               135168  1 rtl_pci
mac80211              733184  2 rtl_pci,rtlwifi
cfg80211              548864  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enx0211030a007d Link encap:Ethernet  HWaddr <MAC 'enx0211030a007d' [IF]>  
          inet addr:192.168.42.19  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx0211030a007d' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6078 errors:3 dropped:0 overruns:0 frame:3
          TX packets:5170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4513288 (4.5 MB)  TX bytes:1113654 (1.1 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


enx0211030a007d  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx0211030a007d
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx0211030a007d
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx0211030a007d


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1113     1  0 15:17 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx0211030a007d
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        D6603
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx0211030a007d' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/enx0211030a007d
GENERAL.IP-IFACE:                       enx0211030a007d
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       dfd4a1f7-cbe7-40ca-9a18-bb9d92b8ac1a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dfd4a1f7-cbe7-40ca-9a18-bb9d92b8ac1a | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.19/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.19
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1459779508
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = karolina-HP-Pavilion-x360-Convertible
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx0211030a007d' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


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


[[/etc/NetworkManager/system-connections/SJ]] (600 root)
[connection] id=SJ | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SJ
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Stockholm (based on set time zone)


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


enp2s0    no frequency information.


enx0211030a007d  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


enx0211030a007d  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl_pci]
filename:       /lib/modules/4.2.0-34-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     FB5152C16B54885EE27E3CA
depends:        mac80211,rtlwifi
vermagic:       4.2.0-34-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/4.2.0-34-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     F1626659AE2FC6355721878
depends:        mac80211,cfg80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


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
blacklist acer_wmi


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


[/etc/modprobe.d/iwlwifi-opt.conf]
11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0 ips=0 ant_sel=2


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    6.175479] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.351799] r8169 0000:02:00.0 enp2s0: link down
[    6.351864] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   64.741607] rndis_host 1-4:1.0 enx0211030a007d: renamed from usb0
[   64.796993] IPv6: ADDRCONF(NETDEV_UP): enx0211030a007d: link is not ready


########## wireless info END ############
```

---

### Post by chili555 on 2016-04-04
What is the result and possibly the interesting errors or warnings, if you do:```
sudo modprobe rtl8723be
```

---

### Post by Karolina.K on 2016-04-04
it says this then:

karolina@karolina-HP-Pavilion-x360-Convertible:~$ sudo modprobe rtl8723be
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/iwlwifi-opt.conf line 1: ignoring bad line starting with '11n_disable=1'
modprobe: ERROR: could not insert 'rtl8723be': Invalid argument

---

### Post by chili555 on 2016-04-04
Let's fix these errors and see if we can get the wireless going. First:```
sudo rm /etc/modprobe.d/iwlwifi-opt.conf
```Next, this is caused by a bad build:> modprobe: ERROR: could not insert 'rtl8723be': Invalid argument With a working internet connection, please do:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtlwifi_new.git
```If it reports that rtlwifi-new already exists, then do:```
sudo rm -r rtlwifi-new
```...and then git clone the latest as above. In either event:```
cd rtlwifi-new
make
sudo make install
```Reboot.

You will have compiled the driver for your current kernel version only. When Update Manager installs a newer kernel version, also known as linux-image, after the requested reboot, recompile:

```
cd rtlwifi-new
make clean
make
sudo make install
```Reboot.

Please retain the file and these instructions for that time.

I would probably clean this up, as well:```
sudo gedit /etc/modprobe.d/rtl8723be.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. The file currently reads:> options rtl8723be fwlps=0 ips=0 ant_sel=2
I think you will be just fine by amending it to read:```
options rtl8723be ant_sel=2
```Proofread carefully, save and close the text editor.

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo gedit /etc/default/crda

```Change the last line to read:

    ```
REGDOMAIN=IS

```
Proofread carefully, save and close the text editor.

Reboot and tell us if the wireless is working.

---

### Post by ronald-s on 2016-04-05
Hello Chili555,

I have followed your instructions in the past to get my wifi working with success (thank you).
Since yesterday's Ubuntu update, my wifi will not work. Re-dong the steps that worked in the past do not work now. Plus I have followed the instructions you have given above to miamoto2 without success.[COLOR=#000000] 
[/COLOR]I am a novice, do I post the [COLOR=#000000]results of the wireless script here and join this or start a new thread?
[/COLOR]Best regards,

---

### Post by chili555 on 2016-04-05
> **ronald-s said:**
> Hello Chili555,

I have followed your instructions in the past to get my wifi working with success (thank you).
Since yesterday's Ubuntu update, my wifi will not work. Re-dong the steps that worked in the past do not work now. Plus I have followed the instructions you have given above to miamoto2 without success.[COLOR=#000000] 
[/COLOR]I am a novice, do I post the [COLOR=#000000]results of the wireless script here and join this or start a new thread?
[/COLOR]Best regards,Rather than tack on to another post and confuse poor old Chili as to whose results are whose, please start your own new thread and include the wireless-info from the sticky at the top of the forum.

---

### Post by Karolina.K on 2016-04-05
hej I tried with the solution you gave and it didn't work :( the wireless is still not even seenable from the network menu

---

### Post by chili555 on 2016-04-05
May I please see a new wireless-info?

---

### Post by Karolina.K on 2016-04-05
i tried adding it now, but the forum says that its 15 images of 8 allowed ( no images as far as I know) so It wont post :(

---

### Post by chili555 on 2016-04-05
Images? It's a text file. Just attach the text file to your reply.

---

### Post by Karolina.K on 2016-04-05
[ATTACH]268198[/ATTACH]

okej here it is :) the txt file didnt want to attach either so i put the tar.gz

---

### Post by chili555 on 2016-04-05
Please remove the USB wireless. Then do:```
sudo modprobe -r rt2800usb
sudo modprobe rtl8723be
```What are the messages, warnings, errors, etc.?

---

### Post by Karolina.K on 2016-04-05
on the first one it didnt say anything

and on the second it said this: modprobe: ERROR: could not insert 'rtl8723be': Invalid argument

---

### Post by Karolina.K on 2016-04-05
I restarted it randomly now, and now the wifi works, don't know why it didn't work before but im a bit suspicious that it might break again or something.

---

### Post by chili555 on 2016-04-05
> **miyamoto2 said:**
> I restarted it randomly now, and now the wifi works, don't know why it didn't work before but im a bit suspicious that it might break again or something.Post back if it does. We'll be happy to help.

---

### Post by ronald-s on 2016-04-10
> **chili555 said:**
> Rather than tack on to another post and confuse poor old Chili as to whose results are whose, please start your own new thread and include the wireless-info from the sticky at the top of the forum.
Thank you, I will not have to start a new thread as my connection is miraculously working today after letting it sit for a few days (?!) . I suppose your instructions have worked and that maybe 3rd reboot was all that was needed. I thank you all for the great support info I have used over the past year.

---

