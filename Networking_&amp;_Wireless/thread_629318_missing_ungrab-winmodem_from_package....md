---
title: "missing ungrab-winmodem from package..."
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Akash.Yak on 2007-12-02
Hey people note ..

ungrab-winmodem.ko, that is essential in the process of setting up a PCI modem driver, is missing in the package in which it must be found.

The package is slamr-2.6.22-14-generic.tar.gz, found on [http://linmodems.technion.ac.il/packages/Smartlink/Ubuntu](http://linmodems.technion.ac.il/packages/Smartlink/Ubuntu). Sasha Khapyorsky is the author of this driver for this HSP56 micromodem 688T of Oasis chipset.

Upon gunzipping and tarring, a folder results, that has a setup script, in which there is a line as follows:

                 modprobe ungrab-winmodem

but unfortunately, there is no ungrab-winmodem in that folder. The script thus fails to install the driver on my Edubuntu 7.10. 

Somebody bring it to his notice.

---

