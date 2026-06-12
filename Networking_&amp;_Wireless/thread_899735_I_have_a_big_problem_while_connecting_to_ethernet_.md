---
title: "I have a big problem while connecting to ethernet connections.."
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-08-24
I have a serious problem connecting to ethernet connections..
i have ubuntu 8.04 installed on my laptop and i don't find any problems while connecting to wireless but it rarely connects to ethernet...
I had all my packages installed using wired conection but even then it used to pose a lot of problem whie connecting..
it was just a matter of luck for it to get connected..
Now i have all the packages installed..i have even installed the ethernet drivers from the cd provided by dell..for my laptop..but still it hardly gets connected..i use a proxy server to access net and i have already updated all the proxy settings..available...
since i m in a collge therefore i have to change the ip, netmask and gateway...for different ethernet connections.
but still i can't connect it.
i even check the ethernet configuration through ifconfig and all of them are right..
but still i can't figure out why is that i can't connect to the internet..through an ethernet connection...
help me..

---

### Post by forger on 2008-08-24
You could try setting it up especially for wired/ethernet network, go to menu System > Administration > Network > click Unlock, double-click "Wired connection", uncheck "enable roaming mode" and put in your network information.
(I would uncheck the roaming mode of wireless too)

---

### Post by shredder12 on 2008-08-24
ofcourse i have done it...
that is how i was able to connect to internet in order to download my packages...and ndiswrapper for wireless purposes..
newaz...when i wrote my first post...i was working on wireless..but when i restarted my system..and then suddenly without any modification the ethernet started working..
seriously i did nothing...
the settings were the same before the restart..but then it was not connecting..
how do i explain it..

---

### Post by forger on 2008-08-24
1) broken ethernet cord?
2) wrong ethernet cord? I think there are two types of cords, one "straight" and one "crossed". Maybe you have the wrong type?

---

### Post by porlaizquierda on 2008-08-24
I am having the exact same problem. I cannot connect to the internet and I know that it is not my ethernet cord or modem since it also does not work at a friend's house who has perfectly fine internet connection. I am not allowed to view my network settings for some reason. I have had nothing but trouble when trying to upgrade to 8.04.

---

### Post by forger on 2008-08-24
can you post the output of this:
```
sudo lshw -class network
lspci
```

---

### Post by shredder12 on 2008-08-24
hey the result of the first command is..
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e2:95:fb:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:94:56:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=172.16.14.56 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```
this result was when my ethenet connection was working...
and for the second one..
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
 
```
and believe me the problem is not with the cord..
because i work on different labs and that's why have different wires everytime...which work properly...
so thre is no problem...

---

### Post by dmizer on 2008-08-24
Can you ping by host name or by ip address?

For example
```
ping www.google.com
```
or
```
ping 208.67.219.231
```

Are these all static networks? Are you disabling your wireless connection before attempting to connect to wired?

---

### Post by shredder12 on 2008-08-26
no i m not able to ping these site..
or any ip's
even i m not able to ping the proxy server which my college uses..
but when the internet is connected..
the ping works..

---

### Post by Yannick Le Saint kyncani on 2008-08-28
> **shredder12 said:**
> ```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.

```
this result was when my ethenet connection was working...
and for the second one..
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
```
and believe me the problem is not with the cord..
because i work on different labs and that's why have different wires everytime...which work properly...
so thre is no problem...

Hi shredder, the RTL8111/8168B does not work with hardy's builtin r8169 module, I have "fixed" this using r8168 module provided by realtek.

Here is the script I used to install it :
```

#! /usr/bin/env bash

##
## r8168-build.sh
## (c) Yannick Le Saint (kyncani), 27 Aug 2008
## <y.lesaint at gmail.com> http://y.lesaint.free.fr/
## 
## Released under GPL version 2 (http://www.gnu.org/copyleft/gpl.html)
## This program is free software; you can redistribute it and/or modify
## it under the terms of Version 2 of the the GNU General Public License 
## as published by the Free Software Foundation. Any later versions of
## the GPL will be evaluated as they are released, and this software may
## or may not be re-released under those terms also.
## 
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
##

##
## Realtek RTL8111/8168B ethernet chipset does work with ubuntu hardy
## It is reported with lspci as
## Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B
##   PCI Express Gigabit Ethernet controller (rev 01)
##
## This script will install a working r8168 module to handle these
## cards.
##

#######################################################################

## Package name
PN="r8168"

## Package version
PV="8.008.00"

## Kernel version
KV=`uname -r`

## Module name
MODULE="r8168"

## Program name
prog=`basename "$0" | sed "s#[^-_\.[:alnum:]]##g; s/^\$/$MODULE/"`

## Blacklist file
BLACKLIST="etc/modprobe.d/$MODULE"

## Where to download the sources from
SOURCES_SITE="ftp://61.56.69.18/cn/nic/"
SOURCES_EXT=".tar.bz2"

#######################################################################

## Successfully execute a command or die.
dothis() {
    if ! eval "$*"; then
        echo "$prog: $* error." >&2
        exit 1
    fi
}

#######################################################################

for tool in "gcc build-essential" checkinstall unp; do
    if echo "$tool" | grep -q " "; then
        t1=`echo "$tool" | sed 's/ .*//'`
        t2=`echo "$tool" | sed 's/^[^ ]* //'`
    else
        t1="$tool"
        t2="$tool"
    fi
    if ! type $t1 &>/dev/null; then
        echo "$prog: $t1 not found, you need to install $t2." >&2
        exit 1
    fi
done

if ! test -e "$PN-$PV$SOURCES_EXT"; then
    echo "Downloading $PN-$PV."
    dothis wget "$SOURCES_SITE/$PN-$PV$SOURCES_EXT"
fi

echo "Extracting $PN-$PV from archive."
test -d "$PN-$PV" && rm -rf "$PN-$PV"
dothis unp "$PN-$PV$SOURCES_EXT"
dothis cd $PN-$PV

echo "Removing any previous installation of $PN, if any."
modprobe -r $MODULE
apt-get purge $PN

echo "Blacklisting r8169 module."
dothis install -d `dirname "$BLACKLIST"`
dothis "echo 'blacklist r8169' >$BLACKLIST"
dothis chmod 0644 "$BLACKLIST"
dothis perl -pi -e 's/^install:/install__:/' Makefile
dothis "echo >>Makefile"
dothis "echo >>Makefile"
dothis "echo 'install: install__' >>Makefile"
dothis "echo -e '\tinstall -m 0644 $BLACKLIST /$BLACKLIST' >>Makefile"
dothis "echo >>Makefile"

echo "Compiling $PN."
dothis make clean modules

echo "Building a debian package $PN-$PV-$KV-r0 and installing it."
dothis checkinstall \
    --type debian \
    --pkgname $PN \
    --pkgversion $PV \
    --pkgrelease ${KV}-r0 \
    --arch `dpkg --print-architecture` \
    --pkgsource "$SOURCES_SITE/$PN-$PV$SOURCES_EXT" \
    --pkglicense GPL \
    --pkggroup kernel \
    --requires linux-ubuntu-modules-$KV \
    --maintainer `whoami`@`hostname -f` \
    --strip=no \
    --nodoc \
    --default \
    make install

echo "Updating kernel module list."
dothis depmod -a

echo "Unloading r8169 module."
sudo modprobe -r r8169

echo "Loading $MODULE module."
dothis sudo modprobe $MODULE

echo
echo "Module $MODULE was successfully installed."
echo "Do not forget to reexecute this script every time you"
echo "have a kernel upgrade though."
echo

#######################################################################


```

---

