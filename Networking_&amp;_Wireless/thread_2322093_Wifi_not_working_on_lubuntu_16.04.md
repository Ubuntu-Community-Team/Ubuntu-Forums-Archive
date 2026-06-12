---
title: "Wifi not working on lubuntu 16.04"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by markkasville on 2016-04-26
Hi,

I just switched from ubuntu 14.04 to lubuntu 16.04 and I cannot connect to wireless network (surprise...). I've been going through several other threads dealing with this issue, but I haven't been able to fix it. 
Here is my wireless info: 
```

########## wireless info START ##########

Report from: 26 Apr 2016 13:02 EEST +0300

Booted last: 26 Apr 2016 00:00 EEST +0300

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

Lubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e07e]
    Kernel modules: bcma, wl

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:0860]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b47f Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0489:e055 Foxconn / Hon Hai 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
cfg80211              565248  0
video                  40960  2 i915,acer_wmi
wmi                    20480  1 acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d7b1:30e0:6150:a65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3542014 (3.5 MB)  TX bytes:378779 (378.7 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       546     1  0 12:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6a85500c-5922-4329-a7aa-0c58268acbd4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6a85500c-5922-4329-a7aa-0c58268acbd4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.251/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.251
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
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1461750956
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = Markkasaspire
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::d7b1:30e0:6150:a65/64
IP6.GATEWAY:                            

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
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Helsinki (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   11.498159] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   11.498167] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   23.999201] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   24.166644] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[   24.166724] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   25.809168] r8169 0000:03:00.0 enp3s0: link up
[   25.809183] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############


```

I'd appreciate your help :)

---

### Post by ajgreeny on 2016-04-26
As you have found and used the wireless info script I assume you may have already seen and done all that is at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) but just in case I show it again for you to try.

Can I also check that you have fully updated the machine using an ethernet cable connection; it will make this a lot easier if you can do that.

---

### Post by markkasville on 2016-04-26
Yes, my machine is up to date and yes I've read that thread too. I have been removing bcmwl-kernel-source and reinstalling it. I have also tried with firmware-b43-installer, but no luck so far.

---

### Post by Bucky Ball on 2016-04-26
Try this:

```
sudo apt install b43-fwcutter firmware-b43-installer
```

... and reboot.

Also, have you looked in 'Additional Drivers', if Lubuntu has that, after an update/upgrade?

Run these two in 16.04 LTS:

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by markkasville on 2016-04-26
I've tried that already, but I gave it a go one more time. Did not work :/

---

### Post by brian127 on 2016-04-30
Thanks Bucky Ball, your 
"sudo apt install b43-fwcutter firmware-b43-installer"

instruction fixed the problem on my Asus A6 laptop using lubuntu.

Cheers

---

### Post by Marvin Stodolsky on 2016-07-21
My hardware problem and solution were somewhat different from those already posted, so herein is my report.
My hardware is a MacbookAir, whose internal diagnostics reports wireless type: Broadcom BCM43xx.
The Linux Open Source drivers b43 and bcmXX drivers are not effective. 
However, upon booting with a 14.04-64bit Ubuntu_Install USB, the wl.ko driver could be installed by opening a Gnome-terminal
$ sudo su root
# apt-get install bcmwl-kernel-source
with reported install to /lib/modules/KernelVersion/updates/dkms/wl.ko  (or similar, not under Linux now)
This did support my wireless router access through the NetWork manager icon.
Should you like to get the driver package, find its folder with:
# find / -name bcmwl
as its install depends on the dkms toolset, also find its folder with:
# find /  -name dkms
Copy the *.deb files to a USB stick to for usage later.  Note that the wl.ko  is specific to the kernel it is compiled under. Display KernelVersion with:
$ uname -a
With some Linux installations, compiling support may not initially be adequate to thereon install and compile dkms and wl.ko through it.

After the Lubuntu with same KernelVersion was installed and booted up, the standard target folder was created with:
$ sudo su root 
# mkdir -p /lib/modules/KernelVersion/updates/dkms/
The USB stick auto-mounted. A copy therefrom was done:
# cp wl,ko /lib/modules/KernelVersion/updates/dkms/
Informing the System of its presence with:
# depmod -a
was without a problem report.  Thereafter the module auto-loaded upon boot up, as reported afterward by:
# lsmod | grep wl
which reported both b43 and wl loaded. Try it.
However only the loopback "lo" channel and no wireless channel, was reported by
# ifconfig

After trying various, the following reproducibly worked. 
Unloading the b43 driver with:
# modprobe -r b43
to eliminate possible interference between the two drivers.
# ifconfig
still did not report a wireless channel.  But after a:
# modprobe -r wl
to clear any muddled history, a subsequent loading with
# modprobe wl
did promote creation of a  wireless channel wl_something as reported by:
# ifconfig 
At this point searching for wireless routers can be done with the tool iwlist:
# iwlist wl_something scan
which did include my router with ESSID: FavoritePetName  

For reasons obscure, an initial loading of the b43 (just once) was Essential.  Success was not achieved if bootup loading of b43 was blocked  by BlackListing in the /etc/modprobe.d/ files
When similar stratagems would be necessary with other wireless hardware and drivers, I cannot assess. But that is what the BlackList files were setup for.

ONLY AFTER a wireless channel is confirmed by:
# ifconfig
is it worth proceeding further. But given a success, the Networking setup panels were accessed.  
Selecting to ADD a WiFi channel,  I entered my 
ESSID: RouterName 
WPA2  password
and Internet access was thereafter automagic.  I'm not sure whether entering the nm-applet was suggested in an earlier post is essential or not.

Hope this helps some of you.

MarvS

---

### Post by Bucky Ball on 2016-07-21
> **Marvin Stodolsky said:**
> Hope this helps some of you.

As this is a solved thread which was solved two months ago by one command 

```
sudo apt install b43-fwcutter firmware-b43-installer
```

... and doesn't seem related to what you've posted (you're using a Macbook Air for starters and different issue by the looks of it), it's unlikely to be seen by many people at all, but you might want to consider asking it to be moved to ***Tutorials*** where it will be of the most benefit and have a better chance of being seen. 

To do so, hit the 'Report Post' button on the post and ask staff to move it, we will discuss and get back to you. It has little to no chance of helping anyone here, but thanks for sharing. ;)

---

### Post by jjcase337 on 2016-08-21
@                                      [                                                     [IMG]https://ubuntuforums.org/customavatars/avatar504316_19.gif[/IMG]                                              ]("https://ubuntuforums.org/member.php?u=504316")                                                                                     [**[COLOR=#C61919][B]Bucky Ball**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=504316") Thank you. This was the one that fixed it for me. Now the wifi signals have come up again. The other proprietary driver  wouldn't work after applying changes in software & updates/ Additional drivers.

sudo apt update
sudo apt full-upgrade

---

### Post by prasanth-sunrise on 2016-12-03
> **Bucky Ball said:**
> Try this:

```
sudo apt install b43-fwcutter firmware-b43-installer
```

... and reboot.

Also, have you looked in 'Additional Drivers', if Lubuntu has that, after an update/upgrade?

Run these two in 16.04 LTS:

```
sudo apt update
sudo apt full-upgrade
```


This worked in lubuntu-16.10. Thanks

---

### Post by Bucky Ball on 2016-12-03
A pleasure. ;)

---

### Post by beto1211 on 2017-03-15
Does anyone knows if this procedure works with a usb stick running version of lubuntu 16.10?

---

### Post by jeremy31 on 2017-03-15
> **beto1211 said:**
> Does anyone knows if this procedure works with a usb stick running version of lubuntu 16.10?

If you are referring to ```
sudo apt-get update && sudo apt-get install firmware-b43-installer
```
Sometimes it works but you have to unload and load the b43 and ssb modules so that it will attempt to load the firmware.  If the USB isn't persistent, then the commands will have to be redone after every boot

---

### Post by juergen-sly on 2017-12-05
> **jeremy31 said:**
> If you are referring to ```
sudo apt-get update && sudo apt-get install firmware-b43-installer
```
Sometimes it works but you have to unload and load the b43 and ssb modules so that it will attempt to load the firmware.  If the USB isn't persistent, then the commands will have to be redone after every boot

Tried it several times, still the wifi dongel doesn't connect and what a surprise the bluetooth dossn't work as well after the update and upgrade from 14.04 to 16.04.3 LTS, what a regression, started to transfers the data to my stereo receiver again with a cable, this works. :D

---

### Post by jeremy31 on 2017-12-05
> **juergen-sly said:**
> Tried it several times, still the wifi dongel doesn't connect and what a surprise the bluetooth dossn't work as well after the update and upgrade from 14.04 to 16.04.3 LTS, what a regression, started to transfers the data to my stereo receiver again with a cable, this works. :D
You should have started a new thread with results from the wireless script in my signature.  It is not a regression with some Broadcom wifi and bluetooth devices as Broadcom refuses to change their firmware license so it can be distributed with Ubuntu.  I do have a Broadcom BCM4313 that bluetooth and wifi worked out of the box with no hoops to jump through

---

### Post by kovlus on 2018-05-31
I'd the same problem, this code works for me:
sudo apt install b43-fwcutter firmware-b43-installer

---

