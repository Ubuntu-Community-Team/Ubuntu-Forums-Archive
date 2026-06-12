---
title: "wireless card"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by mcolwell on 2006-09-06
Just installed Ubuntu on a new Dell D620 laptop the wireless card however seems to have not been recognized. I checked lspci and lshw and it didn't show the card. I don't know what else as far as trouble shooting to do.
My card is (according to windows) Dell Wireless 1390 WLan Mini-Card which according to NdisWrapper site is based on Broadcom BCM4311 chipset. That site also provided this Pciid:14e4:4311 (not sure what that is)
I couldn't find any information about a linux driver for this other than the NdisWrapper thing (not entirely sure what that does). Can anyone tell me if Ubuntu supports this hardware? If not is there anything I can do?

Thanks

---

### Post by james957 on 2006-09-17
I'm also having trouble with the Broadcom 1390 wireless card and Ubuntu Dapper Drake 6.06 .  I have a Dell Precision M65 with an Intel Core Duo (1.83 GHz) dual-core processor.  
I've tried both Ndiswrapper and bcm43xx-fwcutter with no success.  In both cases, Ubuntu does not recognize the wireless device.

With Ndiswrapper, I've tried both the bcmwl5 Windows driver, and the b57win32 Windows driver (both are located in my Windows folder C:\drivers\network\ (bcmwl5 in ~\addon and b57win32 in ~\onboard ).

With bcm43xx-fwcutter, I've tried bcmwl5 and wlapsta_0 (or something like that, I'm going from memory here).

I've seen several mentions of bcmwl5a.  Will that make a difference?  Where can I download that?

Does the dual-core processor require a different driver?

Does anyone know of step-by-step instructions for wireless and a dual-core processor?

Thanks in advance,
James

By the way, I've been pleased with the other aspects of Ubuntu (automatic NTFS mounting, recognition of nVidia graphics card).

---

