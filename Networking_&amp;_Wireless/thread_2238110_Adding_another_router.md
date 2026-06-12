---
title: "Adding another router"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by dave131 on 2014-08-06
We have Comcast Xfinity for TV, phone and internet and it uses a "black box" to split everything.  TV out via cable, phone out via cable, internet via wireless or 2-port (I think) router.  I would like to have more connections in the office where not everything is or can be wireless, but can use a wired network connection.  Without any changes to the Comcast "black box", is there some sort of stand-alone router like device uses wireless to connect to the access point (in this case the Comcast "black box") and has both wired and wireless ports of it's own?  I'd like to basically have a little subnet running in the office (I think that's the right term).  I know nothing about such things.  Any ideas?

---

### Post by QIII on 2014-08-06
Hello!

You should be able to use an ethernet switch.  One cable out to the switch from the router and as many cables out from the switch as it has ports.

My home network has a bunch of wireless devices, which all compete for the wireless bandwidth.  I have a single ethernet cable coming out of one of the RJ45 ports on the router to an ethernet switch that services a bunch of other wired machines under my desk.

---

### Post by sandyd on 2014-08-06
> **dave131 said:**
> We have Comcast Xfinity for TV, phone and internet and it uses a "black box" to split everything.  TV out via cable, phone out via cable, internet via wireless or 2-port (I think) router.  I would like to have more connections in the office where not everything is or can be wireless, but can use a wired network connection.  Without any changes to the Comcast "black box", is there some sort of stand-alone router like device uses wireless to connect to the access point (in this case the Comcast "black box") and has both wired and wireless ports of it's own?  I'd like to basically have a little subnet running in the office (I think that's the right term).  I know nothing about such things.  Any ideas?

What you should get is a router with DD-Wrt support, which will allow you to setup a bridge. Use the router to setup a [http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge) and you should be good to go. The speed of the internet (or transfers between devices connected to the black box) may be a bit slower due to the fact that all your connections are being piped through wireless.

---

### Post by QIII on 2014-08-06
It's Comcast!  :)

Their phone techs have a conniption if you say you have something else in the mix.

Then you get in a fight with them, threaten to go to another provider and realize they have a monopoly in your area.

---

### Post by weatherman2 on 2014-08-06
> **dave131 said:**
> We have Comcast Xfinity for TV, phone and internet and it uses a "black box" to split everything.  TV out via cable, phone out via cable, internet via wireless or 2-port (I think) router.  I would like to have more connections in the office where not everything is or can be wireless, but can use a wired network connection.  Without any changes to the Comcast "black box", is there some sort of stand-alone router like device uses wireless to connect to the access point (in this case the Comcast "black box") and has both wired and wireless ports of it's own?  I'd like to basically have a little subnet running in the office (I think that's the right term).  I know nothing about such things.  Any ideas?

If you can run an ethernet cable from the Comcast modem to the office, then you can simply add a wireless router in the office and that should do everything you need: provide wired connections and another wireless access point in addition to the one in the Comcast modem.

If you can't or don't want to run an ethernet cable all the way to the office but can pick up wireless in there, you can instead use a wireless ethernet bridge, a device to connect to your Comcast wireless network and provide wired ethernet connections.  Most consumer-grade wireless routers cannot be configured as ethernet bridges, but you can sometimes install firmware like Tomato or DD-WRT on a consumer router and add features like that. (Putting Tomato or DD-WRT on your router is like installing Linux on it.)  If you can find a Linksys/Cisco router that's 2-3 years old and is compatible with Tomato firmware, it can be easily turned into a wireless ethernet bridge.

---

### Post by dave131 on 2014-08-06
I just read the page you pointed to, and that seems to be essentially what I want to do.  So if I look on Ebay I basically just look for a wireless router with dd-wrt support?

If possible, I would like the devices to be on their own subnet - so if the wireless connection from the dd-wrt router to the Comcast router is 10.0.0.x, is there any way for the connections to the dd-wrt router to be something like 11.0.0.x?

Thanks!

---

### Post by sandyd on 2014-08-06
> **dave131 said:**
> I just read the page you pointed to, and that seems to be essentially what I want to do.  So if I look on Ebay I basically just look for a wireless router with dd-wrt support?

If possible, I would like the devices to be on their own subnet - so if the wireless connection from the dd-wrt router to the Comcast router is 10.0.0.x, is there any way for the connections to the dd-wrt router to be something like 11.0.0.x?

Thanks!

The setup above shares the comcast router's DHCP server as the interface is bridged over the wireless.

Make sure you read the dd-wrt hardware compatability list and reviews on what builds it supports before buying.

---

### Post by dave131 on 2014-08-06
So, would a device like this work:  [http://www.amazon.com/dp/B00DTPYRTI?psc=1](http://www.amazon.com/dp/B00DTPYRTI?psc=1)

It seems to be able to be completely wireless with a new ssid, but do you think I could connect one of those wired multi-port things (sorry, I'm not sure what they are called) to the wired port and still have the connection be wireless?

---

### Post by dave131 on 2014-08-08
I thought I'd bump this up one time just to see if there are any comments on my last post and the device it links to.

---

### Post by bab1 on 2014-08-08
Why would you disregard @QIII 's advice?  All you need to expand your LAN is a simple 4 port switch with a cost of under $15 USD.  Plug a Ethernet cable between MODEM you have already and the switch and user the other ports for the various hard wired devices.  If you feel you need more than 4 more ports you can get a switch with more ports (4, 8, 16, 24 etc.).  There is no need to set up a 2 router and then bridge the thing so it becomes functionally a switch.  Just buy the switch, plug it in and be done with it.  No configuration needed.

Or... Have I missed something here?

---

### Post by dave131 on 2014-08-08
I need the connection between the switch and the access point to be wireless:


Comcast box ~~~~~wireless~~~~~~ switch in office

I can't hardwire to the access point and route one more cables to the office.

BTW - definitely not disregarding QIII's advice - they're one of the big experts.  It's just my understanding from that recommendation is hardwiring a switch to the access point, then running cables to the office.  I can't run any cables to the office.  From the access point to the switch needs to be wireless.  So is there such thing as a wireless switch other than what was recommended about a 2nd wireless router set up with the dd-wrt capabilities?

---

### Post by bab1 on 2014-08-08
Clearer now.  You will have to have a wireless extender to connect to the wireless router at the very least.  You might find that an alternative to configuring a wireless router to do that.

---

### Post by dave131 on 2014-08-08
Do you think the device I posted a link to in my previous post would work?  I see it has wireless and a wired port, but I don't know enough about these things to know if it can connect via the wireless to the existing network and, if so, I can connect a switch (I'm guessing from previous replies that that is what it's called) to the wired port?  Sorry to ask so many dumb questions but I just plain don't know much of anything right now.

Thanks for the input!

---

### Post by bab1 on 2014-08-08
> **dave131 said:**
> Do you think the device I posted a link to in my previous post would work?  I see it has wireless and a wired port, but I don't know enough about these things to know if it can connect via the wireless to the existing network and, if so, I can connect a switch (I'm guessing from previous replies that that is what it's called) to the wired port?  Sorry to ask so many dumb questions but I just plain don't know much of anything right now.

Thanks for the input!
Maybe, but I've never heard of it.  I prefer (in no particular order) Asus, Cisco, DLink or Netgear.  I have an old Linksys Wireless AP but it has no real range so I wouldn't get a Cisco/Linksys device without checking it out via Google to see what others say.

As we speak, I am pulling wires in my house that I'm remodeling.  I use wireless only in an emergency or if it is a temporary (i.e. guest) use situation.

---

### Post by dave131 on 2014-08-08
Wish I could pull wire, but alas everything is finished here and I don't want to go into ceilings or walls to pull cables and then patch them back up ;)

---

### Post by nix_weasel on 2014-08-11
what i did in the same situation was,
i have a oldish laptop wireless connected to internet router, brought a wifi router (Dlink dl-254) connected the two via cable (not wan port) shared internet from wireless to wired on laptop and done

---

