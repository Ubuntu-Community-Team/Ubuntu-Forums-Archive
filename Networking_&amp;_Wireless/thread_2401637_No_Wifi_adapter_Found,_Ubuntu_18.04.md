---
title: "No Wifi adapter Found, Ubuntu 18.04"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by mommashaq89 on 2018-09-20
I am VERY new to the Linux OS and Ubuntu. I am a novice, at best. I know little to nothing about coding. Please bare with me and my language, as it may not be exactly accurate, but I think you will follow. I have tried the suggestion on the post about the wireless driver. I have installed git, dkms etc. I have checked that the wifi and WLAN is enabled in BIOS. I have rebooted after all of these steps and I got nothing. Hopefully you can help. Also, I have an HP laptop. I downloaded Ubuntu on a different HP laptop and had no issues.This one, however, has given me a run for my money. I did install pastebinit(?) and this is what I got. Thanks so much in advance!


```
########## wireless info START ##########

Report from: 20 Sep 2018 10:10 EDT -0400

Booted last: 20 Sep 2018 00:00 EDT -0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84ac]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
	Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
	Kernel modules: wl

##### lsusb #############################

Bus 001 Device 003: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0408:5310 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wl                   6447104  0
cfg80211              622592  1 wl
wmi                    24576  2 wmi_bmof,hp_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 71.81.194.195  netmask 255.255.240.0  broadcast 71.81.207.255
        inet6 2600:6c5e:7005:300:dc4f:2ba1:4e48:7c97  prefixlen 128  scopeid 0x0<global>
        inet6 fe80::f8dd:aa28:dcdd:c663  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1026  bytes 840703 (840.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 917  bytes 123680 (123.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 289  bytes 22835 (22.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 289  bytes 22835 (22.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         71.81.192.1     0.0.0.0         UG    100    0        0 enp2s0
71.81.192.0     0.0.0.0         255.255.240.0   U     100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       689     1  0 10:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

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
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       de5f2d94-9ad8-397f-ba0b-f4604b44d12d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         71.81.194.195/20
IP4.GATEWAY:                            71.81.192.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 71.81.192.1, mt = 100
IP4.ROUTE[2]:                           dst = 71.81.192.0/20, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             71.10.216.1
IP4.DNS[2]:                             71.10.216.2
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.240.0
DHCP4.OPTION[4]:                        domain_name_servers = 71.10.216.1 71.10.216.2
DHCP4.OPTION[5]:                        ip_address = 71.81.194.195
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 68.114.38.212
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = -18000
DHCP4.OPTION[10]:                       broadcast_address = 255.255.255.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 21594
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 12339
DHCP4.OPTION[17]:                       routers = 71.81.192.1
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1537477223
DHCP4.OPTION[21]:                       host_name = mommashaq89-HP-Laptop-15-db0xxx
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       interface_mtu = 576
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 71.81.192.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 0.0.0.0
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       requested_host_name = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 24679
IP6.ADDRESS[1]:                         2600:6c5e:7005:300:dc4f:2ba1:4e48:7c97/128
IP6.ADDRESS[2]:                         fe80::f8dd:aa28:dcdd:c663/64
IP6.GATEWAY:                            fe80::201:5cff:fe65:de46
IP6.ROUTE[1]:                           dst = ::/0, nh = fe80::201:5cff:fe65:de46, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = 2600:6c5e:7005:300:dc4f:2ba1:4e48:7c97/128, nh = ::, mt = 100
IP6.DNS[1]:                             2607:f428:ffff:ffff::1
IP6.DNS[2]:                             2607:f428:ffff:ffff::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:86:9d:9:9c:71:c5:62:de:c9:bd:46:74:cf:71:8e:58
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = 2607:f428:ffff:ffff::1 2607:f428:ffff:ffff::2
DHCP6.OPTION[4]:                        rebind = 483840
DHCP6.OPTION[5]:                        max_life = 604800
DHCP6.OPTION[6]:                        preferred_life = 604800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1537449214
DHCP6.OPTION[10]:                       ip6_address = 2600:6c5e:7005:300:dc4f:2ba1:4e48:7c97
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 302400
DHCP6.OPTION[13]:                       iaid = 86:b9:09:26
DHCP6.OPTION[14]:                       starts = 1537449214
DHCP6.OPTION[15]:                       dhcp6_server_id = 0:1:0:1:4b:73:43:3a:0:14:4f:c3:f6:90
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   de5f2d94-9ad8-397f-ba0b-f4604b44d12d | Wired connection 1

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

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.15.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.15.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/rtl8723de.conf]
options rtl8723de ant_sel=X

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.710402] wl: loading out-of-tree module taints kernel.
[   13.710406] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.272936] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=826c lmp_ver=08 lmp_subver=a99e
[   14.272939] Bluetooth: hci0: rtl: assuming no firmware upload needed

########## wireless info END ############
```

---

### Post by chili555 on 2018-09-20
Please remove the incorrect driver:```
sudo apt purge bcmwl-kernel-source
```Next, check here: [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce)

---

### Post by mommashaq89 on 2018-09-20
I removed the incorrect driver. That link is for a Lenovo think pad and also Ubuntu 17.0 is that the link you meant to send?

---

### Post by mommashaq89 on 2018-09-20
So, I scrolled down to the replies and attempted the options provided just to see. When i input the first section this is what I get.
[IMG]https://ibb.co/fwNc2K[/IMG]
The next step is to scroll down to line 152 to change the text. There is no where to scroll and I cant seem to utilize the options at the bottom. Am I a lost cause here?

---

### Post by chili555 on 2018-09-20
```
That link is for a Lenovo think pad and also Ubuntu 17.0 is that the link you meant to send?
```The salient point is that it is for an rtl8821ce device. It doesn't really matter what laptop brand it's in.> The next step is to scroll down to line 152 to change the text. There is no where to scroll and I cant seem to utilize the options at the bottom. You can certainly scroll with the arrow keys in nano; what seems to be missing is a line counter! Please try:```
gedit Makefile
```The line counter is in the lower right. Don't forget to proofread carefully and Save after you make your change.

Also, you may safely ignore all the warnings in the terminal when you open gedit. I get a warning about a missing theme. We don't care; we just want to modify the text, save and move on.> Am I a lost cause here?Never. There is often more than one way to do things in Ubuntu. We'll get it!

---

### Post by mommashaq89 on 2018-09-20
Ok. So I was able to open the file successfully and see the numbered lines. Progress. Line number 152 was blank. I searched for the line that needed to be replaced and did find it and replaced it. When I tried ctrl+o followed by enter it brought me back to the downloads folder instead of saving. I saved the file manually. When I clicked ctrl+x to exit, again nothing happened, so I manually exited. When I typed in make, I got the error message "No targets specified and no make file found." I tried to sudo make install in case it needed a command. It asked for my password. Then it gave me a similar message saying there was no target file to make. I feel like I take 2 steps forward and 3 steps back. Also, I really appreciate your patience and willingness to help.

---

### Post by chili555 on 2018-09-20
First, please confirm that the change to the Makefile was saved properly.```
cd ~/Downloads/rtl8821ce
less Makefile
```Is the change properly saved? If not, stop and we'll fix that before we proceed.

Get out of 'less' with q.

---

### Post by mommashaq89 on 2018-09-20
> **chili555 said:**
> First, please confirm that the change to the Makefile was saved properly.```
cd ~/Downloads/rtl8821ce
less Makefile
```Is the change properly saved? If not, stop and we'll fix that before we proceed.

Get out of 'less' with q.



No such file or directory. 
I guess that means it didn’t save properly.
When I open my downloads file, its there

---

### Post by chili555 on 2018-09-20
Let's try this another way.```
cd
```That will get you to your home directory. Here is my example:```
chili@T440p:~/Desktop/Forum$ cd
chili@T440p:~$ 
```Now we go to Downloads:```
cd Downloads
```And to the folder you are working on:```
cd rtl8821ce
```Any errors or warnings? No?

List the contents in the folder:```
ls
```Is Makefile among the contents?```
less Makefile
```Is the change properly saved? If not, stop and we'll fix that before we proceed.

Get out of 'less' with q.

---

### Post by mommashaq89 on 2018-09-20
[QUOTE=chili555;13802444]Let's try this another way.```
cd
```That will get you to your home directory. Here is my example:```
chili@T440p:~/Desktop/Forum$ cd
chili@T440p:~$ 
```Now we go to Downloads:```
cd Downloads
```And to the folder you are working on:```
cd rtl8821ce
```Any errors or warnings? No?

List the contents in the folder:```
ls
```Is Makefile among the contents?```
less Makefile
```Is the change properly saved? If not, stop and we'll fix that before we proceed.

Get out of 'less' with q

I’m good till step 3. I can do cd and cd Downloads. Then it says no such file or directory.

---

### Post by chili555 on 2018-09-20
The link I gave you says: > Unless you have specified otherwise in your browser, downloads go to the directory Downloads. Is that not the case for you? Didn't you find the file in Downloads previously? Are you certain that you typed the commands correctly?```
cd
cd Downloads
cd rtl8821ce
```Please try again and I'm crossing my fingers!!!

It's difficult to operate on the directory if you can't even find it.

---

### Post by chili555 on 2018-09-20
Like this: 

[IMG]https://i.postimg.cc/Z5Q8gxTg/Screenshot_from_2018-09-20_19-53-09.png[/IMG]

---

### Post by mommashaq89 on 2018-09-20
Actually, I was able to get to the last step. After typing less Makefile I get a long list of Extra CFLAGS
[IMG]http://tinypic.com/r/4j6kxf/9[/IMG]
EXTRA_CFLAGS += $(USER_EXTRA_CFLAGS)
EXTRA_CFLAGS += -O1
#EXTRA_CFLAGS += -O3
#EXTRA_CFLAGS += -Wall
#EXTRA_CFLAGS += -Wextra
#EXTRA_CFLAGS += -Werror
#EXTRA_CFLAGS += -pedantic
#EXTRA_CFLAGS += -Wshadow -Wpointer-arith -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes

EXTRA_CFLAGS += -Wno-unused-variable
EXTRA_CFLAGS += -Wno-unused-value
EXTRA_CFLAGS += -Wno-unused-label
EXTRA_CFLAGS += -Wno-unused-parameter
EXTRA_CFLAGS += -Wno-unused-function
EXTRA_CFLAGS += -Wno-unused
#EXTRA_CFLAGS += -Wno-uninitialized

GCC_VER_49 := $(shell echo `$(CC) -dumpversion | cut -f1-2 -d.` \>= 4.9 | bc )
ifeq ($(GCC_VER_49),1)
EXTRA_CFLAGS += -Wno-date-time  # Fix compile error && warning on gcc 4.9 and later
endif

---

### Post by chili555 on 2018-09-20
Use the arrow keys to scroll down till you see this:```
export TopDIR ?= $ ~/Downloads/rtl8821ce
```Or, do you see this?```
export TopDIR ?= $(srctree)/drivers/net/wireless/rtl8821ce
```If you see the *first* one, then the changes you made are good and we proceed. Get out of 'less' with q.

Now, before you do anything else, do:```
make
```If the process ends like this:> MODPOST 1 modules
  CC      /home/chili/Downloads/rtl8821ce/8821ce.mod.o
  LD [M]  /home/chili/Downloads/rtl8821ce/8821ce.ko
Then proceed:```
sudo make install
```Reboot.

---

### Post by mommashaq89 on 2018-09-20
. I see the second one.

---

### Post by chili555 on 2018-09-20
Get out of 'less' with q.

Now do:```
gedit Makefile
```Scroll down to line 152 and change the line that now reads:

```
export TopDIR ?= $(srctree)/drivers/net/wireless/rtl8821ce
```
To now read:

```
export TopDIR ?= $ ~/Downloads/rtl8821ce
```Proofread carefully. gedit has a Save button at the upper right. 

If it all goes perfectly, after you Save, close gedit and proceed as above. If you get a clock skew warning, fix it with:```
make clean
find -exec touch \{\} \;
make
sudo make install   
```Reboot.



[IMG]https://i.postimg.cc/mgdSNGzQ/Screenshot_from_2018-09-20_20-39-45.png[/IMG]

---

### Post by mommashaq89 on 2018-09-20
I honestly don't understand what I am doing wrong. I am copying and pasting the exact commands in the exact order. The steps look correct and everything looks like it is proceeding and then when I go back to check, it hasn't saved my changes. Would it be easier at this point for me to just purchase a USB adapter, or will that not work either if I don't get the driver installed?

---

### Post by chili555 on 2018-09-20
Do you mean that the changes to the Makefile aren't saved when you used gedit? Did you click the Save button at the top right before you closed gedit?

Or do you mean something else?

---

### Post by mommashaq89 on 2018-09-20
The changes I made in gedit. Changing the export portion. I clicked the save in the top right corner and it had the save bar loading at the top of the window and that finished fine. Then I exit gedit and go through the steps to less Makefile to see if the changes were successful and it still shows the original srctree etc.  What’s strange to me is that when I reopen the document in gedit, it shows the change, but in less makefile it is incorrect.

---

### Post by chili555 on 2018-09-20
Did you close out of 'less' before you did the gedit? If not, close it out with q and then check again. ```
less Makefile
```I'll bet it's fine!!!

---

### Post by mommashaq89 on 2018-09-20
We did it!!! It took all day, but we did it! I really am an intelligent person I promise, haha although sometimes I'm sure you were wondering. Thank you so much. I am not sure if this is backwards or even allowed, but I went into the actual file, not through gedit and realized that it was editable. I gambled and changed it right there. Went and checked in less Makefile and sure enough, it was correct. I did make and then sudo make install and rebooted and voila! I have wifi! Now I can enjoy all Ubuntu has to offer and I got a crash course in coding. You are awesome!

---

### Post by chili555 on 2018-09-20
Awesome!!

But, we aren't yet done. Please remember to follow the later part of the original post:> EDIT: You have compiled the module for your currently running kernel version only. When Update Manager offers a later kernel version, known as linux-image, after the requested reboot, you must recompile:

```
cd rtl8821ce
make clean
make
sudo make install
sudo modprobe 8821ce
```
Please retain the file and these instructions for that time.

I'm glad it's working by whatever means.

Have fun!

---

### Post by wwonka2 on 2018-10-24
Hello I am using a Broadcom BCM4322 Wireless lan controller (airport extreme) on a mid-2010 MacBook pro and even though the driver is apparently installed, it shows no visible networks, i've been back and forth through forums trying to find a fix and haven't gotten to one yet. I did (although i think i had incorrect drivers) at one point have the networks visible but then i could not authenticate on a Netgear router with WPA2 security. Very new to Linux. Any help is appreciated.

Hopefully i am not violating any rules by posting in this thread

---

### Post by chili555 on 2018-10-24
> **wwonka2 said:**
> Hello I am using a Broadcom BCM4322 Wireless lan controller (airport extreme) on a mid-2010 MacBook pro and even though the driver is apparently installed, it shows no visible networks, i've been back and forth through forums trying to find a fix and haven't gotten to one yet. I did (although i think i had incorrect drivers) at one point have the networks visible but then i could not authenticate on a Netgear router with WPA2 security. Very new to Linux. Any help is appreciated.

Hopefully i am not violating any rules by posting in this threadPlease start your own new thread. You are not likely to get much attention for your Broadcom in a lengthy thread concerning a Realtek.

---

### Post by wwonka2 on 2018-10-24
okay didn't realize that Realtek was the problem at hand. thank you for your response though.

---

### Post by kostheod on 2018-10-26
hello i had the same problem with you with my hp envy 15 in ubuntu 18.04.1. i started downloading drivers but nothing worked.im fairly new to linux myself(specificly 5 days).The answer for me was way easier than i expected.I went to software update made sure that im up to date and then i went to settings.I went to additional drivers and in broadcom limited i togled the option "using broadcom 802.11 linux sta driver..." and then pressed apply changes.After that the secure uefi should ask you to place your password for bios. At this point my wireless networking started working .
the video i used was this one [https://www.youtube.com/watch?v=lCXvEmRCobg](https://www.youtube.com/watch?v=lCXvEmRCobg)
He goes directly to additional drivers.I know it isnt a very advanced solution but since you said you are new to this too it might help you :)

---

