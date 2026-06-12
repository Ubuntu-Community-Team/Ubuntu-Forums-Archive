---
title: "Faster networking via thunderbolt or USB3?"
date: 2017-10-07
forum: Networking &amp; Wireless
---

### Post by jlparsons on 2017-10-07
I work on a laptop (linux mint) which sits less than 3 meters away from my server (ubuntu server) and regularly transfer large files between them.  The bottleneck is the gigabit lan which connects them, topping out at about 120 megabytes per second.  This isn't a massive issue for me and I wouldn't be bothered upgrading to 10g any time soon to get around it due to the cost and the fact my laptop doesn't have 10g, but it does occur to me that both machines have spare USB3 ports capable of 5gigabit throughput (albeit one way I believe) and it would be easy to add a thunderbolt card to the server for 10/40gigabit.  Question is, is there any way to do this currently?  My guess is there's two possible routes;

Firstly I could leave the network as it is but have the server and laptop share folders via a thunderbolt/usb connection - effectively have the server act as a mass storage device.  I haven't been able to find any way to do this on the forum or googling.  There are USB host-to-host cables available but the ones I've found appear to be USB2 (slower than gigabit) and windows/mac only, requiring proprietary software.  Anyone managed such a thing on linux?

Secondly I could get rid of the laptop's gigabit ethernet connection and connect it to the server via a usb/thunderbolt connection masquerading as a network connection, as I know has been done on windows/mac machines and I know is a goal of the linux thunderbolt project.  My guess is I would have to configure a virtual switch on the server between its incoming ethernet port, the usb/thunderbolt connection and its own default gateway such that the laptop is daisy-chained onto the network via the thunderbolt/usb connection with the server.  From the look of it the plan is that in the future thunderbolt will do this out of the box, allowing a high speed network between daisychained thunderbolt devices.  Again I'm drawing a blank on the forum and google on how to form the basic usb/thunderbolt network connection.

Anyone done similar, or know if either option might be possible?

---

