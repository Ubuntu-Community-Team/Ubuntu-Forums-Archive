---
title: "intel wireless pro 3945 doesn't work"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by xchicax on 2007-10-21
hello. my computer is hp k2 pro model number k2-2a8de and my wireless card is supposedly intel wireless pro 3945. for whatever reason i cannot connect to the internet via wireless. the computer recognizes that i have a wireless card (it shows on networking as wlan0 and wmaster0), and can even pick up wireless networks, but refuses to connect to them. i have ubuntu 7.10 but had the same problem on ubuntu 7.04 as well. please help. this is what i get when i type lshw:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: eth0
       version: 10
       serial: 00:16:17:54:5d:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.179 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:09:ae:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by millfarm on 2007-10-21
I have the exact same problem.... can anyone help?

---

### Post by xchicax on 2007-10-24
i've tried to install both the iwlwifi driver and the iwp3945 driver. now the computer reports that it can connect to the internet via wireless, but in reality there is no connection. when i run lshw it shows the same thing it did before - it doesn't recognize the card as an intel card and doesn't list any drivers as the card's drivers. what do i do? i had the exact same problem on fiesty, so this is not a gutsy bug. please help!

---

### Post by millfarm on 2007-10-26
*-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network **DISABLED**
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:c8:18:64
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2d firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated


Any idea why it says disabled but I can still see the wireless networks when I click the network icon at the top panel? And how do I enable it?

---

### Post by fjlour on 2007-10-27
hello :) (my 1st post here)

I have the same wifi card, i installed Wifi Radar from Synaptics and i was able to connect to WEP wifi network here at home. But i have to use manual IP and not DHCP.

---

### Post by elctb on 2007-10-30
I finally got the wireless interface to work on my Dell Latitude D630 laptop. It uses the Intel  PRO/Wireless 3945ABG controller.

I tried the iwl3945 driver to no avail. I kept getting all kinds of errors and the wireless interface had strange names (wlan0_rename, etc).

I then tried the ipw3945 driver and now everything is working. These are the steps I followed:
. Download driver, firmware (ucode), and deamon from [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
. Copy firmware to /lib/firmware directory: (sudo cp ipw3945.ucode /lib/firmware).
. Copy deamon to /sbin directory. Note the name of the kernel has to be appended to the deamon name: (sudo cp x86_64/ipw3945d /sbin/ipw3945d-2.6.23.1).
. Copy driver to /lib/modules:
        . sudo cp ipw3945.ko /lib/modules/2.6.23.1/kernel/net/wireless
        . sudo depmod -a
        . sudo modprobe ipw3945
. To test wireless driver:
        . iwconfig
            . Should display an interface with wireless support.
        . sudo ifconfig eth1/wlan0/etc up
        . iwlist scan

---

### Post by xchicax on 2007-10-30
i tried to install the driver but according to intel's instructions couldn't succeed. i haven't seen any of the files you mentioned while in the package i downloaded from the site. can you give more instructions please?

---

### Post by elctb on 2007-10-30
Go to [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Go down the page a little bit where it says requirements.

Download and save to disk the binary microcode (ipw3945-ucode-1.14.2.tgz). You don't need the README file since it's included in the tar file.

Download and save to disk the user space regulatory daemon (ipw3945d-1.7.22.tgz). The driver won't load without it installed. You don't need the README file.

The driver requires linux kernel 2.6.13 or newer. Verify your kernel is at least 2.6.13. If it's not, get the latest kernel. You'll need to configure, build and install the kernel. It's hard the first time you do it.

You might need to install the ieee80211 kernel subsystem. I just used the ieee80211 in my kernel (2.6.23.1) so I didn't need to do this step. If you are using your own built kernel, make sure the ieee80211 module is built:
Networking -> Wireless ->  Generic IEEE 802.11 Networking Stack
Also enable: IEEE 802.11 WEP encryption (802.1x), IEEE 802.11i CCMP support, and IEEE 802.11i TKIP encryption

Don't use the stable driver form Intel's site. Instead go down the page to downloads and save to disk the latest driver (ipw3945-1.2.2.tgz).

Then follow these commands:

mkdir daemon
mkdir driver
mkdir ucode
cd ucode
tar zxvf path/ipw3945-ucode-1.14.2.tgz (path points to where you saved the file).
sudo cp ipw3945-ucode-1.14.2/ipw3945.ucode /lib/firmware
cd ../daemon
tar zxvf path/ipw3945d-1.7.22.tgz
uname -r
sudo cp ipw3945d-1.7.22/x86/ipw3945d /sbin/ipw3945d-(append string returned by uname -r).
For me it was:
sudo cp ipw3945d-1.7.22/x86_64/ipw3945d /sbin/ipw3945d-2.6.23.1
Make sure you use the right daemon for your architecture, either x86 or x86_64.
cd ../driver
tar zxvf path/ipw3945-1.2.2.tgz
cd ipw3945-1.2.2
make SHELL=/bin/bash
sudo cp ipw3945.ko /lib/modules/(your kernel)/kernel/net/wireless
For me it was:
sudo cp ipw3945.ko /lib/modules/2.6.23.1/kernel/net/wireless

Make sure you remove any other wireless drivers you installed in the /lib/modules/... directory. I had to remove the iwl3945.ko module.
sudo depmod -a
reboot

Test the driver:
iwconfig
iwlist scan
configure the interface and pass traffic.

---

### Post by Seisen on 2007-10-30
I have the same wireless card and it should work with the restricted-drivers-manager in ubuntu.

---

### Post by millfarm on 2007-10-31
> **Seisen said:**
> I have the same wireless card and it should work with the restricted-drivers-manager in ubuntu.

yes, it should, but it doesn't :(

---

### Post by millfarm on 2007-10-31
> **fjlour said:**
> hello :) (my 1st post here)

I have the same wifi card, i installed Wifi Radar from Synaptics and i was able to connect to WEP wifi network here at home. But i have to use manual IP and not DHCP.

this actually seems to work... thanks!

---

### Post by xchicax on 2007-11-05
i've installed the driver and the situation is pretty much as it was. the iwconfig shows the wireless as working, but the iwlist scan comes back with no results. my theory is that the memory card of the iwp doesn;t work and so the ubuntu can't recognize the card as such. this is the best explanation i found to why the lshw doesn't list the type and manufacturer of the card and why pccardctl ident comes back with no results. i would love any other ideas as to what's the problem. if this is the problem,  found a place in the wiki that explains how to repair it ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) under 3.1.2) but i don't know the manfid for the iwp3945. can anyone with an iwp3945 type sudo pccardctl ident and tell me what's the manfid?

when i run restricted drivers manager it says i have no hardware that requires restricted drivers.

---

### Post by elctb on 2007-11-07
This is what I get:

sudo pccardctl ident
Socket 0:
  no product info available

But if I run the info command I get:

sudo pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

My wireless controller is:

lspci |grep Wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

And the driver I'm using is:

modinfo ipw3945
filename:       /lib/modules/2.6.23.1/kernel/net/wireless/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2d
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     996B578EE03EE8D082DFF6A
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.23.1 SMP mod_unload 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           mode:network mode (0=BSS,1=IBSS) (int)

---

### Post by xchicax on 2007-11-09
what's the info command?

---

### Post by elctb on 2007-11-09
> **xchicax said:**
> what's the info command?

sudo pccardctl info

---

### Post by xchicax on 2007-11-09
the info command gives me the exact same information as yours elctb. what does your lshw command shows about the wireless card information?

---

### Post by elctb on 2007-11-09
> **xchicax said:**
> the info command gives me the exact same information as yours elctb. what does your lshw command shows about the wireless card information?

sudo lshw -C network
[sudo] password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:e0:05:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2d firmware=14.2 1:0 () ip=10.10.232.218 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:0e:e3:b8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.81 duplex=full firmware=5755m-v3.29 ip=10.2.250.121 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

