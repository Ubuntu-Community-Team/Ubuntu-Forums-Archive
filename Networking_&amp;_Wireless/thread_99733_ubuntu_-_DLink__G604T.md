---
title: "ubuntu - DLink  G604T"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by craigdele on 2005-12-06
Is anyone using ubuntu successfully with a DLink DSL G604T router?

I am unable to update or use Gaim. From reading the forums it appears it may be a router problem. I have checked the Australian website(i live in NZ) for the lastest firmware. However i already have this installed.

There is a version 2 of the firmware for Australian ISP as this version caters for ADSL2. Would it be wise to install this version on my router (NZ does not yet have ADSL2) or will it damage my router?

Any suggestions.

regards

Dele

---

### Post by manicka on 2005-12-06
I have the same router. Enter your network settings manually, particularly the dns server which the router provides incorrectly with dhcp. 

system --> Administration --> Networking

In the DNS tab Remove the router as the dns server and replace with your isp's settings

---

### Post by mips on 2005-12-06
If the above does not work also try disabling IPv6.

You can also try configuring port forwarding on the router for the specific TCP or UDP ports in use.

D-Link Oz supplies the NZ market so I dont 'think' the hardware is different. According to their website you wont be able to downgrade the firmware again without sending it to d-link.

The ADSL2/2+ only adds support for that version but does not remove the ADSL1 support. You can always contact NZ tech support on 0800 900900 and ask them if it will work or not.

---

