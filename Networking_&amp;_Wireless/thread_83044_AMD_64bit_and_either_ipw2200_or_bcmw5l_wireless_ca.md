---
title: "AMD 64bit and either ipw2200 or bcmw5l wireless cards."
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by skmassey on 2005-10-27
I have an Acer Aspire 5002 with an internal (miniPCI) Broadcom wireless card using the bcmw5l chipset/driver.  The CPU is a Turion 64.  I'm running Breezy 5.10 64bit.  I have had no luck getting NDISwrapper and the windows drivers to work with my system.  My questions are:

1. Has anyone been able to get this to work?

2. Has anyone been able to get a card using the ipw2200 chipset/driver to work with a 64 bit system?

](*,)

---

### Post by mlomker on 2005-10-27
> 2. Has anyone been able to get a card using the ipw2200 chipset/driver to work with a 64 bit system?


Yes, it works out of the box for me.  Intel has native drivers and doesn't require ndiswrapper.

I assume you know that you need 64-bit WinXP drivers to use with ndiswrapper?  Sometimes one Broadcom windows driver will work and another won't.  I'd recommend searching Google and trying a couple.

---

### Post by Tass on 2005-10-29
Hi

I'm having similar problems with my wireless card.  I have the Acer Aspire 5024, with the broadcom (bcmwl5.inf).  I have managed to get the the device installed and appearing in the list of network devices.  Have you been able to get that working?  If now, let me know and I'll give you a list of steps that I went through.

Once that's set up, I try to configure it to use DHCP.  When I activate it, it takes about 30 seconds.  When viewing the device in the Network Tools, it only have an IPv6 address, and not an IPv4 address.  If I activate my ethernet connection, it aquires an IP Address without any problem.

Anyone else had this problem?

---

### Post by skmassey on 2005-11-01
I had the same problem with mine.  I installed it several times and one time it actually showed up.  One thing I noticed about that though is when I issued the command "lspci" it still showed up as an unknown device.  But for some reason it showed up under my network-admin GUI tool.  Also appearing under the iwconfig command it would show that it had no wireless extensions.  :???:  That says to me that the card wasn't correctly installed.  I was using ndiswrapper 1.4 and the bcmw5l driver from the acer site.

---

