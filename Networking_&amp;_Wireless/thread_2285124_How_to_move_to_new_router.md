---
title: "How to move to new router"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by rbroman on 2015-07-03
I have a Kubuntu 15.04 box (and other systems) on a home LAN to a Comcast cable modem. I have had previously, and have now, difficulty in replacing my LAN's router with a new one. Ie when I physically substitute/reconnect the new router for the old one, the Kubuntu box does not communicate with the new router or the internet. When I go back to the old router everything works fine.

I've tried this with different new routers and result is same, so I assume its not the router itself or its cables. I'm no networking expert, but I do notice with the new router, the response to arp -n on the Kubuntu box shows HWaddress incomplete.

Is there a series of commands I should issue on the Kubuntu box to cause the box to connect to/thru the new router?

Thx, Gus

---

### Post by Bucky Ball on 2015-07-03
The IP address of the new router is probably different to the old one. Read the documentation that came with the new router, plug it all in (the router via an ethernet cable), open a browser and type the IP address of the router into the address bar and hit enter. You should be taken to the router's configuration GUI. Set it up the same way as the old router.

No series of commands, nothing much to do with Kubuntu. You need to configure the router. Very doubtful you would plug it in and would just 'work' the way the other one did. It will be at factory defaults for a start. If you're using it wirelessly you'll probably need to set up the wireless properties, etc. Write them all down from the other one if required prior to unplugging.

---

### Post by weatherman2 on 2015-07-03
Unless you have a reason to, all of your devices on your network - Kubuntu computer, phones, etc. - should all be set to DHCP/Automatic to obtain their IP address.  If that's the case, then you don't need to do anything with them - when you unplug them from the old router you lose your IP and get a new one when you plug into the new router.  Same when you connect a wireless device via WiFi to a new router.

You do need to make sure the new router is not on the same subnet as the Comcast modem.  Lately, Comcast has been using 10.0.0.1/24 meaning anything connected to the modem gives you an IP of 10.0.0.2 - 10.0.0.252 (or so).  If you connect up a router to the modem, it must NOT use 10.0.0.1/24 - it should be different.  Typically a router will use 192.168.1.1/24 or something with 192.168 at the beginning and that's fine.

Final thing with Comcast modems: you may need to power cycle them once after connecting new devices to them.  Sometimes a new router can't get internet access from the Comcast modem until the modem power cycles once to recognize the new device.  In rare cases (old equipment), you may also need to call Comcast support to register a  new hardware (MAC) address for the device connected to the modem.  Or you can clone the MAC address of the old router in the new one, so the Comcast modem thinks the old router is still connected.  I doubt you'd have to do that anymore, though.

---

