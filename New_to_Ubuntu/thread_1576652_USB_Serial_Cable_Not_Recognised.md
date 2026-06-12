---
title: "USB Serial Cable Not Recognised"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by simong6 on 2010-09-17
Hi there,

I've been flirting between windows and Ubuntu for some time now, but have finally made my mind up and stuck with Ubuntu. 

HOWEVER....... I use a program called VCDS for fault diagnosing on my car, the cable is a USB serial cable for those unfamiliar its similar to this [http://cgi.ebay.co.uk/006-VAG-COM-USB-DIAGNOSTIC-409-1-CABLE-OBD2-II-LEAD-VAG-/220663506461?pt=UK_Diagnostic_Tools_Equipment&hash=item336091e61d]("http://ubuntuforums.org/clicky")

it came with a Drivers disk, which is recognised in windows, however I can't seem to get it to register on Ubuntu, I've installed the program with no problems what so ever via the Wine program.

other than that, I absolutely adore Ubuntu, and can't wait to fully explore all that it can do for me!!

---

### Post by lukeiamyourfather on 2010-09-17
That's not a serial cable. That's an ODBII cable which is relatively specialized. You might have to dual boot or use a virtual machine for that.

---

### Post by mr_luksom on 2010-09-17
What about Freediag? [http://freediag.sourceforge.net/](http://freediag.sourceforge.net/) Let me know how you go, I've always wanted buy the cable and do this with my car...

---

### Post by simong6 on 2010-09-21
> **mr_luksom said:**
> What about Freediag? [http://freediag.sourceforge.net/](http://freediag.sourceforge.net/) Let me know how you go, I've always wanted buy the cable and do this with my car...

no problem, once i actually figure out how to actually install it i'll let you know how i get on!

---

### Post by lkraemer on 2010-09-22
Why don't you post the output of:
```

lsusb

```
Then plug in your USB ODBII Reader's USB Cable and after a couple
of minutes try this:
```

lsusb
dmesg | tail -n 50

```
Post this output also.

lk

---

### Post by simong6 on 2010-09-23
```
 simon@simon-laptop:~$ lsusb 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 002: ID 1d57:b2b1   
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
``````

 simon@simon-laptop:~$ lsusb demsg | tail -n 50 
 Usage: lsusb [options]... 
 List USB devices 
   -v, --verbose 
       Increase verbosity (show descriptors) 
   -s [[bus]:][devnum] 
       Show only devices with specified device and/or 
       bus numbers (in decimal) 
   -d vendor:[product] 
       Show only devices with the specified vendor and 
       product ID numbers (in hexadecimal) 
   -D device 
       Selects which device lsusb will examine 
   -t 
       Dump the physical USB device hierarchy as a tree 
   -V, --version 
       Show version of program
 
```i get these messages

---

### Post by PriceChild on 2010-09-23
Please try that last one again, pressing enter after the text in each box.
```
lsusb
```
```
dmesg | tail -n 50
```
Also watch out, I believe it is dmesg, not demsg.

---

### Post by simong6 on 2010-09-23
tried again,

i get this now

```

simon@simon-laptop:~$ dmesg | tail -n 50
[   23.310097] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.310155] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[   23.485261] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.485289] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.621048] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   23.628073] Console: switching to colour frame buffer device 80x30
[   23.644255] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   23.646578] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.647570] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.653086] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.654090] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   23.671196] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.671210] nvidia 0000:01:00.0: setting latency timer to 64
[   23.671216] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   23.672226] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   23.702811] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   23.820921] type=1505 audit(1285249040.906:5):  operation="profile_load" pid=737 name="/usr/share/gdm/guest-session/Xsession"
[   23.834071] type=1505 audit(1285249040.918:6):  operation="profile_replace" pid=739 name="/sbin/dhclient3"
[   23.834725] type=1505 audit(1285249040.918:7):  operation="profile_replace" pid=739 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.835082] type=1505 audit(1285249040.918:8):  operation="profile_replace" pid=739 name="/usr/lib/connman/scripts/dhclient-script"
[   23.855271] type=1505 audit(1285249040.938:9):  operation="profile_load" pid=741 name="/usr/bin/evince"
[   23.902900] type=1505 audit(1285249040.986:10):  operation="profile_load" pid=741 name="/usr/bin/evince-previewer"
[   23.909536] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.958674] type=1505 audit(1285249041.042:11):  operation="profile_load" pid=741 name="/usr/bin/evince-thumbnailer"
[   24.444821] ppdev: user-space parallel port driver
[   34.136019] eth1: no IPv6 routers present
[   46.329891] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   47.344026] ipw2200: Failed to send SCAN_REQUEST_EXT: Command timed out.
[   48.344025] ipw2200: Failed to send CARD_DISABLE: Command timed out.
[   54.488240] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   54.696427] lib80211_crypt: registered algorithm 'CCMP'
[   54.709691] padlock: VIA PadLock not detected.
[   54.715746] lib80211_crypt: registered algorithm 'TKIP'
[   64.988026] eth1: no IPv6 routers present
[  129.976063] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  130.158270] usb 3-1: configuration #1 chosen from 1 choice
[  130.245459] usbcore: registered new interface driver usbserial
[  130.246041] USB Serial support registered for generic
[  130.246624] usbcore: registered new interface driver usbserial_generic
[  130.246627] usbserial: USB Serial Driver core
[  130.274740] USB Serial support registered for FTDI USB Serial Device
[  130.276348] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[  130.276490] usb 3-1: Detected FT232BM
[  130.276497] usb 3-1: Number of endpoints 2
[  130.276503] usb 3-1: Endpoint 1 MaxPacketSize 64
[  130.276508] usb 3-1: Endpoint 2 MaxPacketSize 64
[  130.276514] usb 3-1: Setting MaxPacketSize 64
[  130.278264] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[  130.278303] usbcore: registered new interface driver ftdi_sio
[  130.278308] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

```

---

### Post by applejuicekiss on 2011-03-30
any luck with this?  our jetta tdi MIL light has come one.  would like to use vcds go get the error code.

it appears that the serial connection version of vcds works for some in wine, but there is no kernel driver for the usb connector required for the usb version.  i'm hoping someone gets the usb version to work, as my netbook has no serial connector.

thanks in advance

---

### Post by wep940 on 2011-03-30
Judging from the output of the lspci, I think the following refers to the device:
 
[  129.976063] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  130.158270] usb 3-1: configuration #1 chosen from 1 choice
[  130.245459] usbcore: registered new interface driver usbserial
[  130.246041] USB Serial support registered for generic
[  130.246624] usbcore: registered new interface driver usbserial_generic
[  130.246627] usbserial: USB Serial Driver core
[  130.274740] USB Serial support registered for FTDI USB Serial Device
[  130.276348] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[  130.276490] usb 3-1: Detected FT232BM
[  130.276497] usb 3-1: Number of endpoints 2
[  130.276503] usb 3-1: Endpoint 1 MaxPacketSize 64
[  130.276508] usb 3-1: Endpoint 2 MaxPacketSize 64
[  130.276514] usb 3-1: Setting MaxPacketSize 64
[  130.278264] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0
[  130.278303] usbcore: registered new interface driver ftdi_sio
[  130.278308] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
 
 
I think it is recognizing the device perhaps you need to have the software point at ttyUSB0 as the device.  Also, is the software native Linux or are you running a Windows program in Wine?  If Wine, I don't believe it supports USB devices other than keyboards, mice, etc..

---

