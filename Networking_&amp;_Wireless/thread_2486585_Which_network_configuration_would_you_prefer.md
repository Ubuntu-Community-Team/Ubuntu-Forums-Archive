---
title: "Which network configuration would you prefer?"
date: 2023-05-04
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2023-05-04
I'm making some changes in my network and would like opinions on how you would set it up. To start:
[LIST]
[*]Cable internet 200/10. That seems slow but there's just me and I'm not a heavy user; no games, no heavy duty graphics, no cloud stuff. 
[*]I 'cut the cord' so no cable TV. Instead I have a Roku for each TV. I have 3 TVs but only one in use at any one time. They're all smaller than 55" so no need for 4K. 
[*]I have been using the ISP provided modem/router combination. It's a fairly low end device (Cisco DCP3941T) but the WiFi is surprisingly good. The device is in the basement, Roku devices are on the 1st and 2nd floors. Signal strength indicates good or better on the Rokus. That WiFi network supplies only the Rokus and a very undemanding weather station. I have a second WiFi network that supplies service to laptops and phones. 
[*]I have a MoCA network that supplies desktops and printers with network services. I also have a wireless access point supplied by the MoCA network. Until recently this wireless access point was the only wifi source. I had fiber for some years but the fiber provider's rates were substantially higher than the cable company's rates and I don't really need the higher download/upload speeds of the fiber provider. I know this is contrary to many peoples' needs but there we are. Actually the real motive for switching was phone service. Internet and unlimited voice/data for around $35 USD/month plus any streaming services. We were paying around $175/month. 
[/LIST]

Up until today the ISPs modem/router combo was providing DNS services and WiFi. The second WiFi access point was supplied by the ISPs ethernet. I had been using a TP-Link router with DD-WRT for routing/firewall/DNS/DHCP services prior to getting the ISP provided Gateway. When I got the ISP provided device it took over those services. It seemed like wired ethernet was not as responsive as it was with the TP-Link/DD-WRT device and configuration options on the ISP provided modem/router are pretty sparse. I can understand why they make that choice; most people want to plug a device in and use it without further thought.

I considered just making the ISPs device a modem only but the WiFi on that device works very well and if I enabled Bridge Mode I presume I'd lose wifi function on the ISP provided device. Right now I have this configuration:

Coax cable -> to ISP provided Cisco DCP3941T Gateway. In the back of the Gateway are 4 ethernet ports, I'm using 2. One goes to the TP-Link/DD-WRT WAN port, the second goes to an Ooma VOIP device. The TP-Link/DD-WRT router feeds into an unmanaged switch one floor up. That unmanaged switch is connected to 2 printers, a MoCA 2.0 bonded adapter (theoretical 1 Gb. throughput) and a desktop PC. Another ethernet cable from the switch feeds the 2nd WiFi access point. I was concerned about having two routers sort of daisy chained, I was expecting DNS or DHCP conflicts but I guess having 2 separate networks there's no conflict. So to my question.

Am I being silly and needlessly complicating my life? Are there any security implications? Should I go back to just using the ISP supplied router. It sure seems like using the 2nd router makes things quicker. For one thing I am able to choose a 3rd party DNS provider, using the ISP supplied device I have to use the ISP's DNS. It seemed like DNS was slower and would sometimes stall for a couple seconds on the ISPs Gateway. The firewall in the ISPs Gateway seems pretty basic but probably more than most customers know or care about.

I appreciate any thoughts or input anyone wishes to provide. Thank You.

---

### Post by aljames2 on 2023-05-04
Are you required to use your ISP gateway/modem?  I use Cox cable in my area and they  offer an option to use/rent their gateway.  No me.  In fact I don't even  use their modem.  I bought my own Arris cable modem and that connects  to the WAN side of my own router/firewall running pfSense as my  gateway.  I used to have Verizon Fiber and hated it when the service was not available at the house we live in now, so I had to go back to the coaxial crap.  Fingers crossed, service is working good this time.

If you are required to use your ISP device so that they have something to poke at every now and then, then bridge  mode is an option to essentially make their device a passthrough device  to your own router/gateway just beyond that.  If it were me I would also disable the ISP device wifi as well.

On my network I prefer wifi to be on a physically separate network from my LAN, strictly for IoT type devices, Rokus, etc., and I also like the idea of using an Access Point for this, not a router that has wifi.  Some routers that have wifi can be put in AP mode, but the surest way is to just use an AP.  Daisy chaining routers and leaving them set up as routers is not good and can lead to double NAT which you likely don't want.  My AP is a Unifi nanoHD all the way on the other end of the house about 100 feet away where the TVs and lounging stuff goes on.

Sry for the rambling, not sure it's answering much for you. Networking is the fun geeky part of this that I enjoy.  Have fun !

---

### Post by kurt18947 on 2023-05-05
I don't have to use the ISP's device, I do own a DOCSIS 3.0 cable modem, no router. I do like the ISP's Gateway for its WiFi which is why I didn't set it to Bridge Mode. I thought there is some security benefit to having multiple wifi networks though I may be off on that. I just got a notice that there may be service interruptions "due to network upgrades" from the ISP. I suspect the network upgrades might be from DOCIS 3.0 to DOCIS 3.1. DOCIS 3.1 modems are a fair bit more $$$ than 3.0. I think DOCSIS 3.0 devices will work on networks that are DOCSIS 3.1 at least for a while. The Gateway from the ISP is free for now so no cost associated with using it.

---

