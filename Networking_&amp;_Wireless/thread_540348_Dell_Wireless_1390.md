---
title: "Dell Wireless 1390"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by markk1994 on 2007-09-01
How would  I be able to install this card "Dell WIreless 1390"?

---

### Post by rollerskatejamms on 2007-09-01
sudo apt-get install bcm43xx-fwcutter
reboot

---

### Post by delibercogito on 2007-09-03
I've been trying for over 12 total hours to get a Broadcom Corporation Dell 1390 WLAN Mini PCI Card working.  I've tried every HowTo on the entire internet.  I even went so far as to make every different attempt on a completely fresh install to avoid leftover complications.  I am happy to say, that it now works. 

Now, WHY it works, makes little sense.  But it does.  This is on an Acer Aspire 5570-2052.  This is with a completely clean install from a Ubuntu 7.04 LiveCD.  Completely clean meaning I DID NOT DO ANY UPDATES.  I am sure that based on previous issues, UPDATES WILL BREAK THIS.

YOU MUST HAVE A USB WIRELESS ADAPTER FOR THIS TO WORK.

Skip the following UNLESS you are using an Acer that is listed as compatible here: [http://code.google.com/p/aceracpi/wiki/SupportedHardware](http://code.google.com/p/aceracpi/wiki/SupportedHardware) 

Go to:
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

Download acer_acpi-0.8.1.tar.bz2
Extract it.

Open a terminal and navigate to the acer_acpi-0.8.1 directory.
make
sudo make install

Follow this guide: [http://ubuntuforums.org/showthread.php?t=224349](http://ubuntuforums.org/showthread.php?t=224349) starting at Load the acer_acpi into memory and activate the wireless:

Note the typo in the original post at:


Code:

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

should be

Code:

ls /etc/rcS.d/S39acer_acpi_wireless_enable
ls /etc/rc0.d/S34acer_acpi_wireless_enable
ls /etc/rc6.d/S34acer_acpi_wireless_enable

Finish the guide and reboot.

Go to [http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/)

Download and install 	bcm43xx-firmware_1.3-1ubuntu2_all.deb

reboot.

You'll notice that network manager will still not list any networks.

Plug in a USB Wireless Adapter. I used a Linksys WUSB54GC.  Wait for a second.  Click on Network Manager again.  It should now list both wireless devices.  Unplug the USB adapter.  Your onboard wireless should still list networks at this point.  Make sure you can connect to one.  Reboot.

[I plugged in the Linksys adapter because I'd given up on getting the onboard to work and figured I'd just try the USB adapter.  Imagine my suprise (and cursing) when suddenly, the onboard worked.]

---

