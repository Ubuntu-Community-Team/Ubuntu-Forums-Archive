---
title: "Belkin Problem"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by AMP on 2005-06-12
Okay i installed ndiswrapper fine, installed the driver, the light turns on but i never get any link, it fails activation, and the link light doesnt turn off.

Can anyone please help me??? This is the 3rd time iv had troubble and never really got awnsers.

---

### Post by spd106 on 2005-06-13
Could you provide some more information please. Such as output from each of these
```
$lspci
$dmesg | grep ndis
$ndiswrapper -l
$cat /etc/network/interfaces
```

You can edit out any unrelated lines and/or encryption keys.

---

### Post by AMP on 2005-06-13
[QUOTE=spd106]Could you provide some more information please. Such as output from each of these
```
$lspci
$dmesg | grep ndis
$ndiswrapper -l
$cat /etc/network/interfaces
```

You can edit out any unrelated lines and/or encryption keys.[/QUOTE]
 $lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
0000:00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:01:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

$dmesg | grep ndis
ndiswrapper version 1.2rc1 loaded (preempt=yes,smp=no)
ndiswrapper: driver bcmwl5 (Broadcom,12/29/2002, 3.10.36.0) loaded
ndiswrapper: using irq 9
wlan0: ndiswrapper ethernet device 00:30:bd:90:2a:ae using driver bcmwl5, configuration file 14E4:4320.5.conf
ndiswrapper (set_auth_mode:584): setting auth mode failed (C0010015)

$ndiswrapper -l

bcmwl5  driver present, hardware present

$cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp

auto wlan0

iface eth0 inet dhcp

auto eth0


There you are all my results under the command.

---

### Post by spd106 on 2005-06-14
I notice that you have no entry in your /etc/network/interfaces file for hotplug. 
If you are using cardbus then you should have something like this.

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

```

My card didn't work correctly because i had "map eth0" instead of "map wlan0".

You may want to check that you have hotplug up and running, though i'm not sure how to do this or indeed what will happen if it isn't. It's probably worth a try though. You will probably have to reinsert the card afterwards.

Hope this helps

---

### Post by AMP on 2005-06-15
[QUOTE=spd106]I notice that you have no entry in your /etc/network/interfaces file for hotplug. 
If you are using cardbus then you should have something like this.

```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

```

My card didn't work correctly because i had "map eth0" instead of "map wlan0".

You may want to check that you have hotplug up and running, though i'm not sure how to do this or indeed what will happen if it isn't. It's probably worth a try though. You will probably have to reinsert the card afterwards.

Hope this helps[/QUOTE]
 okay, ill try that, but i just installed normally and followed the Belkin How To and it sitll wont work!

---

### Post by talon on 2005-06-15
I am also having a problem with my Belkin wireless. I have a belkin router and A belkin USB device. I have tried reapetedly to get them working on my linux partition but they just won't. The drivers are loaded fine with ndiswrapper, but I can't connct to my network or get an IP address from the router. If I set it to static IP address, it doesn't work either.
I have asked about this problem serveral times and none of the fixes suggested so far have worked.

---

### Post by AMP on 2005-06-15
[QUOTE=talon]I am also having a problem with my Belkin wireless. I have a belkin router and A belkin USB device. I have tried reapetedly to get them working on my linux partition but they just won't. The drivers are loaded fine with ndiswrapper, but I can't connct to my network or get an IP address from the router. If I set it to static IP address, it doesn't work either.
I have asked about this problem serveral times and none of the fixes suggested so far have worked.[/QUOTE]
 Good luck with usb i hear its even more hard than others

---

### Post by talon on 2005-06-16
your telling me.......................... I'm going to try and get a wireless pci card....
But in the meantime anyone any ideas?

---

