---
title: "Setting up Dlink DWL-G122 (rRev. D) Wireless Dongle"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by jmas on 2008-01-25
I run Linux Mint "Daryna" 4.0, which is in effect Gutsy Gibbon. That's why I'm posting the question here.

I recently got the Dlink DWL-G122 (rev. D) dongle and plugged it into my Presario 2227US laptop; downloaded the drivers from the Dlink website and they worked like a gem on my Windows partition. In Linux, though, when I went into Windows Wireless Drivers in the Administration menu and installed the USB55N5x.inf file, it said the driver was invalid.

Same happened when I then reinstalled through the CLI:

> jonathan@Gottfried-Wilhelm:~/Desktop/Dongle/DWL-G122 D/Drivers/Windows XP$ ndiswrapper -r USB55N5x.inf

It reinstalled the driver yet the Windows Wireless Drivers window said the driver was invalid. This is the official Dlink driver that according to my research was supposed to work using ndiswrapper. Any suggestions?

Jonathan

---

