---
title: "Broadcom 43b1: Trying to install NDISWRAPPER"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by Tyler_Bogan on 2013-09-16
Hello, I am trying to install ndis wrapper so I can install my wireless card which is: 03:00.0 Network controller: Broadcom Corporation Device 43b1(rev 03) however I can't install it using the terminal or any other methods.In terminal when I try to install NDISWRAPPER-common_1.56-1_all.deb it reas E: unable to locate packages and E: COuldn't find any package by regex 'NDISWRAPPER COMMON'.I am using ubuntu 13.04. P.S. I just started with ubuntu today so I am total noob.

---

### Post by sanderj on 2013-09-16
Start Ubuntu Software Center, search for "ndiswrapper", in the search results click on "show technical items" at the very bottom. You should see "ndiswrapper-common". Click on it to install.

HTH

---

### Post by Tyler_Bogan on 2013-09-16
The option to use this source is greyed out.

---

### Post by squakie on 2013-09-16
What release of Ubuntu?  Have you tried restricted drivers?  While I used to be a strong advocate of ndiswrapper (and of course ndisgtk to make things easy), there is only a rare need anymore.  More and more wireless chipsets are being supported, and it's just a matter of installing things.  To start, please post back the entire line from lsusb or lspci where you got you information.

You will find that most of the posts for ndiswrapper are old and out of date now.

---

### Post by Tyler_Bogan on 2013-09-16
00:00.0 Host bridge: Intel Corporation Haswell DRAMController (rev 06)
            Subsystem:ASRock Incorporation Device 0c00
            Flags: busmaster, fast devsel, latency 0
            Capabilities:<access denied>
 
00:01.0 PCI bridge: Intel Corporation Haswell PCI Express x16Controller (rev 06) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0
            Bus:primary=00, secondary=01, subordinate=01, sec-latency=0
            I/O behindbridge: 0000e000-0000efff
            Memorybehind bridge: e0000000-f00fffff
            Capabilities:<access denied>
            Kerneldriver in use: pcieport
 
00:14.0 USB controller: Intel Corporation Lynx Point USB xHCIHost Controller (rev 04) (prog-if 30 [XHCI])
            Subsystem:ASRock Incorporation Device 8c31
            Flags: busmaster, medium devsel, latency 0, IRQ 41
            Memory atf0120000 (64-bit, non-prefetchable) [size=64K]
            Capabilities:<access denied>
            Kerneldriver in use: xhci_hcd
 
00:16.0 Communication controller: Intel Corporation LynxPoint MEI Controller #1 (rev 04)
            Subsystem:ASRock Incorporation Device 8c3a
            Flags: busmaster, fast devsel, latency 0, IRQ 44
            Memory atf013b000 (64-bit, non-prefetchable) [size=16]
            Capabilities:<access denied>
            Kerneldriver in use: mei
 
00:19.0 Ethernet controller: Intel Corporation EthernetConnection I217-V (rev 04)
            Subsystem:ASRock Incorporation Device 153b
            Flags: busmaster, fast devsel, latency 0, IRQ 42
            Memory atf0100000 (32-bit, non-prefetchable) [size=128K]
            Memory atf0139000 (32-bit, non-prefetchable) [size=4K]
            I/O ports atf040 [size=32]
            Capabilities:<access denied>
            Kerneldriver in use: e1000e
 
00:1a.0 USB controller: Intel Corporation Lynx Point USBEnhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
            Subsystem:ASRock Incorporation Device 8c2d
            Flags: busmaster, medium devsel, latency 0, IRQ 16
            Memory atf0138000 (32-bit, non-prefetchable) [size=1K]
            Capabilities:<access denied>
            Kerneldriver in use: ehci-pci
 
00:1b.0 Audio device: Intel Corporation Lynx Point HighDefinition Audio Controller (rev 04)
            Subsystem:ASRock Incorporation Device 1150
            Flags: busmaster, fast devsel, latency 0, IRQ 46
            Memory atf0130000 (64-bit, non-prefetchable) [size=16K]
            Capabilities:<access denied>
            Kerneldriver in use: snd_hda_intel
 
00:1c.0 PCI bridge: Intel Corporation Lynx Point PCI ExpressRoot Port #1 (rev d4) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0
            Bus:primary=00, secondary=02, subordinate=02, sec-latency=0
            I/O behindbridge: 00002000-00002fff
            Memorybehind bridge: f0500000-f06fffff
            Prefetchablememory behind bridge: 00000000f0700000-00000000f08fffff
            Capabilities:<access denied>
            Kerneldriver in use: pcieport
 
00:1c.3 PCI bridge: Intel Corporation Lynx Point PCI ExpressRoot Port #4 (rev d4) (prog-if 00 [Normal decode])
            Flags: busmaster, fast devsel, latency 0
            Bus:primary=00, secondary=03, subordinate=03, sec-latency=0
            Memorybehind bridge: f0200000-f04fffff
            Capabilities:<access denied>
            Kerneldriver in use: pcieport
 
00:1d.0 USB controller: Intel Corporation Lynx Point USBEnhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
            Subsystem:ASRock Incorporation Device 8c26
            Flags: busmaster, medium devsel, latency 0, IRQ 23
            Memory atf0137000 (32-bit, non-prefetchable) [size=1K]
            Capabilities:<access denied>
            Kerneldriver in use: ehci-pci
 
00:1f.0 ISA bridge: Intel Corporation Lynx Point LPCController (rev 04)
            Subsystem:ASRock Incorporation Device 8c44
            Flags: busmaster, medium devsel, latency 0
            Capabilities:<access denied>
            Kerneldriver in use: lpc_ich
 
00:1f.2 SATA controller: Intel Corporation Lynx Point 6-portSATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
            Subsystem:ASRock Incorporation Device 8c02
            Flags: busmaster, 66MHz, medium devsel, latency 0, IRQ 43
            I/O ports atf090 [size=8]
            I/O ports atf080 [size=4]
            I/O ports atf070 [size=8]
            I/O ports atf060 [size=4]
            I/O ports atf020 [size=32]
            Memory atf0136000 (32-bit, non-prefetchable) [size=2K]
            Capabilities:<access denied>
            Kerneldriver in use: ahci
 
00:1f.3 SMBus: Intel Corporation Lynx Point SMBus Controller(rev 04)
            Subsystem:ASRock Incorporation Device 8c22
            Flags:medium devsel, IRQ 10
            Memory atf0135000 (64-bit, non-prefetchable) [size=256]
            I/O ports atf000 [size=32]
 
01:00.0 VGA compatible controller: Advanced Micro Devices[AMD] nee ATI Cape Verde PRO [Radeon HD 7750] (prog-if 00 [VGA controller])
            Subsystem:XFX Pine Group Inc. Device 3248
            Flags: busmaster, fast devsel, latency 0, IRQ 45
            Memory ate0000000 (64-bit, prefetchable) [size=256M]
            Memory atf0000000 (64-bit, non-prefetchable) [size=256K]
            I/O ports ate000 [size=256]
            ExpansionROM at f0040000 [disabled] [size=128K]
            Capabilities:<access denied>
            Kerneldriver in use: radeon
 
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATICape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
            Subsystem:XFX Pine Group Inc. Device aab0
            Flags: busmaster, fast devsel, latency 0, IRQ 47
            Memory atf0060000 (64-bit, non-prefetchable) [size=16K]
            Capabilities:<access denied>
            Kerneldriver in use: snd_hda_intel
 
03:00.0 Network controller: Broadcom Corporation Device 43b1(rev 03)
            Subsystem:AzureWave Device 2123
            Flags: busmaster, fast devsel, latency 0, IRQ 5
            Memory atf0400000 (64-bit, non-prefetchable) [size=32K]
            Memory atf0200000 (64-bit, non-prefetchable) [size=2M]
            Capabilities:<access denied>

currently running 12.04 UBUNTU

That's what lspci gives me

---

### Post by squakie on 2013-09-16
Okay, now post back the output of:

lspci -vnn -d 14e4:

---

### Post by squakie on 2013-09-17
Okay, what seems to be a bad news/good news kind of thing:  it is known on launchpad that this device is not supported by the kernel, but there is a partial solution posted.  It doesn't give total functionality for everything the device does (bluetooth included), but can apparently at least get the wireless going in the 2.4ghz range:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173761)

If things have changed I'm sure someone will post back.

---

### Post by fireflower on 2013-09-17
Had this exact same problem with 10.04. It's how my first day with Ubuntu went, too. You really need two computers. On the second, working computer, a simple Google search presented the solution to the problem. Or at least, the "how." Then I had to actually do annoying things like find the Windows drivers on the wireless card company's website, burn the Windows drivers to a disc, and copy them onto the Ubuntu machine. It involved transcribing lines of code that I did not understand, from sources I found via Google search. Very sketchy. But with a fresh install there's nothing to break is there?

---

### Post by squakie on 2013-09-17
IF you are talking about windows drivers, that does require ndiswrapper, with a few things that need to be noted up front:

- normally the driver must be a windows xp driver - this may have changed
- the architecture of the OS (32 or 64 bit) and the driver must match

copy the windows drivers to a folder, say something like ~/mydrivers.  This needs to include the .inf and .sys files.

If you have a working network connection you should be able to the following:

sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install ndisgtk

Note this only installs the software tools - putting them to use follows down further in this post.

If you don't have an internet connection:

- with ubuntu booted and running, load the livedvd
- use the file explorer and navigate the livedvd as follows:
1. go to the /pool/main/n folder.  You should see a folder for ndisgtk and ndiswrapper.
2. go to the ndiswrapper folder.
3. click on the ndiswrapper-common file to start its installation
4. when that has finished, click on the ndiswrapper-utils-1.9 file to begin its installation. 
(note the steps 3 and 4 must be done in that order - ndiswrapper-common must be installed before you can install ndiswrapper-utils-1.9)
5. navigate back to the /pool/main/n folder
6. go to the ndisgtk folder
7. click on the ndisgtk file to begin its installation

These steps also just installed the software tools.

AFTER the software tools have been installed:

Use the unity menu to locate ndisgtk  and launch it.

Click on "new" or "add" or what ever it is.

Point it to the windows driver .inf file (if you followed above it would be the mydrivers folder off your home account (~.mydrivers/xxxxxxx.inf, where "xxxxxxx.inf" should be replaced with the name of your .inf file).

Click "ok", "go" or what ever it is.  This should install the driver via ndiswrapper (ndisgtk is a graphical front-end to ndiswrapper, and normally - but not always - takes care of the command line things you might see in older posts about ndiswrapper).

Exit ndisgtk, wait about 30 seconds, then check in network manager to be sure (1) networking is enabled and (2) wireless is enabled.  If not then click them.

When both networking and wireless are enabled, see if you see any wireless networks in network manager.  If so, the driver is probably working.

Sorry if I can't match the exact "go" "ok" or whatever prompts - I haven't done the ndiswrapper thing in a couple of years.

Also - those folders and files used to be on the livedvd, but I haven't checked lately.  If you don't find them please post back.

---

