---
title: "Amtel  wlan driver help"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by majkmil on 2005-11-14
Hi,  I am trting to get my linksys usb adapter working. I downloaded this driver (atmelwlandriver). I have learned alot from the forums and google but I am not sure about the kernel and sources for the kernel. Could someone please read this and help me with this section in the read me file that came with the driver. I think UBUNTU is built on the linux 2.6 kernel but I am not even sure about this. The directions say I need the kernel sources and put them in the right place. I do not know how to do this. Please Help,   Mark




STEP I: Kernel compilation
--------------------------------------------------------------------------------
NOTICE: Sometimes, you may not have to build your kernel manually. This happens
when you are so lucky that your precompiled kernel which your distribution uses
fullfills all the requirements mentioned below. However, in any case you still
have to obtain the kernel sources that correspond to your running kernel, and
put them in the right place.
To configure your kernel build options, in the kernel source directory
(most probably /usr/src/linux-2.x.x), do a `make menuconfig` under console
or `make xconfig' under X environment. (If no such dir exists, this means that
you have no kernel sources, and you have to install them)
The following parameters must be configured, in order for the driver to work:
- Loadable Module Support -> Enable (Module unloading is also recommended)
- Processor types and features -> Symmetric Multiprocessing Support - Disabled
- Device Drivers -> Networking Support -> Wireless LAN (non-hamradio)
        No further specific drivers need to be selected there.
- (PCMCIA only) Bus Options -> PCMCIA/CardBus support -> yenta-compatible.
        Select this only if you prefer to use internal card services
	Otherwise, When you build the external package pcmcia_cs,select i82365.
	You may have to edit /etc/sysconfig/pcmcia, filling the `PCIC=' field,
	with `i82365' or `yenta_socket', according to your selection.
- (USB only) The appropriate host controller interface has to be selected. 
	If unsure, select both ehci, ohci and alternate-uhci and you'll 
	later determine which one is actually used.
- (USB for 2.5 and 2.6) In order to make the driver work for 2.6 kernels,
	you have to download and install the reset-usb kernel patch.
	To make things easier, we provide a link to download the patch from 
	(atmelwlandriver.sourceforge.net/downloads.html).
	Gzip -d it, Copy the ungzipped file to /usr/src/linux-2.6.x and run:
	#patch -bf -p1 < patch_atmel_reset
	This keeps backups of the updated files, in case something goes wrong.
	After the patch has been applied, rebuild your kernel.

To find out if your kernel (custom or not) has these parameters configured as 
required, view the file /usr/src/<Your Running Kernel>/.config and check if the
following lines are the same. 
(they wont be found together, you have to search for each one of them)

CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y 		# recommended
# CONFIG_SMP is not set
CONFIG_NET_RADIO=y		# to enable wireless extensions
CONFIG_NET_WIRELESS=y

CONFIG_PCMCIA=m			# mandatory for pcmcia
CONFIG_YENTA=m			# if not using external cs
CONFIG_CARDBUS=m

CONFIG_USB=y			# mandatory for usb
CONFIG_USB_EHCI_HCD=m		# `=m' to all 3 HCI's is the least risky option
CONFIG_USB_OHCI_HCD=m		# therefore `=y' is not recommended.
CONFIG_USB_UHCI_UHCI_ALT=m	# you only need to select the one that suits you
				# but selecting all of them won't do any harm
				

WARNING: There are serious conflicts when our driver tries to cooperate with 
usb-uhci, that can lead to a crash. Using uhci (instead of usb-uhci)
is higly recommended. So, if your system starts with usb-uhci loaded 
(you can see this with lsmod), rmmod it and manually load uhci.o (or uhci-hcd.ko
for 2.5+ kernels). In kernel Configuration, select as module only the alternate
UHCI driver if your bus is of that type.


Some further info for linux newbies:
After having finished with kernel tweaking, do `make bzImage', `make modules'
and `make modules_install'.
(For 2.4.x kernels, `make dep' must be run after exiting `make config')
The kernel image shall reside in ./arch/i386/boot/bzImage and should be copied
to /boot directory. For GRUB, just adding a section (in /boot/grub/menu.lst)
containing the new kernel image, is enough to activate the newly compiled kernel
and to be able to load it when booting.

---

### Post by Lambert on 2005-11-14
I don't believe you have to do all this as you are running a 2.6.12 kernel. From a terminal you can run [COLOR=DarkRed]uname -r[/COLOR] and it will tell you the kernel you're running.

I show the atmel driver supported in this kernel.

Have you tried to just plug in the device, go to system>admin>networking

You should see your device in the list.

With the device plugged in, from the terminal run these commands.

```
ifconfig
and
iwconfig
```

---

### Post by majkmil on 2005-11-14
thanks, This is what I get under iwconfig.

  IEEE 802.11-DS  ESSID:"okuwlan"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:D

---

### Post by majkmil on 2005-11-17
[QUOTE=Lambert]I don't believe you have to do all this as you are running a 2.6.12 kernel. From a terminal you can run [COLOR=DarkRed]uname -r[/COLOR] and it will tell you the kernel you're running.

I show the atmel driver supported in this kernel.

Have you tried to just plug in the device, go to system>admin>networking

You should see your device in the list.

With the device plugged in, from the terminal run these commands.

```
ifconfig
and
iwconfig
```[/QUOTE]

Where do you find that the atmel driver is supported in thi kernel?
Does this make this device plug and play?

---

### Post by Urusai on 2005-11-17
I had to use the atmelwlandriver for my Netgear MA101.  I untarred the source to /usr/src/atmel and ran make (it shows you the compile options when you run it).  Don't bother with lvnet or winter.   After you compile and install, you have to run something like "iwconfig atml0" then "ifconfig atml0", I think it was.  There's more to it, but I was running it in Gentoo and with Gentoo discovering these things yourself is the fun of it.

There's another driver at berlios.de, I forget the name, it is probably a better driver since the atmelwlandriver at sourceforge seems frozen (I had to change the source myself to make it work with later Linux versions).  I think my diff is in the sourceforge forum.  The berlios.de driver seems a little less funky.

---

### Post by Lambert on 2005-11-17
[quote=majkmil]Where do you find that the atmel driver is supported in thi kernel?
Does this make this device plug and play?[/quote] 
/lib/modules/2.6.12-9-386/kernel/drivers/usb/net/atmel/at76c503-i3861.ko


When you ran iwconfig and the device showed up then that tells me that a driver is loaded and identifying this as a wireless device.

command [COLOR=Sienna]sudo lshw -C bus [/COLOR]will list the device. Look for the section showing the device and then the line configuration: this will tell you what driver is being used.

My pci card shows up like this. (it's an atheros chipset)
*-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       logical name: ath0
       version: 01
       serial: 00:11:95:50:be:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.0.150 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:10800000-1080ffff irq:11

have you tried going into System>admin>network and entering your network info and activating? Are you using wep or wpa encryption?

What's output of 

sudo iwlist <device> scan

---

### Post by majkmil on 2005-11-17
I am pretty sure that the driver at76c503 is native to breezy. I aws trying everything that I could find. All I did was plug it in and it was recognized in the network. Then all I did was configure, ie. essid and I used a static ip. Good to go. This is where the Belios driver is ([http://at76c503a.berlios.de/)](http://at76c503a.berlios.de/)). It says in the read me file that it supports you card too (Netgear MA101B). Thats all I know. Do you have it running in ubuntu?

---

