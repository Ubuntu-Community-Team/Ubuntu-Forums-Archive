---
title: "Wired connection doesn't work after suspend in Ubuntu 16.04 LTS"
date: 2017-09-09
forum: Networking &amp; Wireless
---

### Post by garakchy on 2017-09-09
Wired connection doesn't connect after suspending PC and starting it back. The system is Ubuntu 16.04 LTS.

Output of ```
lspci
``` command:

```
00:00.0 Host bridge: Intel Corporation Device 590f (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 5902 (rev 04)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
```

And output of```
 lspci -k | grep -iA3 ethernet 
```(I don't know what does this command show but I have come across this command when I was looking for the answer in google) command:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
Subsystem: ASRock Incorporation Motherboard (one of many)
Kernel driver in use: r8169
Kernel modules: r8169
```

Edit on Sep 9 2017, Sat: 

I tried to install r8168 driver from realtek's site. First, I followed the manual instructions in this site: [https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

I tried to install dependencies by entering the code into terminal:

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

and then I downloaded the driver from Realtek's site: [URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2"]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2
[/URL]
I downloaded the version which states Linux driver for kernel up to 4.7. I don't exactly if that is the case, if that one is causing me the problems.

Then I blacklisted my already installed and working r8169 driver by this code:
```

sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf'
```

Then I untarred the archive by this code: ```
tar xfvj 0009-r8168-8.044.02.tar.bz2
```
which showed me the following output:
```
r8168-8.044.02/
r8168-8.044.02/autorun.sh
r8168-8.044.02/Makefile
r8168-8.044.02/README
r8168-8.044.02/src/
r8168-8.044.02/src/Makefile
r8168-8.044.02/src/Makefile_linux24x
r8168-8.044.02/src/r8168.h
r8168-8.044.02/src/r8168_asf.c
r8168-8.044.02/src/r8168_asf.h
r8168-8.044.02/src/r8168_dash.h
r8168-8.044.02/src/r8168_fiber.h
r8168-8.044.02/src/r8168_n.c
r8168-8.044.02/src/r8168_realwow.h
r8168-8.044.02/src/rtltool.c
r8168-8.044.02/src/rtltool.h
r8168-8.044.02/src/rtl_eeprom.c
r8168-8.044.02/src/rtl_eeprom.h
```

After that I got into that folder```
 r8168-8.044.02/ 
```and compiled the script autorun.sh ```
sudo ./autorun.sh
```
which showed me the following output on terminal:
```
Check old driver and unload it.
rmmod r8169
Build the module and install
At main.c:158:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
Backup r8169.ko
rename r8169.ko to r8169.bak
DEPMOD 4.10.0-33-generic
load module r8168
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-4.10.0-33-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
Completed.
```

Then I run this code: ```
lsmod | grep r8168
``` which output:```
 r8168 499712 0
```

Then I run ```
sudo ethtool -i enp2s0
```

After that I suspended my PC and reopened it back, but it had the same problem, it did not connect to Wired connection after suspension. I had reboot it to get working Ethernet connection. After rebooting I tried to install it automatically rather than manually, so I edited > /etc/apt/sources.list, I changed ```
xenial main restricted
``` to ```
xenial main restricted universe
```. 

Then I ```
sudo apt-get update
```, then I ```
sudo apt-get install r8168-dkms
```

However, those things also did not help, when I suspended my PC. So, I had to reboot again to get internet connection.

After rebooting I followed some of the instructions in this site: [https://nosemaj.org/hardy-r8168](https://nosemaj.org/hardy-r8168).

I run:
```
sudo bash
```

then ```
rmmod r8169 
```which output ```
rmmod: ERROR: Module r8169 is not currently loaded
```.

then ```
make clean
``` which output:

```
make -C src/ clean
make[1]: Entering directory '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src'
make -C /lib/modules/4.10.0-33-generic/build SUBDIRS=/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src clean
make[2]: Entering directory '/usr/src/linux-headers-4.10.0-33-generic'
CLEAN /home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src/.tmp_versions
rm: cannot remove '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src/.tmp_versions/r8168.mod': Permission denied
Makefile:1569: recipe for target 'clean' failed
make[2]: *** [clean] Error 1
make[2]: Leaving directory '/usr/src/linux-headers-4.10.0-33-generic'
Makefile:99: recipe for target 'clean' failed
make[1]: *** [clean] Error 2
make[1]: Leaving directory '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src'
Makefile:47: recipe for target 'clean' failed
make: *** [clean] Error 2
```

then ```
make modules
``` which output:
```
make -C src/ modules
make[1]: Entering directory '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src'
make -C /lib/modules/4.10.0-33-generic/build SUBDIRS=/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src modules
make[2]: Entering directory '/usr/src/linux-headers-4.10.0-33-generic'
rm: cannot remove '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src/.tmp_versions/r8168.mod': Permission denied
Makefile:1511: recipe for target 'crmodverdir' failed
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory '/usr/src/linux-headers-4.10.0-33-generic'
Makefile:95: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
make[1]: Leaving directory '/home/garakchy/my_stuff_002/drivers_I_downloaded/r8168-8.044.02/src'
Makefile:40: recipe for target 'modules' failed
make: *** [modules] Error 2
```

then```
 make install
``` etc. After all, I suspended my PC and reopened it back, it totally crashed and stopped working at all, let alone the not working Ethernet connection. My PC got stuck. I reboot. After rebooting my PC temporarily working in good condition, but I wanted to go back to r8169 driver, which was installed default. So, I changed > modprobe.d/blacklist.conf, I deleted>  r8169 there and wrote>  r8168 instead.

Output of ```
sudo lshw -class network 
```command:
```
*-network 
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: enp2s0
version: 02
serial: d0:50:99:72:eb:0c
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.044.02-NAPI duplex=full ip=192.168.1.26 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:17 ioport:e000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:90000000-9000ffff
```

It shows > r8168 as a driver still, even if I had blacklisted it.

Here are some other information that I thought would be useful: [http://paste.ubuntu.com/25497742/](http://paste.ubuntu.com/25497742/)

```
########## wireless info START ##########

Report from: 09 Sep 2017 16:58 +03 +0300

Booted last: 09 Sep 2017 00:00 +03 +0300

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description: Ubuntu 16.04.3 LTS
Release: 16.04
Codename: xenial

##### kernel ############################

Linux 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
Kernel driver in use: r8168

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi 16384 0
wmi 16384 1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0 Link encap:Ethernet HWaddr <MAC 'enp2s0' [IF1]> 
inet addr:192.168.1.26 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::9d89:9a06:9c3c:aa5f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:841359 errors:0 dropped:0 overruns:0 frame:0
TX packets:508522 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1206038659 (1.2 GB) TX bytes:39262133 (39.2 MB)
Interrupt:17 Base address:0xd000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:3258 errors:0 dropped:0 overruns:0 frame:0
TX packets:3258 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:329425 (329.4 KB) TX bytes:329425 (329.4 KB)

##### iwconfig ##########################

enp2s0 no wireless extensions.

lo no wireless extensions.

##### route #############################

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 100 0 0 enp2s0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 enp2s0
192.168.1.0 0.0.0.0 255.255.255.0 U 100 0 0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

NetworkManager

Running:

root 826 1 0 15:07 ? 00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE: enp2s0
GENERAL.TYPE: ethernet
GENERAL.NM-TYPE: NMDeviceEthernet
GENERAL.VENDOR: Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many))
GENERAL.DRIVER: r8168
GENERAL.DRIVER-VERSION: 8.044.02-NAPI
GENERAL.FIRMWARE-VERSION: 
GENERAL.HWADDR: <MAC 'enp2s0' [IF1]>
GENERAL.MTU: 1500
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE: enp2s0
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: Wired connection 1
GENERAL.CON-UUID: 10942507-8479-3f0f-aa05-39f5cfc92e15
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED: no (guessed)
CAPABILITIES.CARRIER-DETECT: yes
CAPABILITIES.SPEED: 100 Mb/s
CAPABILITIES.IS-SOFTWARE: no
WIRED-PROPERTIES.CARRIER: on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: 10942507-8479-3f0f-aa05-39f5cfc92e15 | Wired connection 1
IP4.ADDRESS[1]: 192.168.1.26/24
IP4.GATEWAY: 192.168.1.1
IP4.ROUTE[1]: dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]: 192.168.1.1
IP4.DOMAIN[1]: home
DHCP4.OPTION[1]: requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]: requested_domain_search = 1
DHCP4.OPTION[3]: requested_host_name = 1
DHCP4.OPTION[4]: requested_time_offset = 1
DHCP4.OPTION[5]: requested_domain_name = 1
DHCP4.OPTION[6]: requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]: requested_broadcast_address = 1
DHCP4.OPTION[8]: requested_wpad = 1
DHCP4.OPTION[9]: requested_netbios_scope = 1
DHCP4.OPTION[10]: next_server = 0.0.0.0
DHCP4.OPTION[11]: expiry = 1505045259
DHCP4.OPTION[12]: requested_interface_mtu = 1
DHCP4.OPTION[13]: requested_subnet_mask = 1
DHCP4.OPTION[14]: routers = 192.168.1.1
DHCP4.OPTION[15]: dhcp_message_type = 5
DHCP4.OPTION[16]: ip_address = 192.168.1.26
DHCP4.OPTION[17]: requested_static_routes = 1
DHCP4.OPTION[18]: domain_name = home
DHCP4.OPTION[19]: dhcp_renewal_time = 43200
DHCP4.OPTION[20]: requested_domain_name_servers = 1
DHCP4.OPTION[21]: broadcast_address = 192.168.1.255
DHCP4.OPTION[22]: domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[23]: requested_ntp_servers = 1
DHCP4.OPTION[24]: dhcp_lease_time = 86400
DHCP4.OPTION[25]: dhcp_rebinding_time = 75600
DHCP4.OPTION[26]: requested_netbios_name_servers = 1
DHCP4.OPTION[27]: subnet_mask = 255.255.255.0
DHCP4.OPTION[28]: network_number = 192.168.1.0
DHCP4.OPTION[29]: requested_routers = 1
DHCP4.OPTION[30]: dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]: fe80::9d89:9a06:9c3c:aa5f/64
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

Region: Europe/Istanbul (based on set time zone)

country 00: DFS-UNSET
(2402 - 2472 @ 40), (6, 20), (N/A)
(2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
(5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0 no frequency information.

lo no frequency information.

##### iwlist scan #######################

enp2s0 Interface doesn't support scanning.

lo Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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
blacklist r8168

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

##### dmesg #############################

[ 27.284525] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 27.284681] enp2s0: 0xffff9b47c0c8d000, <MAC 'enp2s0' [IF1]>, IRQ 17
[ 27.312137] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 30.374732] r8168: enp2s0: link up
[ 30.374745] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############
```

I don't know what to do. Can you help me please? Thanks

---

### Post by mörgæs on 2017-09-10
Hi, welcome to the fora.

That's a lot of experimenting. In your case I would rather have spent the time trying to install 17.04 to see if the problem was fixed there.

---

### Post by BenginM on 2017-09-10
Is the motherboard's BIOS up-to-date!

check the current BIOS Revision & date with:
 
$ sudo dmidecode -t bios -q BIOS

and consult the machine vendor official website.

if the BIOS is up-to-date, then your last bit is to report a bug usin'

$ ubuntu-bug linux

in a terminal , and you might find ans existing bug recently reported , in that case add yourself as an effected user.

## see:
[https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by garakchy on 2017-09-10
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") Thank you for the warm welcome. I think I will stick to LTS for a while. I'm not sure though if I should install latest Ubuntu version or stick with the LTS one. What do you suggest? Is LTS too good compared to non-LTS versions? Or are the non-LTS versions too buggy? Thanks. By the way, is there any way to like your comment or somebody's so that I can give you some karma for your help. I looked for an upvote or like button, but could not find any.

---

### Post by garakchy on 2017-09-10
@[**[COLOR=#000000]BenginM[/COLOR]**]("https://ubuntuforums.org/member.php?u=1100835") 	 Thanks. I checked the BIOS, it seems updated to the latest version, so I reported the bug. By the way, I'm new here, I want to ask a question. If I don't include your username in my reply, do you still get notified about the reply or do I have to add username? I haven't been notified about these replies to my thread, which is a must I think. I just checked my post and then learned that I had answers on it. Sorry, but in my opinion, this Ubuntu forum lacks functionality that is provided by StackExchange network. Thanks after all.

---

### Post by BenginM on 2017-09-10
I get notified for replies instantly because i am subscribed to the thread, And you can do the same. from the forum top panel open settings -> General Settings -> Default Thread Subscription Mode

select instantly, using mail , or daily . or weekly .

Welcome to the forums, and thanks for flyin' Ubuntu!

---

### Post by garakchy on 2017-09-10
I subscribed to it now. Thanks for the welcome.

---

### Post by BenginM on 2017-09-10
O' and you can also use the Thread Tools under the thread title and choose to subscribe to any thread you like!

You're welcome , keep an eye on your e-mail inbox for the bug report, the kernel team now is notified about the bug. Well done. if you want instant assistance you may wish to join the kernel team channel #ubuntu-kernel on freenode using [this web-interface]("https://webchat.freenode.net/"), and give them the bug number from the bug page #NumbersHere [URL="https://webchat.freenode.net/"]
[/URL]

---

### Post by garakchy on 2017-09-10
Ok. Thanks

---

### Post by mörgæs on 2017-09-11
> **garakchy said:**
> Thank you for the warm welcome. I think I will stick to LTS for a while. I'm not sure though if I should install latest Ubuntu version or stick with the LTS one. What do you suggest? Is LTS too good compared to non-LTS versions? Or are the non-LTS versions too buggy? Thanks. By the way, is there any way to like your comment or somebody's so that I can give you some karma for your help. I looked for an upvote or like button, but could not find any.

The LTS versions are the ones which are buggy. If a bug was found in, say June 2016 (when 16.04 had been out for a couple of months) then it would have been fixed in what was the development version at that time, that is 16.10. A bug found in January 2017 would have been fixed in 17.04 and so on.

Bugfixes are only rarely backported to old releases. If it happens it does so with with a long delay.

16.04 is a museum for old bugs. LTS means stability, that is the opposite of changes. If 16.04 works well at the installation time then stick to it, if it doesn't (like in your case) abandon it. 

Please note that I can't promise that the bug has been fixed in 17.04 but it sould be the first step to test. If you have the space then you could install 17.04 next to your present operative system(s).

Thanks for the kind words :-) 

I rarely ever substribe to a thread. Easier to use 'advanced search' and search for your own user name.

---

### Post by garakchy on 2017-09-11
@[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") Thanks. I will try to upgrade to 17.04.

---

### Post by garakchy on 2017-09-13
I'm tired of Ubuntu's problems. With 16.04 LTS freshly installed on my PC, I was already having plenty of bugs with Linux Ubuntu. I got a suggestion to upgrade to 17.04 which they said that it contains the fixes to the bugs that 16.04 had. That's not true, I upgraded it to 17.04 and realized that it is also full of bugs. Let's start with the story.
  After upgrading 16.04 to 17.04 I reboot my PC since that was what I was asked to do by Command line interface terminal. After rebooting I see my login screen, but guess what my USB keyboard and USB mouse are not working now. So, I reboot continuously in order to solve the problem to no avail. After many tries, I pressed F6, F1, F2, F11 and Del keys when rebooting. PC shows a brief information about to press some keys in order to enter into BIOS system or UEFI or some other places where you can manage some pre-login things like the boot, etc.
  In some of those places I have encountered the list which was written, Ubuntu on the top, then Advanced Mode second and then Recovery mode, I forgot them, the list goes on. I think I entered into the Advanced mode and then into Recovery mode. There I saw some list, on it, were written some items like Network, System settings, Root or some other things, I'm sorry I don't remember exactly the names. Next, I was in the Command line interface terminal, I'm happy now to learn that my keyboard is working in the terminal. I have written some codes happily. I wrote lshw to list my hardware and there I realised that my network is Disabled. Not believing to my eyes I again typed lshw -C network, it was disabled. So, I googled my problem and I learned that I need to write touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf and reboot. After rebooting my Ethernet network, wired connection was working properly.
  Before fixing the connection, I was trying to fix my mouse and keyboard connection bugs. I typed apt update, apt upgrade and many other codes to no avail because I was not connected to the Internet, the system could not fetch some important things from the internet. Now my internet connection working I typed those codes continuously apt update, apt upgrade, --fix-missing and many other codes that I thought would be helpful for me.
  Then I reboot my PC. I entered now Ubuntu, not the Advanced mode, and I was directed to the login screen, but it was not the usual graphics screen, it was a screen like a terminal. There I entered my username and password and I was logged in, still not graphics mode.
  There I learned that I lacked the graphics may be, so I googled and wrote some codes that I think installed the graphics system. The codes as far as I remember were sudo apt dist-upgrade, sudo apt update, sudo apt upgrade, sudo apt install -y ubuntu-desktop*, sudo apt install xserver-xorg-input-all.
  After rebooting I was finally able to login to my graphical Ubuntu 17.04 where I can use my mouse, keyboard and internet connection. I'm now writing from that PC.
  Some notes: I haven't included sudo codes in the first terminal codes because I was root, you may need sudo if you are not root. I know, I have written some codes vaguely because I did not know if those codes would fix the bug or actually increase the problem more. After solving my problems I tried to remember some codes. Linux Ubuntu is full of bugs, no matter which release you use. I used this askubuntu forum and many other forums. Thanks for you, the great community. Without your help, it would have been very difficult for me. Now I'm considering to switch Arch Linux or FreeBSD. Not sure, though, how they will work for me. If I have many troubles there I think I will come back to Linux Ubuntu. I hope some knowledgeable developers fix my buggy codes above if there are any. I wanted to write this experience of mine so that some people encountering similar problems may find a helping hand here. Thank you, everybody.
  Edit on Sep 13, 2017 at 6:20 pm: See, there are many problems and bugs. I opened my command line interface terminal, it is not opening. I tried to open Vivaldi browser, same, it doesn't open, and Google Chrome doesn't open, Chromium doesn't open. I entered my System Settings -> Displays, I had to click on and tick the "Mirror Displays" checkbox. After that my CLI terminal, Google Chrome opened in Ubuntu 17.04.

Edit on Sep 13, 2017 at 9:14 pm: This answer of mine was deleted by Thomas Ward in askubuntu.com.

---

### Post by garakchy on 2017-09-13
Now, I'm writing from FreeBSD. Just installed it. Let's see, what happens. I wish I used Linux Ubuntu more, but there were some bugs involved.

---

### Post by mörgæs on 2017-09-14
I don't know who promised you that the bug was fixed in 17.04. I know that I didn't. We still don't know if it is.
I don't know who encouraged you to upgrade. I know that I talked about a dual boot (you have probably already seen my opinion about upgrades in the link in my signature). 

Anyway, you did a fresh install and it helped. The install was FreeBSD though and not Ubuntu but congratulations with the working computer.

We don't know if the solution was a) switching to BSD or b) to reinstall something from a clean slate. Feel free to use BSD but don't take this as a proof that Ubuntu is hopeless.

---

### Post by garakchy on 2017-09-14
Well, I know that problems persist everywhere no matter what you use. Even if I don't use Ubuntu personally now on my PC, one of my friends use it in his laptop. And I installed it in his laptop deleting the Windows. Ubuntu is good for beginners, and I was a beginner. And I want to a real geek Unix, GNU/Linux dev, admin or something like that.  :P Any given day I was thinking of switching to some other distro that would challenge me. And this was opportunity to me to take and develop myself. Well after upgrading my Ubuntu I learned that there are some bugs and fixed them. Fixing them gave me some confidence. And about your signature, no I haven't seen that till now, and I see it now, and I haven't followed the safe way. :) And I'm blaming Ubuntu for that. Anyway, I'm planning to use Linux one day, by trying Arch, Gentoo, Kali and Slackware, hopefully. I know that they are very difficult to me for now, but I hope I will develop myself with the philosophy of Unix in FreeBSD. Thanks, Mörgaes.

---

### Post by mörgæs on 2017-09-15
Good to see that you have the drive to experiment. If some of the other distros give problems we also have [fora for them]("https://ubuntuforums.org/forumdisplay.php?f=446").

---

### Post by lord-vltor on 2018-05-18
Using XUbuntu 18LTS right now, the bug is still present and makes the 'Suspend' function not an option (unless the machine works isolated, but come on).
I tried to use the command '**sudo service network-manager restart**', but the network keeps offline until I restart my machine.
I really do not understand why various distros with the same flavours have different bugs, and there is no mean of integration (I'm coming from Mint XFCE, where one of the major flaws were the NVidia drivers).
It would be nice to see some fix packs for LTS's major bugs, because waiting up to 2022 to get a network fix (which it seems to have been already present in v16 and hasn't been fixed to x18), sounds a bit outrageous.

---

