---
title: "Lubuntu 14.04 has lost networking capability"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by el_gallo_azul on 2016-09-14
I have been using Lubuntu 14.04 on this eeePC901 for years, and quite happily. Lubuntu 14.04 is still working perfectly on another eeePC901 I have. At the moment, I am using them to run BOINC around the clock because they are very frugal energy consumers.

A couple of weeks ago when I checked that they were both running nicely, this one had lost its wifi network connection. I thought rebooting might sort it out like it usually does. However, the problem seems to be a bit deeper than that.

When I boot, I get

```
Waiting for network configuration...
```

followed by

```
Waiting up to 60 more seconds for network configuration...
```

and then at the end of boot

```
Booting system without full network configuration...
```

And then, after boot, in the panel at the bottom of the screen, when I click the networking applet, I see:

```
NetworkManager is not running
```

so I use the command

```
sudo service network-manager restart
```

which seems to run OK, but then when I click on the networking applet again, it says ```
No network devices are available
```.

Any ideas how to get it back on the network? I can use an ethernet cable if necessary.

---

### Post by wildmanne39 on 2016-09-14
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by wildmanne39 on 2016-09-15
@Joe_Misseri  I moved your posts here:
[https://ubuntuforums.org/showthread.php?t=2337141](https://ubuntuforums.org/showthread.php?t=2337141)

---

### Post by el_gallo_azul on 2016-09-16
I'm not able to run the script on the affected computer, because it currently has no network capability (wired or wireless).

I will run it using the executable from

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \chmod +x wireless-info && \
./wireless-info
```

---

### Post by el_gallo_azul on 2016-09-16
Results from wireless-info.txt:

```



########## wireless info START ##########


Report from: 17 Sep 2016 07:44 ACST +0930


Booted last: 17 Sep 2016 07:25 ACST +0930


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-92-generic #139-Ubuntu SMP Tue Jun 28 20:42:32 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
	Subsystem: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:2790]


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8324]


##### lsusb #############################


Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0
iface eth0 inet manual


##### ifconfig ##########################


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


	None found.


##### NetworkManager info ###############


** (process:2430): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


** (process:2430): WARNING **: error: could not connect to NetworkManager


NetworkManager Tool


State: unknown


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


[[/etc/NetworkManager/system-connections/TelstraSux-2.4GHz]] (600 root)
[connection] id=TelstraSux-2.4GHz | type=802-11-wireless
[802-11-wireless] ssid=TelstraSux-2.4GHz | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/iiNet1FB465(2.4GHz)]] (600 root)
[connection] id=iiNet1FB465(2.4GHz) | type=802-11-wireless
[802-11-wireless] ssid=iiNet1FB465(2.4GHz) | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eeePC-1]] (600 root)
[connection] id=eeePC-1 | type=802-11-wireless
[802-11-wireless] ssid=eeePC-1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eeePC-3]] (600 root)
[connection] id=eeePC-3 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=eeePC-3
[ipv4] method=shared
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x0781 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    2.302857] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)


########## wireless info END ############

```

---

### Post by jeremy31 on 2016-09-16
I suspect an update may have had issues, check ```
dpkg -l | grep extra
``` and see if there is one with 3.13.0-92

If my suspicion is correct, reboot and use the shift key to get the Grub menu to appear, then scroll down to advanced options or previous linux versions and select and older kernel to boot into to have internet

---

### Post by el_gallo_azul on 2016-09-16
```

user@eeepc3:~$ dpkg -l | grep extra
ii  chromium-codecs-ffmpeg-extra         50.0.2661.102-0ubuntu0.14.04.1.1117   i386         Extra ffmpeg codecs for the Chromium Browser
ii  libarchive-extract-perl              0.70-1                                all          generic archive extracting module
ii  libcdparanoia0:i386                  3.10.2+debian-11                      i386         audio extraction tool for sampling CDs (library)
ii  libfm-extra4                         1.2.0-1ubuntu2                        i386         file management support (extra library)
ii  libido3-0.1-0:i386                   13.10.0+14.04.20151021-0ubuntu1       i386         Shared library providing extra gtk menu items for display in
ii  librsvg2-common:i386                 2.40.2-1                              i386         SAX-based renderer library for SVG files (extra runtime)
ii  libwvstreams4.6-extras               4.6.1-7                               i386         C++ network libraries for rapid application development
rc  linux-image-extra-3.13.0-32-generic  3.13.0-32.57                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic  3.13.0-49.83                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic  3.13.0-51.84                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic  3.13.0-52.86                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic  3.13.0-53.89                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic  3.13.0-54.91                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic  3.13.0-55.94                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic  3.13.0-57.95                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic  3.13.0-58.97                          i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic  3.13.0-61.100                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic  3.13.0-71.114                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-73-generic  3.13.0-73.116                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic  3.13.0-74.118                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic  3.13.0-76.120                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic  3.13.0-77.121                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic  3.13.0-79.123                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic  3.13.0-83.127                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic  3.13.0-85.129                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic  3.13.0-88.135                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic  3.13.0-91.138                         i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  ubuntu-extras-keyring                2010.09.27                            all          GnuPG keys of the Ubuntu extras archive
user@eeepc3:~$ 

```

but in fact 3.13.0-92 is the current kernel (per wireless-info.txt output above).

```

...
##### kernel ############################




Linux 3.13.0-92-generic #139-Ubuntu SMP Tue Jun 28 20:42:32 UTC 2016 i686 i686 i686 GNU/Linux
...

```


Now I'll try booting it from a different kernel, and see what happens.

---

### Post by el_gallo_azul on 2016-09-16
Yep. Sure enough, it works when I use 3.13.0-91. I'm just updating now.

I've never had that happen before, where a routine update makes the computer stop working properly.

---

