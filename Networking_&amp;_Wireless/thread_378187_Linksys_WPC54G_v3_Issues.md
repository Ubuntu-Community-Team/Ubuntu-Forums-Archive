---
title: "Linksys WPC54G v3 Issues"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by NjRef511 on 2007-03-07
Ladies and Gents:

I've been spending the past 6 hours attempting to get Ubuntu setup on my Inspiron 1100 (I know, with all the driver issues, could i have picked a better laptop to convert?)  However, it seems that I've run into another driver issue, this one being my wireless card.

I have a Linksys WPC54G v3 wireless card.  I have loaded the most recent version of the drivers via NDISWrapper, but to no avail.  It detects the card, however, it will not pick up the wireless networks which I know are in range.  Any suggestions?

Thanks!
Chris

---

### Post by Metaljaz on 2007-03-07
what chipset does the card have? Did you install the right drivers for the chipset?

Post the results of lspci

Any WEP or WPA?

---

### Post by Mr. C. on 2007-03-07
Be sure any test that any speed-boast proprietary settings aren't affecting the ability to associate.

MrC

---

### Post by Shadow503 on 2007-03-10
I have that wireless card. Run these commands (from a root terminal) and then reboot your computer:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules

---

### Post by fleshberkowski on 2007-03-16
shadow,

i've gotten to a similar point where i'm supposed to type in: echo ndiswrapper >> /etc/modules

but it gives me the message: bash: /etc/modules Permission Denied

any reason why you think it would do that?

---

### Post by Mr. C. on 2007-03-16
The previous recommendation should have stated:

```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```

MrC

---

### Post by fleshberkowski on 2007-03-16
i'm still getting the same permission denial error. also, i tried installing the card using this guide: 

n terminal:
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8

mkdir linksys
cd linksys
wget [ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip)
unzip wpc54g_v2_driver_utility_v2.0.zip

At this point you have the software you need to install your driver

Now a little housekeeping to ensure you don't any future problems, we are going to convert the following filename to all CAPS this ensures your driver recognizes the file
mv tnet1130.sys TNET1130.sys

Now we are going to install the drivers
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper

Now we are going to set up your system to initialize on boot-up
sudo nano /etc/modules

add the following line at the end of the file
ndiswrapper
then ctrl-x
y
enter
Now insert your card and enter
ndiswrapper -l

the screen should read:
Installed drivers:
lsbcmnds driver installed
lstinds driver installed, hardware present
Disable your wired network connectio
Now run dmesg and look for the following lines:
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.1 loaded
ndiswrapper: using irq <irq#>
wlan0: vendor: 'TNET1130'
wlan0: ethernet device 00:0f:66:d8:a7:88 using NDIS driver lstinds, 104C:9066:1737:0033.5.conf

Now restart networking with the following command:
sudo /etc/init.d/networking restart



***** 

and when i get to the point where it should say" lstinds driver installed, hardware present" i get "invalid driver, invalid driver" and no acknowledgment of the hardware. 

i have v3.1 of the wpc54g card and substituted the 3.1 drivers in the above instructions.

---

### Post by MeeMaw on 2007-03-16
> **fleshberkowski said:**
> 
********
and when i get to the point where it should say" lstinds driver installed, hardware present" i get "invalid driver, invalid driver" and no acknowledgment of the hardware. 

i have v3.1 of the wpc54g card and substituted the 3.1 drivers in the above instructions.

But are you sure those are the right drivers for your card?  Linksys uses a bunch of different chipsets and drivers -----  what do you get when you do 

sudo lspci

Please post your results......  (someone else requested that, I think.... the output of that command would really help us help you.)   Thanks

---

### Post by fleshberkowski on 2007-03-17
ok, i ran sudo lspci and this what it spit out:
> 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
(rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

and then when i tried lspci -v, this is what i got:
> 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
Flags: bus master, medium devsel, latency 32
Memory at f4000000 (32-bit, prefetchable) [size=64M]
Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 32
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fd000000-feffffff
Prefetchable memory behind bridge: f8000000-fbffffff

00:03.0 CardBus bridge: Texas Instruments PCI1420
Subsystem: Dell Latitude C600
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at 28000000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
Memory window 0: 20000000-21fff000 (prefetchable)
Memory window 1: 22000000-23fff000
I/O window 0: 00001000-000010ff
I/O window 1: 00001400-000014ff
16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1420
Subsystem: Dell Latitude C600
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at 28001000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
Memory window 0: 24000000-25fff000 (prefetchable)
Memory window 1: 26000000-27fff000
I/O window 0: 00001800-000018ff
I/O window 1: 00001c00-00001cff
16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
Flags: bus master, medium devsel, latency 32
I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
Flags: bus master, medium devsel, latency 32, IRQ 11
I/O ports at dce0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
Subsystem: Dell Latitude C600
Flags: bus master, medium devsel, latency 32, IRQ 5
I/O ports at d800 [size=256]
Memory at f3ffe000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>

00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
Subsystem: 3Com Corporation Unknown device 6456
Flags: bus master, medium devsel, latency 32, IRQ 11
I/O ports at d400 [size=256]
Memory at f3ffdc00 (32-bit, non-prefetchable) [size=128]
Memory at f3ffd800 (32-bit, non-prefetchable) [size=128]
Expansion ROM at fc000000 [disabled] [size=128K]
Capabilities: <access denied>

00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
Subsystem: 3Com Corporation Unknown device 615b
Flags: bus master, medium devsel, latency 32, IRQ 11
I/O ports at d000 [size=256]
Memory at f3ffd400 (32-bit, non-prefetchable) [size=256]
Memory at f3ffd000 (32-bit, non-prefetchable) [size=128]
Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
Subsystem: Dell Latitude C600
Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Memory at f8000000 (32-bit, prefetchable) [size=64M]
I/O ports at ec00 [size=256]
Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
[virtual] Expansion ROM at fd000000 [disabled] [size=128K]
Capabilities: <access denied>

06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Subsystem: Linksys Unknown device 0048
Flags: fast devsel, IRQ 11
Memory at 26000000 (32-bit, non-prefetchable) [disabled] [size=8K]


---

### Post by MeeMaw on 2007-03-17
fleshberkowski you have another post re: this same thing and chili555 is VERY knowledgeable. Go back to that thread...........I'm sure chili555 can help you.

NjRef511 - have you solved your problem yet?

---

