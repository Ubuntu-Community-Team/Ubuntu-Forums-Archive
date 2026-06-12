---
title: "Onboard Realtek NIC not playing nice with Ubuntu"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by DaltonAdair on 2008-08-09
Okay, so myself and another person here were working with the Realtek 8169 card onboard my d945gclf intel motherboard.

The problem I was having is that for some reason the card can detect a network, but it seems I am unable to be assigned an IP address. Or so it seems.

I checked my router's DHCP service and it shows my desktop connected with an assigned IP address. Huh?

The only thing I can think of is the driver is jacked up.

The driver is r8169. Is there a newer/better version of this driver? Can anyone please help?

The only thing that seems to work is disabling, then re-enabling the onboard card via the BIOS. (cycling the power inbetween of course.)

This is a highly temporary workaround, I don't want to have to cycle my NIC on and off every time I want to reconnect to my network.

I could leave my computer on all the time, but I would rather not. 
I like to save energy, part of the reason why I went with an Intel Atom in the first place.

---

### Post by chili555 on 2008-08-10
I doubt that the driver is 'jacked up.'> The problem I was having is that for some reason the card can detect a network, but it seems I am unable to be assigned an IP address.Can you please explain this further? How is your ethernet card detecting a network?

Does this machine dual-boot with Windows? If so, please read this: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/)

---

### Post by Xeon3D on 2008-08-31
The driver actually IS 'jacked up'.

Updating to a newer kernel would solve your problem.

---

