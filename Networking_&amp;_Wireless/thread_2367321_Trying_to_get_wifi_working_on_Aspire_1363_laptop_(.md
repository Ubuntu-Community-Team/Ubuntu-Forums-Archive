---
title: "Trying to get wifi working on Aspire 1363 laptop (Inprocom IPN2220 wifi card)"
date: 2017-07-28
forum: Networking &amp; Wireless
---

### Post by achookang on 2017-07-28
Hi,

I am trying to get the wifi card working with a new Lubuntu 17.04 installation.
I have tried to install NDISWRAPPER and it seems to be installed but somehow when I try and load the windows driver it soesn't seem to work. 

I don't get and wifi option in Network Manager at all.

Here is the wifi-info script output:

```
########## wireless info START ##########

Report from: 28 Jul 2017 19:19 BST +0100

Booted last: 28 Jul 2017 00:00 BST +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:31:03 UTC 2017 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:0a.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
    Subsystem: AMBIT Microsystem Corp. T60N871 802.11g Mini PCI Wireless Adapter [1468:0305]
    Kernel modules: ndiswrapper

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102/VT6103 [Rhine-II] [1106:3065] (rev 74)
    Subsystem: Acer Incorporated [ALI] VT6102/VT6103 [Rhine-II] [1025:006e]
    Kernel driver in use: via-rhine

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

##### lsmod #############################

ndiswrapper           200704  0
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s18' [IF1]> brd <MAC address>
    inet 192.168.1.133/24 brd 192.168.1.255 scope global dynamic enp0s18
       valid_lft 85232sec preferred_lft 85232sec
    inet6 fe80::<IP6 'enp0s18' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp0s18   no wireless extensions.

##### route #############################

default via 192.168.1.254 dev enp0s18 proto static metric 100 
192.168.1.0/24 dev enp0s18 proto kernel scope link src 192.168.1.133 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       483     1  0 18:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s18
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         VIA Technologies, Inc.
GENERAL.PRODUCT:                        VT6102/VT6103 [Rhine-II]
GENERAL.DRIVER:                         via-rhine
GENERAL.DRIVER-VERSION:                 1.5.1
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s18' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:12.0/net/enp0s18
GENERAL.IP-IFACE:                       enp0s18
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7390a119-72ba-4845-8f5a-65f03392fac3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7390a119-72ba-4845-8f5a-65f03392fac3 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.133/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1501351195
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.133
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::<IP6 'enp0s18' [IF1]>/64
IP6.GATEWAY:                            

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=PlusnetWireless3857D7
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s18   no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s18   Interface doesn't support scanning.

##### module infos ######################

[ndiswrapper]
filename:       /lib/modules/4.10.0-28-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     5A5BA67E725572B2819B3F6
depends:        
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

ndiswrapper

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
blacklist b43
blacklist b44
blacklist ohci_hcd
blacklist ssb

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

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000017FEd00002220sv00000305sd00001468bc*sc*i* ndiswrapper
alias pci:v000017FEd00002220sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   24.512778] ndiswrapper (load_wrap_driver:103): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[   33.322095] IPv6: ADDRCONF(NETDEV_UP): enp0s18: link is not ready

########## wireless info END ############
```



sudo lshw -C network gives:

```
alan@alan-Aspire-1360:~$ sudo lshw -C network
  *-network:0 UNCLAIMED     
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:1c00(size=32) memory:c0006000-c000601f memory:c0005000-c00057ff
  *-network:1
       description: Ethernet interface
       product: VT6102/VT6103 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: enp0s18
       version: 74
       serial: 00:0a:e4:a1:1f:cc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=192.168.1.133 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:1800(size=256) memory:c0006800-c00068ff
```

Thank you for any help offered!

Alan

---

### Post by chili555 on 2017-07-28
> ndiswrapper (load_wrap_driver:103): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'I suspect that means that the .inf and .sys files are incorrect.

Please check here: [https://ubuntuforums.org/showthread.php?t=2049417](https://ubuntuforums.org/showthread.php?t=2049417)

Poat back if you need a step-by-step.

---

### Post by achookang on 2017-07-28
Thanks for reply. I had seen that thread when searching before. I downloaded the driver files from the link that was posted and tried sudo ndisgtk. The teminal window gave a lot of weird ? error messages (see code box below) 

```
alan@alan-Aspire-1360:~$ sudo ndisgtk
[sudo] password for alan: 
/usr/sbin/ndisgtk:42: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:23:18: not a number

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:23:18: Expected a string.

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:815:10: not a number

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:815:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1953:14: not a number

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1953:14: Expected a string.

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: nautilus.css:50:71: Using one color stop with linear-gradient() is deprecated.

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: nautilus.css:51:71: Using one color stop with linear-gradient() is deprecated.

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-lubuntu.css:252:14: not a number

(ndisgtk:2072): Gtk-WARNING **: Theme parsing error: gtk-lubuntu.css:252:14: Expected a string.
```

and then the window for installing the Wireless Network Drivers came up (the GUI for ndiswrapper I guess?) 
There was already a driver installed for the wifi card, so I chose uninstall, then re-installed by pointing to the downloaded driver from your link.

I get this in the terminal window:
```
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
```

The Wireless Network Drivers window now says: neti2220 Hardware present: yes. 
I can choose "configure network" and enter the SSID and pw but there is still no wifi option in the Network Manager in the bottom corner of the screen.

Not sure what is going wrong!

---

### Post by praseodym on 2017-07-28
You can also try this one

[https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz)

---

### Post by chili555 on 2017-07-28
> **achookang said:**
> The Wireless Network Drivers window now says: neti2220 Hardware present: yes. 
I can choose "configure network" and enter the SSID and pw but there is still no wifi option in the Network Manager in the bottom corner of the screen.

Not sure what is going wrong!What do the logs say?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by achookang on 2017-07-28
> **praseodym said:**
> You can also try this one

[https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz)

Thanks for the link. Unfortunately however I have the same results when trying these drivers too.

---

### Post by achookang on 2017-07-28
ndiswrapper -l gives
```
alan@alan-Aspire-1360:~$ ndiswrapper -l
neti2220 : driver installed
    device (17FE:2220) present
```

dmesg | grep ndis gives
```
[    9.606928] ndiswrapper: loading out-of-tree module taints kernel.
[    9.607567] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[    9.607587] ndiswrapper: module license taints kernel.
[    9.609047] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   24.417512] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[   24.417521] ndiswrapper (load_sys_files:200): couldn't prepare driver 'ipn2220_x64intel_mod'
[   24.418703] ndiswrapper (load_wrap_driver:103): couldn't load driver ipn2220_x64intel_mod; check system log for messages from 'loadndisdriver'
[   24.429589] usbcore: registered new interface driver ndiswrapper
[  515.456899] usbcore: deregistering interface driver ndiswrapper
[  515.540415] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[  515.828850] Modules linked in: ndiswrapper(OE+) edac_mce_amd edac_core input_leds joydev serio_raw i2c_viapro k8temp snd_via82xx_modem snd_via82xx snd_mpu401_uart snd_ac97_codec pcmcia gameport snd_rawmidi snd_seq_device ac97_bus snd_pcm snd_timer snd soundcore via_ircc yenta_socket pcmcia_rsrc pcmcia_core shpchp irda mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 pata_acpi nouveau mxm_wmi wmi i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm psmouse firewire_ohci via_rhine mii firewire_core pata_via crc_itu_t video fjes [last unloaded: ndiswrapper]
[  515.829035] CPU: 0 PID: 1904 Comm: loadndisdriver Tainted: P        W  OE   4.10.0-28-generic #32-Ubuntu
[  515.832024]  ? wrapper_ioctl+0x9af/0xbd0 [ndiswrapper]
[  515.832024]  ? unload_wrap_driver+0x140/0x140 [ndiswrapper]
[  515.850108] ndiswrapper (load_wrap_driver:103): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[  515.857074] usbcore: registered new interface driver ndiswrapper
```

Okay, so something's not right there!  I hope you can help me figure out what :)

The references to ipn2220_x64intel_mod and the 64 bit driver I presume are because I had also previously tried to install that driver (after suggestion of alternative drivers from another poster to this thread) - there were both 32 and 64 bit versions of the driver in the ZIP posted and since I couldn't remember/wasn't sure if I had installed 32 or 64 bit version of Lubuntu, I thought I might as well give them all a go.

---

### Post by chili555 on 2017-07-28
> since I couldn't remember/wasn't sure if I had installed 32 or 64 bit version of Lubuntu,Find out:```
arch
```Now that you've experimented with a few different versions, we're thoroughly confused. May we see:```
cat  /etc/modprobe.d/ndiswrapper.conf
```Throwing one driver after another at the problem is never helpful.

---

### Post by achookang on 2017-07-29
Ah ok sorry about trying the different drivers, it's just I saw on various other threads where I was looking for a solution that sometimes similar problems had been solved by using different ones....

Is there anyway to "clean it up" preferably without having to reinstall the whole OS (although I am willing to do that if absolutely necessary)?

Anyway, cat /etc/modprobe.d/ndiswrapper.conf gives
```
alan@alan-Aspire-1360:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias pci:v000017FEd00002220sv00000310sd00001468bc*sc*i* ndiswrapper
alias pci:v000017FEd00002220sv*sd*bc*sc*i* ndiswrapper
```

Thanks for the tip on using "arch" to find out which version of OS you are using by the way.

---

### Post by chili555 on 2017-07-29
> Is there anyway to "clean it up"Let's try:```
sudo ndiswrapper -e neti2220
sudo rm /etc/modprobe.d/ndiswrapper.conf
```Now install the correct for your architecture; either 32- or 64-bit, driver again. Check the log:```
dmesg | grep ndis
```

Please be reminded that ndiswrapper is getting older and may or may not work.

---

### Post by achookang on 2017-07-29
ok here is what I get now:

```
alan@alan-Aspire-1360:~$ dmesg | grep ndis
[    9.715180] ndiswrapper: loading out-of-tree module taints kernel.
[    9.715825] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[    9.715846] ndiswrapper: module license taints kernel.
[    9.717313] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   24.486263] Modules linked in: ndiswrapper(OE+) parport_pc ppdev lp parport ip_tables x_tables autofs4 pata_acpi nouveau mxm_wmi wmi i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse drm via_rhine firewire_ohci pata_via firewire_core mii crc_itu_t fjes video
[   24.486310] CPU: 0 PID: 249 Comm: loadndisdriver Tainted: P        W  OE   4.10.0-28-generic #32-Ubuntu
[   24.486431]  ? wrapper_ioctl+0x9af/0xbd0 [ndiswrapper]
[   24.486488]  ? unload_wrap_driver+0x140/0x140 [ndiswrapper]
[   24.486896] ndiswrapper (load_wrap_driver:103): couldn't load driver neti2220; check system log for messages from 'loadndisdriver'
[   24.554177] usbcore: registered new interface driver ndiswrapper
[33307.409766] usbcore: deregistering interface driver ndiswrapper
[33307.409929] ndiswrapper (ntoskernel_exit:2671): object df791620(2) was not freed, freeing it now
[33307.479967] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[33307.544022] Modules linked in: ndiswrapper(OE+) edac_mce_amd edac_core joydev input_leds serio_raw k8temp snd_via82xx_modem i2c_viapro snd_via82xx snd_mpu401_uart snd_ac97_codec gameport snd_rawmidi snd_seq_device ac97_bus snd_pcm snd_timer snd soundcore pcmcia via_ircc yenta_socket pcmcia_rsrc pcmcia_core shpchp irda mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 pata_acpi nouveau mxm_wmi wmi i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse drm via_rhine firewire_ohci pata_via firewire_core mii crc_itu_t fjes video [last unloaded: ndiswrapper]
[33307.544022] CPU: 0 PID: 2232 Comm: loadndisdriver Tainted: P      D W  OE   4.10.0-28-generic #32-Ubuntu
[33307.544022]  ? wrapper_ioctl+0x9af/0xbd0 [ndiswrapper]
[33307.544022]  ? unload_wrap_driver+0x140/0x140 [ndiswrapper]
[33307.574148] ndiswrapper (load_wrap_driver:103): couldn't load driver ipn2220_x32w9xme_mod; check system log for messages from 'loadndisdriver'
[33307.582730] usbcore: registered new interface driver ndiswrapper
```

---

### Post by praseodym on 2017-07-29
> ```
[   24.417512] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
```
from the second last outputs. Be sure trying the correect driver

---

