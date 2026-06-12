---
title: "Bluetooth with LG Shine on Gutsy"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by abrichr on 2007-11-13
I am on a Compal HEL80 Laptop.  Yesterday I got the Canadian model of the LG Shine with Rogers: the TU720.  In Gutsy AMD64, I was able to see the device, but couldn't connect to it, and received the message:

> "obex://[mac:address]" is not a valid location.

So I installed gnome-vfs-obexftp as per [https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/138356](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/138356).  Now when I try to connect, it asks for a password on both the shine and the laptop, so I enter for example "0000" on both, and it reports a successful connection.

When I try to paste a file into the device, the device reports once again that I'm trying to connect, which I allow.  But then I receive the message "File I/O Error", and my phone reports no free space--even though there's nothing on it.  I've tried with both the internal handset memory and the microSD card.

When I tried to turn bluetooth off on the phone, it said data transfer in progress, and I noticed that my wireless light on the laptop was flashing.  Turning it off allowed me to turn of bluetooth on my phone.

This isn't the only problem I've had with this phone, and will try to connect to a windows PC in order to narrow down the problem.

---

### Post by abrichr on 2007-11-14
Just thought I'd let y'all know that I switched phones and no longer have any problems.  I had so many problems with the shine... let this be a warning to whomever reads this post:  STAY AWAY from the shine.

---

