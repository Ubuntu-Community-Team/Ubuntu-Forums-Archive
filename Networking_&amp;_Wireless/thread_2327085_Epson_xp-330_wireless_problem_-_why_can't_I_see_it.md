---
title: "Epson xp-330 wireless problem - why can't I see it"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by uli9 on 2016-06-07
I connected the printer through the printer panel to my home network (with WPA2 password). It connects ok. It prints the setup report. Everything is ok, it has an IP address.
I log in to the router and it's there as a connected device.
If I ping it from Ubuntu laptop it's unreachable. (I can ping it from the router.)
If I run Zenmap it doesn't show up.
Also Windows 10 and my Android phone cannot see it.
When I switch the WIFI connect mode at the printer to direct connect to the printers WIFI, my phone can see it (I haven't tried it with the Laptop, Ubuntu or Windows. 
Why can I not reach the printer through the home network?

---

### Post by X-RED_Tech on 2016-06-08
> **uli9 said:**
> Why can I not reach the printer through the home network?

Good question and I wish I knew the answer but it has nothing to do with Ubuntu because > Also Windows 10 and my Android phone cannot see it.

It's something on the printer settings, the router or both. How exactly can we help?

---

### Post by uli9 on 2016-06-08
I am already on the hardware forum for Ubuntu driver issues with this printer. So I thought I could get some help here troubleshooting the networking issues I also have with this printer. I know it is not specifically Ubuntu related, but it is the primary OS I am using. I just hoped someone with networking knowledge could suggest something I can do to understand what is going on.

---

### Post by X-RED_Tech on 2016-06-08
Is the printer's IP in the same range as the other devices/computers?
Router make/model?

Perhaps by providing this additional somebody will figure it out. The problem is, I insist, somewhere between your printer and the rest of the network.

---

### Post by uli9 on 2016-06-08
The printers IP address is in the same range as other devices on the home network 192.168.1.7. Like I said, when I login to the router it is listed as a connected, active device.
The router is from Verizon. I have to check later for model number.

Come to think of it now: Could there be an address conflict, because I also connected the printer via USB to an Ubuntu desktop, which is also on the network via ethernet?

Or, could the router somehow be blocking communication to the printer?

---

### Post by X-RED_Tech on 2016-06-08
> **uli9 said:**
> Come to think of it now: Could there be an address conflict, because I also connected the printer via USB to an Ubuntu desktop, which is also on the network via ethernet?

No, the DHCP should handle that. You just added a new device to the network and the router shouldn't allow such conflicts to happen.


> Or, could the router somehow be blocking communication to the printer?

Probably. Try rebooting it anyway and the printer.

---

### Post by uli9 on 2016-06-09
Oh well, this is somewhat stupid and embarrassing. Resetting the router and the printer worked. Thank you for your help X-RED_Tech!

---

### Post by X-RED_Tech on 2016-06-10
Somehow it wasn't "broadcasting" or making available - I really don't know the correct terminology - the printer's IP before restarting. 
Nice it had such simple solution.

---

