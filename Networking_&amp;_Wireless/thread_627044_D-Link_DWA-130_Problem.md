---
title: "D-Link DWA-130 Problem"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by billswild00 on 2007-11-29
I have been following the steps to install a usb wireless adapter here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27)

I can get the driver to associate correctly but I cannot do anything else from there.  I am using the Windows XP driver that I downloaded from the D-Link website.  I have already compiled the latest version of ndiswrapper.  However, I am all out of ideas.  Thank you for the help in advance.

---

### Post by gramgram on 2008-02-27
Yeah, I have same problem. I even tried the Ralink drivers from another card (installed through ndiswrapper), but no luck. I can get it to scan, but not connect. If you hear anything or solve anything I'd appreciate a heads up. I will do the same for you.

---

### Post by zidkenu on 2008-05-18
This tutorial is proven in Ubuntu 7.04 Feisty. 
Go to...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Scoll down and see "2.2. Installing Packages (With Internet access on another computer)"
Download the following deb files, put them together with the adapter inf file(from adapter CD) on a usb drive, 
Plug the adapter in, start the computer with Ubuntu in LiveCD mode.
After booting up, go to 
MainMenu-> Accessories -> Terminal, install the deb files in this order: 

  sudo dpkg -i ndiswrapper-common_*.deb

  sudo dpkg -i ndiswrapper-utils*.deb

  sudo dpkg -i --force-depends ndisgtk_*.deb

#Note: Ubuntu don&#8217;t suggest su



Installing Windows driver by using ndisgtk: Go to MainMenu -> System  -> Administration -> Windows wireless drivers

Click on "install new driver" -> select the adapter inf file in the usb drive.

Then even it shows: "Hardware present: No", ignore it.

Go to ConfigureNetwork, click on WirelessConnection, click on Properties, untick EnableRoamingMode, choose NetworkName and WEP key Hex,

enter the password, use DHCP, leave the rest blank.

then see if the device is flashing, if not, unplug then plug it in again...
if still not working, restart the computer and do it again ...

when seeing flashing, then check the internet... yeah, we're in!!!

#Note: even after all of the above and after installing Ubuntu on my hard drive, and after many many successful internet connection, sometimes(only occasionally, so it is ok), it still won't work. (especially if the device won't flash during boot or the boot process freezes...)
 
In that case, just unplug the device, then restart the computer, after the boot menu, plug in the device again(for re-detection), it will work this way always =)

---

