---
title: "USB to LAN adaptor"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Riis on 2007-09-17
I am looking for an USB to LAN adaptor.
But it ***needs*** to be working under the 2.4 kernel.

Anyone that knows about such adapters that would work?

---

### Post by lisati on 2007-09-17
Do you mean something similar to the device at [http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8273](http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8273)
???
(I don't know if the example will work)

I do possess [http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8177](http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8177) but haven't tried it with Ubuntu yet.

---

### Post by Riis on 2007-09-17
> **lisati said:**
> Do you mean something similar to the device at [http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8273](http://www.dse.co.nz/cgi-bin/dse.storefront/46ee26d900189f2a273fc0a87f3306b4/Product/View/XH8273)
???Something like that yes.
I need a extra LAN-port in my computer.

---

### Post by ddrichardson on 2007-09-17
I can see problems with a device like that under Ubuntu. If you need another ethernet port, why not a second NIC (they're like £10) or a cheap hub?

---

### Post by coffeecat on 2007-09-17
I bought a usb to ethernet adaptor for an old laptop without an ethernet port, and it worked fine with Dapper, but that was with the 2.6 kernel. I believe most, if not all, usb/ethernet adaptors will work with the 2.6 kernel, but the OP wants to use it with the 2.4 kernel. That's getting on a bit now. It might simply not have the drivers. I don't know.

**Riis**, why the 2.4 kernel? And can you say more about your hardware? Desktop or laptop? If a laptop, you can get pcmcia ethernet cards but, personally, I'd be cautious about any usb, pci or pcmcia adapter with the 2.4 kernel.

---

### Post by Riis on 2007-09-17
For various reasons, it needs to be an USB device and it needs to be kernel 2.4 (the computer is currently running kernel 2.4 and I cannot upgrade it).

So from what you are saying, the only option I have (if I want to use an USB->LAN adaptor) is to upgrade to kernel 2.6?

---

### Post by spd106 on 2007-09-17
If you can find a USB-LAN adaptor that is supported by the [Pegasus]("http://sourceforge.net/projects/pegasus2/") driver then you should be ok.

I have a Belkin F5D5050 that works on DSL 2.1, which has a 2.4.31 kernel. I'm not sure how new the USB system is though. Don't expect any kind of performance, I'm lucky to get 700Kb/s even though it's rated as a 10/100 Mbps device.

---

### Post by Riis on 2007-09-17
Will the performance increase if kernel 2.6 is used?

---

### Post by spd106 on 2007-09-17
I booted into my Dapper install and tried it out. The weird thing is that it's actually slower (~200Kbps) than on DSL. There's a post on the Fedora forum saying the same thing [http://forums.fedoraforum.org/forum/showthread.php?t=102830](http://forums.fedoraforum.org/forum/showthread.php?t=102830)

I've no idea where the problem lies, but it looks like the adaptor keeps pausing during transmission. The processor load as measured in top is almost negligible.

---

