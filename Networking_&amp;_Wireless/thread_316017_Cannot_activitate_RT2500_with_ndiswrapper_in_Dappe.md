---
title: "Cannot activitate RT2500 with ndiswrapper in Dapper Drake"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Rene200 on 2006-12-10
[FONT="Arial"]Hi, hope someone can help me, I don't seem to get this working.

Info:
- Toshiba Satellite 1800 laptop
- Dapper Drake
- Tried RT2500 native drivers for Linux: didn't work
- Switched to ndiswrapper, some result, but the card's lights don't even blink
[/FONT]
Steps I took:
- first, I used this link to install the driver: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

Nothing happened, so I decided to do some checking

- "lspci | grep 00" revealed

0000:00:00.0 Host bridge: ALi Corporation M1632M Northbridge+Trident (rev 01)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)
0000:02:00.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:06:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

So, card is known

- Next "lspci -v" revealed

0000:06:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: RaLink: Unknown device 2560
        Flags: slow devsel, IRQ 11
        Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Capabilities: <available only to root>

Doesn't mean anything to me, but perhaps it helps.

- Next "lsmod | grep ndis" revealed

ndiswrapper           177364  0
usbcore               130820  3 ndiswrapper,ohci_hcd

So, ndiswrapper loaded. For info, I have already blacklisted "RT2500", because it was showing up in lsmod first

- Next "dmesg | grep ndis" revealed

[17179616.168000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179616.284000] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,09/07/2005, 3.00.05.0000) loaded
[17179616.292000] ndiswrapper (NdisWriteErrorLogEntry:230): log: C0001388, count: 1, return_address: e8299a66
[17179616.292000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1541
[17179616.292000] ndiswrapper (miniport_init:240): couldn't initialize device: C001001E
[17179616.292000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[17179616.292000] ndiswrapper (miniport_halt:271): device e7426260 is not initialized - not halting
[17179616.292000] ndiswrapper: device eth%d removed
[17179616.292000] ndiswrapper: probe of 0000:06:00.0 failed with error -22

Hmm, doesn't look good.

Tried a few things like editing iftab, but to be honest, I think the problem occurs earlier. Anyway, "cat /etc/iftab" now reveals

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:30:bd:11:57:a3 arp 1
wlan0 mac 00:0e:8e:04:46:d4 arp 1

However, when trying "sudo ifup wlan0" output is

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


That's pretty much it. Anyone any ideas?

---

### Post by FrodoB on 2006-12-10
Can you get ahold of an Edgy Eft CD and try it in Live CD mode? If it works then you can upgrade.

Changing to the latest version of ndiswrapper may also make things easier.

---

### Post by Rene200 on 2006-12-17
Thanks for your reply, FrodoB.

I decided to migrate to Edgy Eft, but unfortunately ndiswrapper did not work either. So, I decided to try the native driver again, and see of I could get that to work.

So far, no luck.

Again, I have searched quite a bit already, but haven not been able to find the solution.

Here is some data:

Environment:
- Edgy Eft

Overview:
[LIST]
[*]Clean install of Edgy Eft
[*]lsmod, this should list the RT2500 module as being loaded => is loaded
[*]lshw, this should list the ra0 interface, with the RT2500 module => it was, however, see later on
[*]iwconfig, this should list the ra0 interface => it was, however see later on
[/LIST]

The wireless did not work. Shut down the machine, started up again a day later, and ra0 was gone when listing the hardware (lshw). It then - of course - also did not show up in iwconfig.

I subsequently changed etc/network/interfaces and added 

# this is added
auto ra0
iface ra0 inet dhcp

No change after restarting.

I then decided to install the latest native driver

Installing new driver:
sudo apt-get install build-essential linux-headers-$(uname -r)
wget [http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod

Everything seems to have been installed ok, however, nothing yet. No change whatsoever. So, this begs the question "Now what?"

I have posted this in a new thread, seems like the right thing to do, being Edgy Eft (instead of Dapper Drake) => [http://www.ubuntuforums.org/showthread.php?p=1897401#post1897401](http://www.ubuntuforums.org/showthread.php?p=1897401#post1897401)

---

