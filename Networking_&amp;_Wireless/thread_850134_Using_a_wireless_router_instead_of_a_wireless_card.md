---
title: "Using a wireless router instead of a wireless card to connect to existing network"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by tubegeek on 2008-07-05
I have a spare wireless router, a Netgear WGR614.

My goal is to replace a wired Ethernet connection with this router. I haven't been able to find this info in the router manual, can anybody suggest a resource for this or how to do it?

The current setup: a cable modem connects to the ISP upstream, and downstream I have a Linksys WRT54GL running Tomato firmware. I connect wirelessly to the Linksys from a Mac laptop, and I have two Linux (Ubuntu 8.04) machines connected to the Linksys via Ethernet cables. These machines have static routes. One Linux machine will be more useful across the room, so I want to create a wireless link between this machine and the Linksys router, using the spare Netgear router.

thanks,

-tubegeek

---

### Post by kevdog on 2008-07-05
Hmm, not sure if you can do this with the Netgear router, although you could with the Linksys.  What concept you are describing is wireless bridging or Repeater Bridge.  These features are available with the dd-wrt firmware -- I'm not sure about tomato firmware although it has a lot of features similar to dd-wrt.  What I think I would do would be to use the Netgear router in place of the linksys (this is the router connected to the router), and then use the linksys to be the wireless bridge or repeater bridge.  In fact I have the same setup at home myself.

Here is the dd-wrt pages on wireless bridging and repeating:
[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)
[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

---

### Post by tubegeek on 2008-07-05
There are two reasons I want to use the routers in the order I have them - one, so I can QoS my network using Tomato on the Linksys, and two, because the Netgear has one dead port.

I will try and learn about Bridge mode now that I know that's what I want - **thank you for the pointer!** Worse comes to worst I'll try to find something cheap that is capable of Bridge mode . . . 

- tubegeek

---

