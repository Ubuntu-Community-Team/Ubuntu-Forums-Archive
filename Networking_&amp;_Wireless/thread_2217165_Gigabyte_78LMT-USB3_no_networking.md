---
title: "Gigabyte 78LMT-USB3 no networking"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by Kevin_Neureuter on 2014-04-15
Hi all,

I am fairly newish to the underworkings of Linux, but have a minecraft server running on Linux Server 12.04.  I recently changed the motherboard to the Gigabyte 78LMT-USB3 (without checking for Linux compatibility) and upgraded my RAM to 12GB and the CPU to Athlon II X4 635.  When the OS boots it can't start the network configuration, and says that it is not supported in this system when I try and get into network settings.

I've tried a USB ethernet dongle, and a discrete PCI network card, neither of which gave me network capabilities.  Do I have to enable them somewhere in terminal in order for it to recognize them?

Is there a way to get network access on this motherboard, or do I need to RMA it to Newegg and get a different one?

P.S. [http://www.linux-hardware-guide.com/2013-11-01-gigabyte-ga-78lmt-usb3-sockel-am3-atx-amd-phenomathlon-4x-ddr3-6x-sata-ii-4x-usb-3-0](http://www.linux-hardware-guide.com/2013-11-01-gigabyte-ga-78lmt-usb3-sockel-am3-atx-amd-phenomathlon-4x-ddr3-6x-sata-ii-4x-usb-3-0)  says the board works out of the box with Linux.

Please help.

-AxE

---

### Post by chili555 on 2014-04-17
Is this a true server running without a desktop environment or is Network Manager running? Please open a terminal and run and post:```
sudo lshw -C network
ifconfig
cat /etc/network/interfaces
```Thanks.

---

### Post by Kevin_Neureuter on 2014-04-24
Hi Chili, 

Sorry for the late reply.  I got it working, and it had to do with Network Manager. 

I ended up following a guide on here to fix the driver issue and set it back from the faulty R8169 Realtek driver to the R8168 driver, doing so changed the interface from eth0 to eth1, which I didn't realize until later.  That still didn't allow my network to connect.  I then saw somewhere that someone disabled Network Manager and they were able to manually connect.  I did that, discovered that eth0 was renamed to eth1, and edited the text document that contains the Network information to reflect that, and it worked for a day or so, then the network connectivity went away again.  I re-enabled the Network Manager, and this time it worked.  Been working since.

---

### Post by chili555 on 2014-04-24
Glad it's working by whatever means!

---

