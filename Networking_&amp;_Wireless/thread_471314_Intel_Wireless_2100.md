---
title: "Intel Wireless 2100"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by BitKeeper on 2007-06-11
I have a Toshiba with a 
> 02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

The install of Ubuntu 7.04 went fine and my wired connection is working. But I am not getting a second eth device for my wireless card.

ifconfig -a gives me eth0 (wired network card) and lo.
iwconfig shows up no wireless extensions.

The ipw2100 module is being loaded.

I am using kernel 2.6.20-16-generic

Any ideas on what is happening?

Thanks.

More Info:

> 
[   18.196000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.2
[   18.196000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.196000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.200000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   18.300000] ipw2100: eth1: Error initializing Symbol
[   18.300000] ipw2100: eth1: Error loading microcode: -5
[   18.300000] ipw2100: eth1: Failed to power on the adapter.
[   18.300000] ipw2100: eth1: Failed to start the firmware.
[   18.300000] ipw2100Error calling register_netdev.
[   18.300000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[   18.300000] ipw2100: probe of 0000:02:05.0 failed with error -5


---

### Post by BitKeeper on 2007-06-24
Still not having any luck with this wireless card.

From all that i have read it should be working out of the box. I dont even get a eth device.


> [   18.500000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   18.500000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.500000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (level, l
ow) -> IRQ 11
[   18.500000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   18.648000] pnp: Device 00:0b activated.
[   18.648000] parport: PnPBIOS parport detected.
[   18.648000] pnp: Device 00:0b disabled.
[   18.720000] nvidia: module license 'NVIDIA' taints kernel.
[   19.144000] ipw2100Error calling register_netdev.
[   19.144000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[   19.144000] ipw2100: probe of 0000:02:05.0 failed with error -5

Some more info.

---

### Post by houms on 2007-07-05
does Network Manager show wireless options? I have an intel 2100 and got it working, what is your setup in terms of wireless settings. broadcasting ssid, any encryption, etc?
It would help if you post 

ifconfig & iwconfig

If ya still need help let me know!!!

---

### Post by BitKeeper on 2007-07-05
Thanks for the reply.

ifconfig and iwconfig don't give any useful info as the eth1 device that should be the wireless card is never created as the whole process fails very early on.

ifconfig only shows my wired device (eth0) and lo.

iwconfig finds no wireless extensions.

There are no wireless options in Network manager.

---

### Post by houms on 2007-07-05
Anytime, here to help and learn
try
sudo ifup eth1
then see if eth1 shows up... it sounds like your wireless card may be off try fn+Fx, to toggle between off and on. (x being one of the F function keys, on dell laptop its fn+F2, it may be different on Toshiba.... but make sure your wireless card is on, 
What does your /etc/network/interfaces file look like
also try lspci and post here or see if your intel card is listed
you can always go to intel's site and dl the  linux driver, but it should already be installed,
did you install from live cd? if so, boot from that and see if your card is detected. this is an internal card right?

---

### Post by BitKeeper on 2007-07-05
/etc/network/interfaces

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp




---

### Post by houms on 2007-07-05
Anytime, here to help and learn
try
sudo ifup eth1
then see if eth1 shows up... it sounds like your wireless card may be off try fn+Fx, to toggle between off and on. (x being one of the F function keys, on dell laptop its fn+F2, it may be different on Toshiba.... but make sure your wireless card is on,
also try lspci and post here or see if your intel card is listed
you can always go to intel's site and dl the linux driver, but it should already be installed,
did you install from live cd? if so, boot from that and see if your card is detected. this is an internal card right?

---

### Post by BitKeeper on 2007-07-05
Hi again,

> 
$ sudo ifup eth1
eth1: ERROR while getting interface flags: No such device

I have tried the function keys, no joy.

> 
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
**02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)**
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)



Yes i did install from the live cd and no wireless didn't work from there.

Thanks for the help.

---

### Post by houms on 2007-07-05
if you right click on the network manager, is there an enable wireless listed? 
Also check your bios and make sure there is not an acpi setting  or PnPOS settingthat is disabling the card during boot, Thinkin maybe something with ACPI and ubuntu is a little flaky... 
Stupid question but you did verify that the wireless card works.. If your not sure, Try another livecd distro like fedora, or Knoppix would be good for something like this...

---

### Post by BitKeeper on 2007-07-05
hi,

No there is no enable wireless option when right clicking on network manager.

The wireless card works under windows, but i am as yet to get it to work under any linux distro. I have tryed Knoppix OpenSUSE Gentoo. 

As far as i can find i cant get into the bios on this laptop. the usual del, f2, keys dont work and f12 just gives me a boot device option.

---

### Post by houms on 2007-07-06
That's strange, you have never accessed the BIOS? what kind of laptop, toshiba what?
try these commands 
Toshiba® 335 CDS  	                      ESC
Toshiba Protege 	                          ESC
Toshiba Satellite 205CDS	           F1
Toshiba Tecra 	F1 o#F1EFA5r           ESC

for Toshiba Notebook [Newer models]
	

1. Turn on computer by Holding down power button while pressing the ESC key.
The machine will beep, then display:
Check System, then press [F1] key.
2. Release ESC key
3. Press F1 key

See if any of these work, damn you used knoppix and it did not detect your intel card.... there is definitely something wrong here... try accessing the BIOS, lets confirm its not the cause of this

Also did you 
sudo modprobe ipw2100, to make sure the module is loading?
I really feel like the BIOS or the wireless card being turned off is the problem... I mean its rare that Knoppix doesnt detect a wireless card as common as ipw2100....

---

### Post by BitKeeper on 2007-07-08
Hi,

I got into the bios there doesn't seam to be any options involving the wireless card. PCI NIC = Enabled was the only networking setting i could find.

Both knoppix and ubuntu see that the device is there and try to load the ipw2100 module but it fails with a  Error initializing Symbol.

From my first post  

> 
[ 18.196000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.2
[ 18.196000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[ 18.196000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[B][ 18.200000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[ 18.300000] ipw2100: eth1: Error initializing Symbol
[ 18.300000] ipw2100: eth1: Error loading microcode: -5
[ 18.300000] ipw2100: eth1: Failed to power on the adapter.
[ 18.300000] ipw2100: eth1: Failed to start the firmware.
[ 18.300000] ipw2100Error calling register_netdev.
[ 18.300000] ipw2100: probe of 0000:02:05.0 failed with error -5[/B]


Thanks

---

### Post by der_vegi on 2008-03-09
I have the same problem on an Ibm machine with the ipw2100 card. It used to work fine, but one day I pressed the Fn-key to disable the wireless. Now, a couple of weeks later, I try to reactivate it, but it doesn't work. Ubuntu recognizes the card, but I also get the "ipw2100: probe of 0000:02:05.0 failed with error -5" error. 'modprobe -r ipw2100' and then reloading the module results in the same error. Pressing the Fn-key kombination again, does not work, either. The Bios setting for the card is 'enabled'.
Anyone any idea? In some forum I once read, that sometimes a Windows driver (okay, which I do not have installed) leaves a wireless card in a stat, that it cannot be used in Linux anymore...

Thanks for the help!

---

### Post by der_vegi on 2008-03-09
Okay, works now after reinstalling the linux-image package... But strange, anyhow.

---

