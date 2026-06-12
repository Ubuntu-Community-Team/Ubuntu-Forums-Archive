---
title: "help me out! wireless problems"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by millertime_018 on 2007-06-06
ok you can e mail me at [email]millertime_018@yahoo.com[/email]. i typed in the lspci - v thing and it gave me this

06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 88000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

i have already looked through the broadcom forums and that didnt help. i would like to know how to get it working. is fwcutter something thats preintalled on fiesty fawn? how do i install if it isnt? help me out please!

---

### Post by Jamie Jackson on 2007-09-10
I've tried most (all?) of the options:

[NDISWrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"): Most involved, but most transmission power, max speed
[Native Driver]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated#comment-1818"): Easiest, low transmission power, medium speed.
FWCutter: (Used to be easiest, but there's a bug in the current package, that makes it a bit harder), low transmission power, lowest speed.

I don't have a link handy for the FWCutter method (that covers the bug workaround) at my fingertips, but you can search around for it.

Update: Oh, and FYI, you have a BCM4311 (Broadcom 4311) Device.

---

### Post by itzmiko on 2008-05-19
spend $30 and get the intel chipset wireless card for your dell.  the broadcom chipset runs like crap even if you manage to get the drivers installed.  Frequent disconnects, slow throughput, etc.

the 3945 intel cards work great in my dell laptop, well worth the $30 for the refurb card i got

---

