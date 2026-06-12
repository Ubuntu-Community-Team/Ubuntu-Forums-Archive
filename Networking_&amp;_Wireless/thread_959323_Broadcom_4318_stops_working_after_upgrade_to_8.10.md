---
title: "Broadcom 4318 stops working after upgrade to 8.10"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Chris107 on 2008-10-26
After upgrading to 8.10, my Broadcom wireless card decides to stop working.  I see the card and it says it's activated in the Hardware Drivers manager but it doesn't connect to anything.  Has anyone been able to get their card working in 8.10?

---

### Post by zorkerz on 2008-11-23
Im using an ubuntu 8.10 live usb with the same symptoms. Broadcom B43 drivers are activated in Hardware Drivers but no wireless networks are visible.

Have you made any discoveries on this issue?

---

### Post by Olivier2371 on 2008-11-23
Instead of using the broadcom driver, have you tried the STA driver.

Don't forget to reboot.

---

### Post by zorkerz on 2008-11-23
I have not where can I find info about that?

---

### Post by Olivier2371 on 2008-11-23
In the menu.

System->Administration->Hardware Drivers

Have you updated the system?

System->Administration->Update Manager

If not update then Reboot.

---

### Post by Ayuthia on 2008-11-23
> **Olivier2371 said:**
> Instead of using the broadcom driver, have you tried the STA driver.

Don't forget to reboot.

Actually, the 4318 card is not supported in the Broadcom STA driver.  It currently covers the 4311, 4312, 4321, 4322, and some 4328 cards.  Here is a link for some info about the driver:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
The 4328 card is not listed on that page, but the driver does show that it supports it and some people have been able to get it to work.

Most likely if you try to go to System->Administration->Hardware Drivers, it will only provide the b43 option.

Can you post the results of:
```
lsmod|grep -e b43 -e ssb -e ndiswrapper -e wl
lshw -C network
```Hopefully there is something there that might help.

---

### Post by IronFox on 2008-11-23
Im having the same problem with the broadcom 4306 card.  After using the hardware drivers under system-admin-hardware drivers, everything lights up, my wireless light is on, ifconfig shows that its sending out packets but i cant connect or see any wireless signals.

---

### Post by Ayuthia on 2008-11-23
> **IronFox said:**
> Im having the same problem with the broadcom 4306 card.  After using the hardware drivers under system-admin-hardware drivers, everything lights up, my wireless light is on, ifconfig shows that its sending out packets but i cant connect or see any wireless signals.

Can you post the results of:
```
lspci -nnm
lshw -C network
```
Also, are you trying to connect to an encrypted router (WEP/WPA/WPA2)?

---

### Post by kevdog on 2008-11-23
Ayuthia

Do you have a masterlist of what Broadcom chipsets are covered by
b43
STA
wl

Any others am I missing?

---

### Post by IronFox on 2008-11-23
root@jordan-laptop:/home/jordan# lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "82915G/P/GV/GL/PL/910GL Memory Controller Hub [2580]" -r0e "Hewlett-Packard Company [103c]" "Device [3082]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82915G/P/GV/GL/PL/910GL PCI Express Root Port [2581]" -r0e "" ""
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [2660]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [2658]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [2659]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [265a]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [265b]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [265c]" -r03 -p20 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 PCI Bridge [244e]" -rd3 -p01 "" ""
00:1e.2 "Multimedia audio controller [0401]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [266e]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1e.3 "Modem [0703]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [266d]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [2640]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [266f]" -r03 -p8a "Hewlett-Packard Company [103c]" "Device [3082]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [266a]" -r03 "Hewlett-Packard Company [103c]" "Device [3082]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "M22 [Mobility Radeon X300] [5460]" "Hewlett-Packard Company [103c]" "Device [3082]"
0b:00.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx21/x515 Cardbus Controller [8031]" "Hewlett-Packard Company [103c]" "Device [3082]"
0b:00.2 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "OHCI Compliant IEEE 1394 Host Controller [8032]" -p10 "Hewlett-Packard Company [103c]" "Device [3082]"
0b:00.3 "Mass storage controller [0180]" "Texas Instruments [104c]" "PCIxx21 Integrated FlashMedia Controller [8033]" "Hewlett-Packard Company [103c]" "Device [3082]"
0b:00.4 "SD Host controller [0805]" "Texas Instruments [104c]" "PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [8034]" "Hewlett-Packard Company [103c]" "Device [3082]"
0b:02.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Hewlett-Packard Company [103c]" "Device [3082]"
0b:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Hewlett-Packard Company [103c]" "Device [12f8]"
root@jordan-laptop:/home/jordan# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a2:1f:f2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ea:ec:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:1f:2a:ca:f9:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I`m trying to connect to both WEP and non-encrypted networks

---

### Post by kevdog on 2008-11-23
How are you trying to connect?

What does
sudo iwlist wlan0 scan show?

For an unencrypted wireless network have you just tried the following:

sudo dhclient -r wlan0
sudo ifconfig wlan0 essid "<ESSID IN QUOTES>"
sudo dhclient dlan0

---

### Post by Ayuthia on 2008-11-23
> **kevdog said:**
> Ayuthia

Do you have a masterlist of what Broadcom chipsets are covered by
b43
STA
wl

Any others am I missing?
The b43 drivers are pretty much what is listed at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43).  The only thing is the 4312 rev 01 card (14e4:4315).  Their site still lists it under the 4310 but the name changed somewhere around the time 8.04.1 came out.  It is unsupported.  The 4306 (rev 02 and 03)and 4318 (rev 02 and 03) cards have been having mixed results in Ubuntu.

The STA and wl drivers are the same drivers.  The following are the ones I have seen work:
4311, 4312, 4321, 4322, and 4328
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) lists the first four cards, but modinfo shows the following cards:
```
filename:       /lib/modules/2.6.27-ARCH/kernel/net/wireless/hybrid/wl.ko
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        ieee80211_crypt
vermagic:       2.6.27-ARCH SMP preempt mod_unload 
parm:           oneonly:int
parm:           piomode:int
parm:           nompc:int
parm:           name:string

```This info is coming from Arch, but Ubuntu shows the same alias info.  I have to say that I don't think that I have seen the 14e4:432A-14e4:432D chipsets yet.  I have seen a few 4328 cards work with it and I have seen a smaller set that have not worked which is probably why the site does not list the card.

It also looks like the 14e4:4315 chipset does not like WEP but seems to work with WPA.

---

### Post by kevdog on 2008-11-23
How do you keep track of this S***?!  I mean stuff!

---

### Post by Ayuthia on 2008-11-23
> **kevdog said:**
> How do you keep track of this S***?!  I mean stuff!

I have most of it in my head.  It is probably because I have spent almost every day in this section trying to help with the Broadcom cards since the early alpha stages of Hardy (the start of the b43 driver).  I just leave the tough questions for you.

---

### Post by myharshdesigner on 2008-11-24
i will update it

---

### Post by kevdog on 2008-11-24
Ayuthia

They pretty much did away with the stickies in this section, however that information would be good to list somewhere.  Too bad it couldn't be listed in a wiki or something.  That is really good informatin.

---

### Post by IronFox on 2008-11-24
jordan@jordan-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for jordan: 
wlan0     No scan results

jordan@jordan-laptop:~$ dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
wmaster0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted
jordan@jordan-laptop:~$ sudo ifconfig wlan0 essid "HOME1"
essid: Unknown host
ifconfig: `--help' gives usage information.

---

