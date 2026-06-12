---
title: "RT2500 offline install?"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Forlornity on 2006-12-03
Hey there, I'm trying to install the Rlink RT2500 driver and config util on my Xubuntu Edgy system, which is not connected to the internet (hence wanting to install wireless) and I'm having trouble with the dependencies it requires, is there any way I can get the required packages from this ubuntu edgy computer and copy them onto my usb-stick to use on the xubuntu machine.
I'm attempting to use this guide to do it: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#InstallRutilT](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#InstallRutilT), but of course I need to be online for this one (my card is an Edimax EW7128g).

Thanks, Forlornity

---

### Post by FrodoB on 2006-12-03
I could be mistaken, but the rt2500 driver is included in the Ubuntu Edgy release. Did you use an Alternate CD perchance?

The device does not just show up in the output of iwconfig?

Publish the outputs of:

lspci or lsusb which ever is applicable

---

### Post by Forlornity on 2006-12-03
Xubuntu Edgy installed via Alternate install, 
iwconfig returns this:
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

lspci returns this:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:10.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:14.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

It shows up but does absolutely nothing, it just won't even try to connect to a network.

thanks, Forlornity

---

### Post by FrodoB on 2006-12-03
Did you install using the Alternate CD? If so then:

1) Have the install CD ready for use.

2) Open a terminal command prompt and type the following:

sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

Publish your outputs again after the reboot.

If that does not help, then search the forum for "rt61".

There are a lot of threads on it and surely someone as solved it.

---

### Post by Forlornity on 2006-12-03
I already have the restricted modules installed it seems...?

---

### Post by FrodoB on 2006-12-03
Alright, then take a look at the rt61 posts and see it they help. These are common devices and I suspect that the solution involves blacklisting the existing driver and installing the latest one from 

Ralink:
[http://www.ralink.com.tw/supp-1.htm](http://www.ralink.com.tw/supp-1.htm)

or the Community rt25xx Project:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

There are pretty active forums at both sites as well as many posts on the Ubuntu forums, so you will be able to figure it out.


Oh, and you might want to retitle this post to include the rt61 name as that is the variant that you actually have.

---

