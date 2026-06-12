---
title: "Cannot configure dhcp network"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by RFXCasey on 2008-11-03
I have an Acer Veriton 7100 I got from a friend and wanted to install Linux. No matter what disto I try to install, when I get to the configuring network part it tell me it failed to configure the DHCP network properly. At first I was using the on board Integrated Intel 82801BA 10/100 adapter. After several failed attempts I disabled the on board nic on the mobo and install a Linksys pci nic and had no success with that either. Re-enabling the onboard and installing again with the pci nic also installed, linux gives me the option to choose either one before it tries to configure the network. Choosing either network device the result is the same. I tried a couple of times hooked up to the router and thought this might be the problem so now I have my machine hooked directly up to my cable modem while installing the os. I have only gotten the network to configure properly once with the Linksys card using Kubuntu 8.10 but I didn't like the desktop manager so I tried to install Ubuntu with out success. I tried to reinstall Kubuntu and now that doesn't work either. The only thing I had done different is the that the first (and only) successful install was done without the pci nic card or my AGP graphics card installed. The network works fine on my main machine so I don't think it has anything to do with my network.I have tried pinging other machines on the network as well as web sites with both net devices and neither work. When I try installing using ubuntu the install goes fine but the machine will never get an ip address? And before anyone asks yes my router is set for dhcp, even hooked to the cable modem directly it cannot configure.

---

### Post by RFXCasey on 2008-11-04
I figured it out. I had to use the alternate install cd and add "acpi=off noacpi" to the boot options. I guess this type of old machine has a screwy bios that can't handle Linux.Since there are no more updates available for the bios I had to turn off the acpi in the kernel. It now sets up the network perfectly during install.

---

### Post by RFXCasey on 2008-11-04
After further experimentation I have found that I only have to use the option 'acpi=noirq' which only diables the PCI IRQ routing. :guitar:

---

