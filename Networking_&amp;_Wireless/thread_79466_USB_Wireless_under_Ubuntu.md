---
title: "USB Wireless under Ubuntu"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by tmattoneill on 2005-10-20
So I have had an ongoing issue trying to get my Linksys Wireless USB 54g (wusb54g) network adapter under Linux for over a year.  I had Mandrake 10.x then moved to Mandriva 2006.  Neither of those worked.  Then I read the glowing reviews and liked what I saw with ubuntu.  I've removed Mandriva and replaced it with ubuntu.

I *still* have no access to my network connection.  If someone can please help I will be most appreciative.  I fail to understand why it's so hard to simply get this to work.  I've also tried with my PCI Belkin 54g wireless networking card, but that doesn't work either.

The *only* device I see as active under my networking settings is eth0, the Intel ethernet card.  I don't have anything connected to that as my whole system is wireless.

I've tried ndiswrapper and it says there is no valid configuration, I've got my windows drivers and everything.  I simply can not get the system to say "I see a USB wireless internet adapter, would you like to configure it?"  It recognizes the USB ports themselves, but not the devices on them.  I get it to see the Belkin PCI card but have no way of configuring it or setting the WEP key or broadcasting to the network point.

Can some please post clear, concise instructions on how to get either a wireless PCI card -or- a wireless USB adapter working under ubuntu?  I have yet to find one simple, explanation.

Thank so much!

Matt ONeill
[email]matt@mattstard.com[/email]

---

### Post by spd106 on 2005-10-21
I am surprised that you've had no luck with the pci card, even with ndiswrapper. Have a look at [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards").

For the usb device you will need to correctly identify which version you have. ie **lsusb ** and match it on this [page]("http://www.qbik.ch/usb/devices/search_res.php?pattern=wusb54g").

Good luck

---

