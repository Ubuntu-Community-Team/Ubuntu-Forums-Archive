---
title: "Wake on lan (WOL) from S3 suspend?"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by njparton on 2007-11-06
Well I've just switched from Gutsy AMD64 to i386 and it's single handidly solved my suspend to ram issues, apart from one...

When I suspend to ram my network card (intel pro/1000 PT) is switched off (no lights on at the back) and I can't therefore send it a magic packet to wake it up.  

If I perform a shutdown then the card stays live and I can wake it with a magic packet.

I've used ethtool to configure wol "g" mode via rc.local

Is there a way in ACPI settings (or elsewhere) to force my NIC card to stay alive in S3 suspend? At the moment I'm not forcing any modules to _un_load via the config files.

I have S3, ACPI and wake from PCI/PCI-E enabled in the BIOS.

---

### Post by |V|utley on 2008-02-25
I have a very similar problem.

I'm also using Gutsy.  When I shutdown the I can restart using WOL, when I suspend to S3 I can't.
However, when at S3, the network light is still on.

What I find when I resume from S3 though is that the network card is no longer configured to support WOL.

I've tried adding the driver (8139too I think) to the modules whitelist in /etc/default/acpi-support but that has made no difference.

This is driving me mad, and could be the reason I have to ditch Ubuntu, as daft as that sounds.

---

