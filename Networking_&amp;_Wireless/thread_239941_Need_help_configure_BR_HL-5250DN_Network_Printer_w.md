---
title: "Need help configure BR HL-5250DN Network Printer with Cups"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by gustavson12 on 2006-08-20
Ubuntu 6.06
I'm tryig to setup up a Brother HL-5250DN Network printer and I'm stuck on the ipp.  I have the ip address of the printer.  I am able to ping printer via terminal.  I have downloaded the correct driver from brother and I am albe to load it during installation.  But....

What do I put in the URI:

Is the first part correct?

ipp://printerIPAddress/???/???

I have tried searching for answers with no luck....

I have tried several inputs with the same error result from cups:
"/usr/lib/cups/backend/ipp failed"
and printer status says stopped

Thank you for looking...

---

### Post by Robin Whittle on 2006-09-21
On Debian 3.1 I found success using the CUPS local web-based admin system:

  [http://localhost:631](http://localhost:631)

There, I gave the URI as:

[http://10.0.0.16:631/ipp](http://10.0.0.16:631/ipp)

Initially I gave:

[http://10.0.0.16:631/ipp/](http://10.0.0.16:631/ipp/)

and this resulted in a test page being printed.  However I couldn't print from applications until I removed the trailing slash.

The web-based CUPS management seems far better than Debian's Gnome Desktop Preferences > System Tools > Printing thing - I wasted hours and hours trying to use that.

  - Robin

---

