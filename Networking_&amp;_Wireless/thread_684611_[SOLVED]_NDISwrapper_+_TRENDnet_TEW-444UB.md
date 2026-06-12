---
title: "[SOLVED] NDISwrapper + TRENDnet TEW-444UB"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by patryk77 on 2008-02-01
Hello, I am trying to get my Trendnet TEW-444UB wireless card to work in Ubuntu 7.10.

I installed ndiswrapper and the Windows drivers, but there are no clear instructions on what I need to do now.

```
p:~$ sudo ndiswrapper -l
net5523 : driver installed

```

Now, I have plugged the card into a USB port, and it doesn't say "device present", as I believe it should.

From dmesg:
```
[540062.123298] ndiswrapper version 1.45 loaded (smp=yes)
[540062.131412] usbcore: registered new interface driver ndiswrapper

```

So what do I do to make it detect my card?
Thanks

---

### Post by Hightide on 2008-02-01
Hi patryk77

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case

check via 'ifconfig' that you do see an wlan0 interface, if not check Kevdog's 'how to'

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

regards
:)

---

### Post by patryk77 on 2008-02-01
Thanks for the reply, but I'm still stuck...

I tried running "lsusb" to detect the device ID to use, but I don't think it's even detected...

```
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000
```

---

### Post by patryk77 on 2008-02-02
I also get this in dmesg when I plug it in:

[26928.398188] usb 5-8: new high speed USB device using ehci_hcd and address 11

Address increases by 1 every time I unplug / replug it

Edit: Oops... sorry about the double post

---

### Post by patryk77 on 2008-02-04
Well, it seems I have found a solution... It's not very pretty but it works.

Remove the NIC, disable High-speed USB by entering:

```
$ sudo modprobe -r ehci_hcd

(plug it back in)

$ lsusb 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 157e:3007  
Bus 004 Device 001: ID 0000:0000 

$ ndiswrapper -l
athfmwdl : driver installed
net5523 : driver installed
        device (157E:3007) present

$ sudo ifconfig 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1280296 (1.2 MB)  TX bytes:1280296 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:14:D1:C1:C4:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Note that this will make your USB 2.0 devices run at 1.1 Speeds:

```
[239842.706074] ehci_hcd 0000:00:1d.7: remove, state 4
[239842.706090] usb usb5: USB disconnect, address 1
[239842.715018] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[239842.715144] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[239858.036350] usb 4-2: new full speed USB device using uhci_hcd and address 3
[239858.204345] usb 4-2: configuration #1 chosen from 1 choice
[239858.352189] usb 4-2: reset full speed USB device using uhci_hcd and address 3
[239858.513213] ndiswrapper: driver net5523 (,07/27/2005,1.5.0.102) loaded
[239858.514161] ndiswrapper (ZwQueryValueKey:2379): not fully implemented (yet)
[239859.483771] wlan0: ethernet device 00:14:d1:c1:c4:3d using NDIS driver: net5523, version: 0x10005, NDIS version: 0x501, vendor: '', 157E:3007.F.conf
[239859.544235] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
```

---

