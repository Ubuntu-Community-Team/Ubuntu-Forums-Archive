---
title: "Wake on Lan - stopped working"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by philip7 on 2016-10-02
I'm currently running Mythbuntu 16.04, I've had this running for a few months and WOL has been working without any issues, a few weeks ago WOL suddenly stopped working. I didn't make any changes or updates to the PC or the router.

I've tried to send WOL packages from multiple devices but they also haven't resolved the problem.

I followed the instructions found here:
[http://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04](http://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04)

There still seems to be power to the network card as the lights are on when the PC is turned off but I've completely run out of ideas what caused the problem and how to fix them, any suggestions would be appreciated.

Thanks

---

### Post by papibe on 2016-10-02
Hi philip7.

Any router, switch, or other network device in the middle of the machine you try to wake up and the one sending the command?

If the router was reset, and/or the machine hasn't been turned on in a while, the router or switch may have dropped the target machine's info from the arp table.

Try this: turn on manually the machine you want to wake up. Make up some traffic from the machine to pass through the network device (a simple ping would do). Turn it off again, and now try to wake the machine up.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by philip7 on 2016-10-03
Only the router between my phone/tablet and the PC, I've used tcpdump whilst the PC is on to confirm that the package is being received.

I've also used the phone/tablet to browse web/file content on the PC.

I have tried sending package from other devices as well just to rule them out the phone/tablet, I've also confirmed the phone/tablet are sending are able to wake a device by waking up another PC on the network.

Just a bit more information the PC is a Shuttle SP35P2 Pro, I have "Wake up by PCI Card" enabled, I don't think there is anything in the BIOS that I need to change but can provide details if required.
The manual is here: [http://download.shuttle.eu/Mirror/XPC/SP35P2/Manual/MANUAL.ZIP](http://download.shuttle.eu/Mirror/XPC/SP35P2/Manual/MANUAL.ZIP)

---

