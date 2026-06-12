---
title: "RT2561/RT61 Problems"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by omax on 2008-08-09
Hi,

I recently bought a Cnet CWP-854 Wireless PCI Adapter. It worked perfect out of the box in Hardy 8.04 2.6.24-19-generic with the rt2x00pci kernel module (I believe)

Though after a couple of hours of the network card running the computer freezed and I had to hard reboot. There seemed to be a problem with the module.

I downloaded the latest driver from Ralinks website: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) (RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)

It builds fine but I can't get the networking to work.
Interface ra0 exists and I can scan for AP's. Though on every AP it finds Bit Rates are 0Kb/s and nothing more.

I need some help with this, since it is a bit over my head. Can I just delete every kernelmodule that has to do with the network card and /etc/Wireless/RT61STA/* to start over?

Is there any updated detailed instructions for Hardy and the RT2561?

---

### Post by omax on 2008-08-09
Update: Currently the card works with rt61 kernel module.

I had to make KBUILD_NOPEDANTIC=1 in order to make it compile. It gave me tons of warnings but it seem's to work anyway. I shall see if it freezes the computer. To be updated

---

