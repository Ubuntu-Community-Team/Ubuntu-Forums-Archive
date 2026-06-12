---
title: "Sitecom Wireless USB (WLA-2100) with Ralink chipset"
date: 2014-07-27
forum: Networking &amp; Wireless
---

### Post by FroggleWoggle on 2014-07-27
First posts below are about a Realtek chipset, but the device seemed to have a Ralink chipset. (Sorry for the confusion). 
The problem was about the 0df6:0078 product. See [this post]("http://ubuntuforums.org/showthread.php?t=2236540&p=13098452#post13098452") for the solution.

====================================================

I've bought a [Sitecom wireless USB (WLA-2100) with a Realtek RTL8192SU chipset]("http://www.wireless-driver.com/nl/sitecom-wla-2100-v1-wifi-macos-driver-utility-ver201/") and can't get it to work on my machine. I've read several posts about it and tried several options but was unsuccesfull. I'm new to Linux but I've learned a lot with this issue!

Some info:

uname -a
```

Linux MeduoLX 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

lsb_release -a
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

```

lsusb
```

Bus 002 Device 006: ID 0df6:0078 Sitecom Europe B.V.

```

After plugging in the USB stick:

dmesg | tail
```

[ 1122.254197] usb 2-2.4: USB disconnect, device number 6
[ 1126.036203] usb 2-2.4: new high-speed USB device number 7 using ehci-pci
[ 1126.160327] usb 2-2.4: New USB device found, idVendor=0df6, idProduct=0078
[ 1126.160333] usb 2-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1126.160337] usb 2-2.4: Product: 802.11 n WLAN
[ 1126.160340] usb 2-2.4: Manufacturer: Ralink
[ 1126.160343] usb 2-2.4: SerialNumber: 1.0

```

iwconfig
```

eth0      no wireless extensions.
lo        no wireless extensions.

```

lsmod | grep 819
```

ahci                   25819  0 

```

modinfo r8192u_usb 
```

filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
srcversion:     1FA0981C52E5A923D61E7D0
alias:          usb:v043Ep7A01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0290d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0043d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8709d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           debug:debug output mask (int)
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware security support.  (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

```

sudo modprobe -v r8192u_usb
```

insmod /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko 

```

---

### Post by FroggleWoggle on 2014-07-30
Can this thread be moved to Hardware?

---

### Post by varunendra on 2014-07-31
Your thread is where it should be (unless it was moved silently from somewhere else to here - Networking & Wireless section). And if you ever want to request or report something to the admins/mods, you can always use the "Report Post" button that appears below every post.

Regarding the wireless problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by FroggleWoggle on 2014-07-31
Result of the wireless_script:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

MeduoLX 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
Memory : 993 MB
Uptime : 20:18:21 up 8 min,  2 users,  load average: 0.37, 0.52, 0.30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5B [1043:81aa]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 006: ID 0df6:0078 Sitecom Europe B.V. 
Bus 002 Device 005: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0763:0197 Midiman Oxygen 61
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 0763:2010 Midiman M-Audio Fast Track
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Wi-Fi connection 1   : ssid=<BLOCKED> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback

#iface eth0 inet static
#address 192.168.1.68
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.254

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search sitecomwlr4000


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.579/0.592/0.605/0.013 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.045/0.051/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
network_drivers.conf~: install rtl8192su /sbin/modprobe --ignore-install rtl8192cu $CMDLINE_OPTS; /bin/echo "0df6 0078" > /sys/bus/usb/drivers/rtl819cu/new_id
r8712u.conf       : install r8712u modprobe --ignore-install r8712u ; /bin/echo "0df6 0078" > /sys/bus/usb/drivers/r8712u/new_id


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=1252f09b-2c6b-4058-909c-33c71d4bd7d5 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.813654] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.814061] audit: initializing netlink socket (disabled)
[    2.079561] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.073398] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========
```

---

### Post by FroggleWoggle on 2014-07-31
The [Realtek drivers site]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2312") shows Linux support for RTL8192SU: Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.2
I'm on Kernel 3.13... 

How can I get it to work?

---

### Post by menth1979 on 2014-08-08
Coffeecat, sorry if I write here after you splitted the thread. I noticed something on the dmesg message frogglewoggle posted:
> 
[ 1126.160340] usb 2-2.4: Manufacturer: Ralink


I think that it's the same adapter that I have, and it's a Ralink 2800 one, not a Realtek.

---

### Post by coffeecat on 2014-08-08
@FroggleWoggle, this output:

> **FroggleWoggle said:**
> 
lsusb
```

Bus 002 Device 006: ID 0df6:0078 Sitecom Europe B.V.

```

After plugging in the USB stick:

dmesg | tail
```

[ 1122.254197] usb 2-2.4: USB disconnect, device number 6
[ 1126.036203] usb 2-2.4: new high-speed USB device number 7 using ehci-pci
[ 1126.160327] usb 2-2.4: New USB device found, idVendor=0df6, idProduct=0078
[ 1126.160333] usb 2-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1126.160337] usb 2-2.4: Product: 802.11 n WLAN
[ 1126.160340] usb 2-2.4: Manufacturer: Ralink
[ 1126.160343] usb 2-2.4: SerialNumber: 1.0

```



Tells us that your 0df6:0078 usb device is a Ralink, not Realtek. Is there a reason why you are trying to enable a driver for a Realtek RTL8192SU chipset and have put "Realtek RTL8192SU" in your thread title?

**EDIT:**

@menth1979, I didn't see your post when I posted. 

> **menth1979 said:**
> Coffeecat, sorry if I write here after you splitted the thread. I noticed something on the dmesg message frogglewoggle posted:


I think that it's the same adapter that I have, and it's a Ralink 2800 one, not a Realtek.

Yes, you are right - the OP appears to have a Ralink but for some reason is investigating the Realtek driver.

---

### Post by varunendra on 2014-08-08
> **coffeecat said:**
> @FroggleWoggle, this output:
....<snip>....
Tells us that your 0df6:0078 usb device is a Ralink, not Realtek. Is there a reason why you are trying to enable a driver for a Realtek RTL8192SU chipset and have put "Realtek RTL8192SU" in your thread title?

I think because the OP is confused by the description page they linked to : [http://www.wireless-driver.com/nl/sitecom-wla-2100-v1-wifi-macos-driver-utility-ver201/](http://www.wireless-driver.com/nl/sitecom-wla-2100-v1-wifi-macos-driver-utility-ver201/)

It clearly says -
> **Chipset:** Realtek RTL8192SU
But then, below the (Mac OS) driver download link, it also says -
> **Ondersteunde hardware-id's:**```
USB VID_0DF6&PID_**[COLOR="#FF0000"]006C[/COLOR]**
```
("Ondersteunde" in dutch is translated to "Supported" in English)

So it seems that either the OP got an entirely different device, or probably Sitecom changed the chip inside. It is not uncommon for the vendors to change the chips in different versions of a device.

In any case, the device "0df6 : 0078" appears to be using Ralink chip inside, as the dmesg identified.

As for the solution, I frankly have no idea. This device doesn't seem to be supported natively and I don't know if a driver for Linux exists anywhere outside.

For this very same reason, I am hesitating to post in the [other thread]("http://ubuntuforums.org/showthread.php?t=2238485"), because others may have a solution while I don't have any.

**PS:**
From the 'echoing' of device id trick (evident in their /etc/modprobe.d/r8712u.conf file included in the wireless_script report), it seems the OP probably followed some post by **praseodym**, since he is the only one whom I have noticed trying that kind of trick with PCI devices. Some of us don't think it works with PCI devices, but we keep learning new things and are always open to corrections.

---

### Post by FroggleWoggle on 2014-08-11
Thanks for your sharp observations. I indeed was mislead by the information on the page I linked to and I missed to dmesg line about the Ralink. I would change the subject of the post if I could but don't know how. So it seems my WLA-2100 device has a Ralink chipset :D.

---

### Post by coffeecat on 2014-08-11
I've edited the thread title for you to remove the reference to Realtek. According to discussion on another thread with what seems to be the same device, that Ralink chipset is problematic. Hopefully, someone will be able to help you.

---

### Post by FroggleWoggle on 2014-08-14
Wow, this is amazing and I can't believe it myself, but thanks to [this bug description]("https://lists.debian.org/debian-kernel/2012/04/msg00558.html") I managed to get my WiFi going. I am really a newby to Linux and this is a major major conquer to me!

1. First load the module since it won't load automatically (there's mention of the non-free firmware-ralink package which supposedly needed to be  installed, but I haven't) (I did an update of the firmware-ralink package however):

```
modprobe rt2800usb
```

2. Second tell the module to assoicate with the usbID of the device (as root): 

```
echo "0DF6 0078" > /sys/bus/usb/drivers/rt2800usb/new_id
```

3. (Optionally): I needed a device unplug and replug

This should do the trick. 

Check that:

1. The module is loaded:

```
lsmod | grep rt2800
```

2. The module association is correct

```
cat /sys/bus/usb/drivers/rt2800usb/new_id
```

Thanks to: Jaimos F Skriletz

---

