---
title: "strange network problem"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-05-08
hi
i have a strange problem, which then causes many other problems...

for some reason, there is a "usb0" networking interface on this system, as of ifconfig. however, there is no such device in the system. the only usb thing is a printer.
the onboard LAN is a palin realtek 8139c, which is not connected through internal usb either.
so i have really no idea what is this usb0 network thingy??
and the worst, it is the default interface for some reason, so i can not get to the internet etc.
i tried to disable this in ifconfig, only to realize, that there is no such device configured in ifconfig at all!!! :O
i have only found it in iftab, commented it out, so now eth0 is the only and default device, and i have internet and can use the LAN.
sounds good, eh?
but no, it isn't!
the device is still showing up with ifconfig, i wonder how is that possible???
i have brought it down (ifconfig usb0 down, and ifdown usb0), and now it's disappeared finally. but how do i do this permanently?
strangely, there is no /dev/usb0 device either...
no routing goes through usb0.
so i have absolutely no clue where is this coming from...?
can it be a virtual device "created" by avahi somehow?

other thing is, if i log in to this pc locally, it now works perfect.
however, if i log in on a vnc session, firefox works, but the system updater, synaptic, etc. don't. they still try to use usb0 to get to the internet. if i down this silly "device", then the above programs generate a lot of "outgoing" traffic on the loopback. like if the above programs would choose lo as the interface to use?! silly.
any ideas, someone? i must get rid of this, permanently.
thanks.

---

### Post by Iowan on 2008-05-08
Have you checked the "Manual network configuration" to see if it lists a USB option (maybe as a connection or under "Wired")?

---

