---
title: "Egdy, and D-Link DWL-G122 Rev A2."
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by Yourname on 2006-11-06
Hi,

Got my DWL-G122 Rev A2 and it's PRISMA02 drivers to work with ndiswrapper.

It says driver present, hardware present as well. I also configured/enabled the wireless wlan0 in System-> Networking to work with DHCP and also entered the SSID of my router.

On the router, there's no security, but only MAC addr filtering, to which my dongle's mac addr is set. So, it should connect.

But for some reason it doesn't.
Also, I did tried to use the nm-applet to click and connect on my SSID, but now it just doesn't show up.

I've tried doing an ifconfig scan, and it showed the networks.
But it doesn't show in the networking drop down anymore either.

I did modprobe, etc..and did lsmod to see what drivers are being used, and it says ndiswrapper.

What else do I need to see?!
It worked before (neber got to connect cuz of WPA2, but now I removed WPA2 cuz I couldn' get it to work)

---

### Post by Yourname on 2006-11-06
Nobody?

---

### Post by Yourname on 2006-11-07
Well, if there was atleast ONE soul watching this thread, then this is for you.

I made it work.
I don't have security, so.. this step worked.

I read that linux-wlan-ng will work. It didn't.
Network-manager was supposed to work, it didn't.

Removed 'em all. 
Rebooted.

And it worked.
Just made sure ndiswrapper had the driver installed, and made sure in System->Admin-Networking it was configured to my AP.

---

### Post by FrodoB on 2006-11-07
Well done!

---

