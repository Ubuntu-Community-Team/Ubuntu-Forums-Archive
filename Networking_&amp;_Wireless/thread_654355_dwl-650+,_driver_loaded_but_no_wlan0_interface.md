---
title: "dwl-650+, driver loaded but no wlan0 interface"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by baosheng on 2007-12-31
Hi,

I have a D-Link DWL-650+ wireless card. I used it well on Ubuntu 6.06 and 7.04. Now after I plugged into my PCMAIC slot and "modprobe acx", the device has been recognized properly, but i can't find any wireless network interface.
[html]
forrest@flavia:~$ lspci | grep ACX
05:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
[/html]

I tried iwconfig, but nothing

[html]forrest@flavia:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/html]

I also can't see anything on GNOME network manager.

Can anyone help me?

---

### Post by istrebitjel on 2008-01-17
I have the same thing on 7.04 and 8.04.

```
$ sudo modprobe acx
$ dmesg | grep acx
[ 1750.356000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[ 1750.356000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 1750.364000] usbcore: registered new interface driver acx_usb
[ 2338.932000] usbcore: deregistering interface driver acx_usb
[ 2344.140000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[ 2344.140000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 2344.144000] usbcore: registered new interface driver acx_usb
$ lsmod | grep acx
acx                    98564  0 
usbcore               134280  5 acx,usbhid,ehci_hcd,uhci_hcd
$lspci -vv
03:00.0 Network controller: Texas Instruments Unknown device 0400
        Subsystem: D-Link System Inc Unknown device 3b00
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at 4000 [disabled] [size=32]
        Region 1: Memory at 3c010000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Region 2: Memory at 3c000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

It's funkyi, I looked at many other threads with acx trouble and all of them had some kind of problem in the log, when loading the module, but not here.

Any ideas? Pretty please! ;)

---

### Post by istrebitjel on 2008-01-19
bump. still desperate :confused:

---

### Post by istrebitjel on 2008-01-24
Wow, I upgraded to kernel 2.6.22-14-generic and all of a sudden it worked.

Well, I had to manually configure the wireless network, it wouldn't work through network manager, but now I'm connected through my wireless network on my dwl-650+ using Ubuntu 7.10,

---

