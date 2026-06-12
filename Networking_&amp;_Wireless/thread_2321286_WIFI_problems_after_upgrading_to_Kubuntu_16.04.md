---
title: "WIFI problems after upgrading to Kubuntu 16.04"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by noam4 on 2016-04-21
HI!

I have a Dell XPS 13 2015 9343 laptop in which I installed Kubuntu.
I have upgraded the system to 16.04 from 15.10 and everything seems to work fine except the WIFI driver which doesn't appear anywhere.
I was able to get internet access via USB so i can download the driver and staff.
I would like to mention that I had a problem setting up this driver in the first place in 15.10, the solution was installing [this package]("https://launchpadlibrarian.net/219070203/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu7_amd64.deb") but it doesn't seems to work anymore. 

Will really appreciate any help with this,

Noam

---

### Post by jeremy31 on 2016-04-21
noam4 please see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the contents of the wireless-info.txt file
Please use the code tags [code ] before the output and [/code ] after without the extra space, you can also use the # in advanced reply

---

### Post by noam4 on 2016-04-22
Here is the requested code:

```



########## wireless info START ##########


Report from: 22 Apr 2016 11:07 IDT +0300


Booted last: 22 Apr 2016 00:00 IDT +0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


/usr/share/xsessions/plasma


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
    Kernel modules: bcma, wl


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 008: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 003 Device 007: ID 05e3:0612 Genesys Logic, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:5758 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
Bus 002 Device 003: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 002 Device 020: ID 24ae:2000  
Bus 002 Device 016: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
cfg80211              565248  0
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enx00e04c68010f Link encap:Ethernet  HWaddr <MAC 'enx00e04c68010f' [IF]>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx00e04c68010f' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3308791 (3.3 MB)  TX bytes:827140 (827.1 KB)


##### iwconfig ##########################


enx00e04c68010f  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enx00e04c68010f
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx00e04c68010f
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enx00e04c68010f


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       825     1  0 10:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx00e04c68010f
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB 10/100/1000 LAN
GENERAL.DRIVER:                         r8152
GENERAL.DRIVER-VERSION:                 v1.08.2
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enx00e04c68010f' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1/3-1.1:1.0/net/enx00e04c68010f
GENERAL.IP-IFACE:                       enx00e04c68010f
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     USB Ethernet
GENERAL.CON-UUID:                       b6996867-9b9a-47ef-9451-57f725637a90
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b6996867-9b9a-47ef-9451-57f725637a90 | USB Ethernet
IP4.ADDRESS[1]:                         192.168.1.12/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = NoamLaptopKubuntu
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1461315291
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.12
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 3600
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enx00e04c68010f' [IF]>/64
IP6.GATEWAY:                            


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=false


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TechSec]] (600 root)
[connection] id=TechSec | type=wifi | permissions=user:noam:;
[wifi] mac-address-blacklist= | ssid=TechSec
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Stephen Curry]] (600 root)
[connection] id=Stephen Curry | type=wifi | permissions=user:noam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Stephen Curry
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TechPublic]] (600 root)
[connection] id=TechPublic | type=wifi | autoconnect=false | permissions=user:noam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TechPublic
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Jerusalem (based on set time zone)


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


enx00e04c68010f  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enx00e04c68010f  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[   67.801970] r8152 3-1.1:1.0 eth0: v1.08.2
[   68.725856] r8152 3-1.1:1.0 enx00e04c68010f: renamed from eth0
[   68.749842] IPv6: ADDRCONF(NETDEV_UP): enx00e04c68010f: link is not ready (repeated 2 times)
[   84.075779] IPv6: ADDRCONF(NETDEV_CHANGE): enx00e04c68010f: link becomes ready
[  100.446520] r8152 3-1.1:1.0 enx00e04c68010f: Stop submitting intr, status -71
[  146.461910] r8152 3-1.1:1.0 eth0: v1.08.2
[  149.520909] r8152 3-1.1:1.0 enx00e04c68010f: renamed from eth0
[  149.542946] IPv6: ADDRCONF(NETDEV_UP): enx00e04c68010f: link is not ready (repeated 2 times)
[  173.101293] IPv6: ADDRCONF(NETDEV_CHANGE): enx00e04c68010f: link becomes ready
[  287.150565] [UFW BLOCK] IN=enx00e04c68010f OUT= MAC=01:00:5e:00:00:01:00:21:04:49:9f:20:08:00 SRC=1.1.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 5 times)
[  853.768316] [UFW BLOCK] IN=enx00e04c68010f OUT= MAC=<MAC 'enx00e04c68010f' [IF]>:00:21:04:49:9f:20:08:00 SRC=192.168.1.1 DST=192.168.1.12 LEN=77 TOS=0x00 PREC=0x20 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=19533 LEN=57 
[  853.863344] [UFW BLOCK] IN=enx00e04c68010f OUT= MAC=<MAC 'enx00e04c68010f' [IF]>:00:21:04:49:9f:20:08:00 SRC=192.168.1.1 DST=192.168.1.12 LEN=77 TOS=0x00 PREC=0x20 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=1429 LEN=57 
[  853.979026] [UFW BLOCK] IN=enx00e04c68010f OUT= MAC=<MAC 'enx00e04c68010f' [IF]>:00:21:04:49:9f:20:08:00 SRC=192.168.1.1 DST=192.168.1.12 LEN=83 TOS=0x00 PREC=0x20 TTL=64 ID=0 DF PROTO=UDP SPT=53 DPT=62530 LEN=63  (repeated 2 times)
[  912.792107] [UFW BLOCK] IN=enx00e04c68010f OUT= MAC=01:00:5e:00:00:01:00:21:04:49:9f:20:08:00 SRC=1.1.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 


########## wireless info END ############

```

I would like to say that it seems that the wireless device is recognised but it's icon doesn't appear in the statusbar:
[[IMG]http://s31.postimg.org/nlu30qvqv/wifi.jpg[/IMG]]("http://postimg.org/image/nlu30qvqv/")

---

### Post by noam4 on 2016-04-22
I would like to add that when I am trying to save the connection settings of a wireless network that was saved on the computer, I am getting this message:
[[img]http://s31.postimg.org/axb3h8f5j/wifi2.jpg[/img]](http://postimg.org/image/axb3h8f5j/)

---

### Post by jeremy31 on 2016-04-22
Choose a download site from [http://packages.ubuntu.com/xenial/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/xenial/amd64/bcmwl-kernel-source/download)
Install this version as it was made for 16.04.  The one from launchpad for 15.10 likely had a build issue because it was missing a patch for the 4.4 kernel

---

### Post by noam4 on 2016-04-23
Sadly it didn't help.
Seems like a it's a problem with the secure boot.
While I was upgrading I was asked to enable secure boot.
Here is a very similar post from guy who have a very similar system (XPS 13): [here]("http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04?newreg=5a4c9d1fa86747e2845ccfd5024fbe6d")

---

### Post by jeremy31 on 2016-04-23
That askubuntu link is scary if it is true.  To think that disabling Secure Boot would cause BIOS to say there isn't an OS is troubling

I am not aware of Dell using a BIOS whitelist for wifi cards so it should be possible to replace the Broadcom with an Intel card, 7260, 3165

I hope your Dell is easier to replace the wifi card than my Inspiron N411Z was.  There is probably a video on youtube on how to replace the wifi card but if you don't think you can handle it there are USB wifi dongles on thinkpenguin.com and I have a TP-Link  TL-WN722N 150Mbps model that is plug and play

---

### Post by noam4 on 2016-04-24
It's a little bit sad to say I dont have the option to use the WIFI device which worked in an earlier version of the OS...
If I were to delete my installation and then reinstall 15.10, will I be able to reuse the WIFI deviec?

---

### Post by jeremy31 on 2016-04-24
I wouldn't reinstall 15.10 but use 14.04 as it is a Long Term Support release or reinstall 16.04 and don't enable Secure Boot and see if it works.  I am using 16.04 in UEFI without Secure Boot enabled on my Lenovo

I would think you could use your wifi device in any version as long as Secure Boot isn't enabled.

---

### Post by noam4 on 2016-04-24
OK, the problem is that I am running on Dual boot with windows 10 which maked it a bit complicated... How can I disable secure boot without making any harm to my system? Is there a guide out there?

edit: I have disabled secure boot and now WIFI connection works very well. Then another problem occured - sound works on kubuntu and right after I reboot the system sound doesn't work on both OSs. I tried to re-enable secure boot, and then sound is good but WIFI isn't recognized again. I think that I should keep secureboot OFF and to find a way to make the sound work (since it worked one time - until I restarted the computer).

edit 2: enabling and disabling sound in BIOS settings do the trick. closed. thanks

---

### Post by jeremy31 on 2016-04-24
With secure boot on try ```
sudo modprobe -v wl
```

Post any errors

---

### Post by jeremy31 on 2016-04-24
How is this solved?  Your reply may help others

---

### Post by FrodeA on 2016-05-13
> **jeremy31 said:**
> How is this solved?  Your reply may help others

I had exactly the same problem with Ubuntu 16.04 on my XPS 13 9343. Had to disable secure boot - then it worked like a charm :-)

See also "askubuntu" - [http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04?newreg=5a4c9d1fa86747e2845ccfd5024fbe6d](http://askubuntu.com/questions/760075/cant-view-wifi-networks-after-upgrading-to-ubuntu-16-04?newreg=5a4c9d1fa86747e2845ccfd5024fbe6d).

Hope this can help others.

---

