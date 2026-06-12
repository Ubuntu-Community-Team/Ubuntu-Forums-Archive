---
title: "wireless card probs once more"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by ankscorek on 2008-02-29
im using ubuntu-7.10 and kubuntu-7.10...

im using hp pavillion dv6000 with vista

probs with broadcom which so many have and the problem has been addressed in forums

i used the restricted drivers to download the driver for broadcom wireless from the repositories

but im unable to use the wireless card

so i downloaded ndiswrapper 

then i blacklisted bcm43xx

and installed bcmw4l6.inf which was available with windows vista on my laptop

no success

steps done

blacklisted bcmw43xx in /etc/modprobe.d/blacklist
ndiswrapper -i bcm4l6.inf
modprobe ndiswrapper


reboot

im unable to still use it

pl help

---

### Post by alan34 on 2008-02-29
Hi I do not have a broadcom card but this might save you some wasted time.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Quote
Install Windows driver

Important: Not all Windows drivers are tested / stable. If the Windows driver that you use is problematic, try alternate Windows drivers that others have tested, especially those in List. Always, try Windows XP drivers and if Windows XP drivers are not available, try Windows 2000/2003 drivers. Windows Vista drivers are not supported (yet) - using Windows Vista driver will result in many &#8216;unknown symbol&#8217; error messages when loading ndiswrapper. 

It says that Vista drivers are not supported yet in ndiswrapper. I would go to to the HP website
and download the XP drivers or see if they are on your cd? You need something.inf and something.sys.

Go System - Administration - Synaptic Package Manager and search for ndisgtk install and it will be in your System - Administration menu. Try using that it is a GUI for ndiswrapper.

Good luck

---

### Post by ankscorek on 2008-02-29
hmm i did one amendment after removing the bcm43xx module i took a reboot and then did a fresh installation of a windowsXP driver found on net....

since i have no wireless nw around me im unable to check

however few basics tests gave me

#iwconfig wlan0 down
#iwconfig wlan0 up

earlier the OS refused to start the wlan0 interface...any further tests pl suggested may be written here so that i can post the output

here is output of dmesg

[   39.947438] ndiswrapper version 1.45 loaded (smp=yes)
[   40.047834] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   40.049769] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   40.050415] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   40.050426] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   40.050462] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   40.058599] ndiswrapper: using IRQ 19
[   40.414998] wlan0: ethernet device 00:1a:73:60:f0:41 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4312.5.conf
[   40.415034] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


i guess it is working properly

my mobile is wifi enabled how do i connect it to my laptop via wifi

i have no wifi routers

just wifi enabled laptop and mobile phone

---

