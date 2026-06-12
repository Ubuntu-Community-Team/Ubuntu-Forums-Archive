---
title: "Wireless issue (wep with RT61)!!!"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by alex4evr on 2008-03-22
Hi guys;

I am seeking your help to solve a wireless network issue related to DWL-G630 Dlink wireless card. I installed the driver from source according to the ubuntu wifi HOWTO. The wifi card can work with unsecured networks (no wep or wpa encryption) but unable to connect to secured network. In fact I am forcing the card to connect to my access point through iwconfig ra0 ap command but the connection is not active. It works like a charm when there is no wep encription. wlassistant couldn't solve the problem. Am I missing something? Does someone have the solution? Below sow information from my machine.

/***********************************************************/

lspci | grep -i net
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:03:00.0 Network controller: RaLink: Unknown device 0302

lsmod | grep rt61
rt61                  256644  1

modinfo rt61
filename:       /lib/modules/2.6.15-51-386/kernel/drivers/net/rt61.ko
author:         Paul Lin <paul_lin@ralinktech.com>
description:    RT61 Wireless Lan Linux Driver
vermagic:       2.6.15-51-386 preempt 486 gcc-4.0
depends:
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     C7CC48A77075CE2FB1F0B93


 iwconfig ra0
ra0       RT61 Wireless  ESSID:"albe.yi.org"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:53:1F:BE
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=95/100  Signal level:-48 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by keratos on 2008-03-22
I note you are using 2.6.15 which is a very old kernel.

update to latest stable kernel, say  2.6.22.

the packages for this are available or you can compile it yourself (although not necessary  for this issue)

---

### Post by moore.bryan on 2008-03-22
are you on a "stock" ubuntu install? i've seen others have issues with network-manager and changing to [wicd]("http://wicd.sourceforge.net/") fixed many of their wep/wpa1/2 issues.

---

### Post by unutbu on 2008-03-22
If you'd like to take a few stabs from the command line before installing more stuff,
try:
```

sudo ifconfig ra0 down
sudo dhclient -r ra0
sudo ifconfig ra0 up
sudo iwconfig ra0 essid "ESSID_IN_QUOTES"
sudo iwconfig ra0 key HEX_KEY
sudo iwconfig ra0 key open  
sudo iwconfig  ra0 mode Managed
sudo dhclient ra0

```

This was taken from [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495).

---

### Post by alex4evr on 2008-03-22
will try the command line options befor compiling the latest kernel, and repost the results again. Just another question, I have wlassistant for managing wireless connection, what is the difference with wicd and what the latter are able to do better than wlassistant? aren't both based on command line options with a gui facility?

---

### Post by keratos on 2008-03-22
wicd is an app for GNOME (uses gnome libs)

wlassitant is an app for KDE (uses kde libs)

both are useful apps, there are others also.

but generally if you are using the GNOME desktop (ubuntu) then go for wicd, if your using KDE (Kubuntu) then go for wlassistant.

that doesnt mean you have to use a GNOME app in ubuntu or KDE app in Kubuntu, its just that extra libraries (and disk space/performance) might be an issue if you switch these around.

try them both!

---

### Post by imdano on 2008-03-22
Wicd uses gtk, nothing gnome specific.  I think wlassistant just uses Qt. Each app just uses the same UI library as a particular desktop environment, rather than being tied to a bunch of libraries specific to that desktop environment.

---

### Post by keratos on 2008-03-23
> **imdano said:**
> Wicd uses gtk, nothing gnome specific.  I think wlassistant just uses Qt. Each app just uses the same UI library as a particular desktop environment, rather than being tied to a bunch of libraries specific to that desktop environment.

Yes I was aware of that but was trying to maintain simple answers: Gnome uses gtk, KDE uses qt.

Thats where I was coming from.

Clearly however, there is nothing to prevent a gtk app running in KDE and qt in GNOME (just more libs to install and potentially inconsistent appearances)

Notwithstanding, he should just try them both and see which one he likes. 

Simple huh !

---

### Post by chichilalescu on 2008-04-17
I can confirm the same problem: I connect to another laptop in Ad-Hoc mode, and it only works with no wep.
my kernel is 2.6.20-16-386.
this is what happens when I plug in my PCMCIA card (taken from the output of dmesg):
```

[   45.508000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   45.508000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   45.508000] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   45.508000] RT61: Vendor = 0x1814, Product = 0x0301
[   45.508000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   45.640000] RT61: RfIcType= 3
[  138.464000] RT61: RfIcType= 3
[  148.640000] ra0: no IPv6 routers present

```

I tried a different kernel at some point (2.6.22 something), and it did work with encryption when connecting to a router, but a few weeks ago I installed ndiswrapper, blacklisted some stuff and installed some other versions of the driver for the wireless from source, and I think that kernel became unusable (on my laptop) for the wireless. I'll use it without wep for now, and I'll probably make a clean install of kubuntu 8.04 when it comes out.

on a sidenote, when it comes to installing a newer kernel, I would be very happy if I had a kernel that worked for my configuration, and I would keep it.

---

