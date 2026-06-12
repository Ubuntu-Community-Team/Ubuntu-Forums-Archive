---
title: "proper network installation in a two floor building"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by iokara08 on 2016-04-23
Good evening linux users,

I am running a small ''rooms for rent'' business and I would like to share with you the network configuration that I have figured, for spreading an adequate wifi signal in all floors, in order to give me any ideas for better results. Below you can see a description of my setup which currently works quite ok but I need a better wifi expansion at the edges of each floor:

Internet connection from my ISP: VDSL at 30Mbps max.

**Ground Floor:** Modem Router (Wireless router Speedport Entry2i, VDSL2, 2,4GHz, DHCP/DDNS client)

**1st Floor:** On the 1st floor I have installed the TP Link TL-WA901ND (wireless N Access Point 300Mbps) which is connected via ethernet cable with the modem router and it operates in access point mode where its DHCP mode is deactivated.

**2nd Floor:** On the 2nd floor I have installed a range extender, TP Link WA850RE 300Mbps, which simply expands the wifi signal to the 2nd floor.

Would it be a better configuration if I was replacing the range extender to a new access point same type of the one on the 1st floor? Since it is difficult to ''run'' one more ethernet cable from my modem router to this new access point could I use an ethernet switch on the 1st floor? What do you think about this configuration?:confused:

Useful Information:
- each floor is about 100m2
- access point on the 1st floor and range extender on the 2nd are placed at the center of each floor and they have a good wifi communication to each other (the signal of the range extender is at full bar which means a very good communication)
- wifi cover in whole building is quite good but it could be better...since the signal at the edges of each floor   

Thank you in advance for your time ):P

---

### Post by TheFu on 2016-04-23
Get a single Ubiquiti UniFi AC LR (long range) access point.  Place it in the center of the building - don't worry too much about the direction it faces.  There are some youtube videos which show some amazing results. About US$110 (today) for that single device.  There is an Android app which is used to configure the device(s) or you can run the config software on your Linux/Max/Win machine. After config, it isn't needed and doesn't need to be left running.  If you have more than 1 AP, the centralized config makes these nice too.

UniFi are PoE devices, so just an ethernet cable needs to be run from the router to the AP location. 

My house is about that same size and the regular UniFi is working great here.  There is night & day difference between Ubiquiti stuff and the consumer stuff.  Plus Ubiquiti handles more concurrent connections, better, than consumer-level stuff.  
[http://www.amazon.com/Ubiquiti-Networks-Enterprise-System-UAP-AC-LR/dp/B015PRCBBI/](http://www.amazon.com/Ubiquiti-Networks-Enterprise-System-UAP-AC-LR/dp/B015PRCBBI/)

I don't work for this company. Just a happy customer after about 10 deployments.

The material for the building matters.  5Ghz doesn't like walls or floors, but 2.4Ghz works fairly well ... unless it is concrete/brick/rock.  If you have a challenging building, place 1 of these on each side of the building (2 total) on the 2nd floor. That should cover it.  If you do put in UniFi, might want to disable the other WiFi devices to limit interference.  The APs will have the same SSID, which makes life convenient.  Plus you can control the power (higher isn't always better) so it is like a grid that works together, but doesn't confuse the devices when a connection transfers from one AP to the other.  In the USA, there are only 3 non-overlaping 2.4Ghz wifi channels - 1, 6, 11. Unless the wifi spectrum is crowded, don't bother with any other channels besides those 3, since that will reduce performance.  In a crowded wifi area, sometimes there isn't any choice and the other channels have to be used.

Make sense?

Not certain what any of this has to do with Ubuntu. ;)

---

### Post by iokara08 on 2016-04-24
Good morning Ubuntu Master (coffee level :cool:) and thanks a lot for your time to reply on my thread which of course has nothing to do with Ubuntu...I just thought to write here in the networking forum since I am an Ubuntu user who trusts a lot the open source community.Additionally, Ubuntu forums is the only forum that I am registered :???: 

The building consists of brick walls and in some point double brick walls and of course concrete floors...(location of building is in Greece). I checked on the net the device that you suggested and based on its characteristics looks much powerful than the APs that most eshops suggest customers to buy.

So you suggest me to have the following deployment:

Ground floor: Modem router -----------ethernet cable------------> 1st Floor: Ubiquity Unifi (Should it work with its DHCP mode turned off?)

If I do so and I see that it does not cover adequately the whole area will it be possible to use it in combination with my other devices(e.g. the extender )? or it will cause interference issues as you mentioned?

So you don't think that my primary deployment could bring some results:
Ground floor: Modem router -----------ethernet cable------------>Ethernet Switch--------------> 1st Floor: Tp Link AP1 & 2nd Floor: TpLink AP2 (New device)                                                                                                             
                                                                                                                                                                                                                            
Thank you once again for your deployment suggestion which I have already started thinking seriously.
Have a nice day

---

### Post by TheFu on 2016-04-24
I've never visited Greece, but it is on my huge list of places. ;)

Most buildings where I've done wifi deployments are NOT concrete/brick, so I don't know how well this will work. Location, location, location matters for wifi, just like real estate. No way to know what will work until you build it.

The only place that had concrete construction where I did some wifi was in Nepal and that was a 5-node, indoor/outdoor setup. We put some Ubiquiti directional outdoor APs in the outer corners facing in to cover the compound with 1 AP in the center for the office staff.  I used a wifi signal tool (android app) to find wifi coverage for the compound before and after we did everything. Since it was a monastery and I'm not a monk, certain places were off-limits.  My room was on the 4th floor, center, outside ... about the worst location with a minimal of 3 concrete walls between the desk and any wifi access. It was fine, but not great. This compound was about 3 acres in size with rooms for about 70 people.  The point is that concrete will stop 5.8Ghz signals and be useless. 2.4Ghz signals can get through some concrete walls, but more than 3 walls is hard.

At another location, we deployed wifi APs every other floor on opposite sides of the building (it was a big bldg 45 floors).  East side of the bldg had APs on 1, 3, 5, 7, 9 ..... 43 floors and the west side of the bldg had APs on 2, 4, 6, 8, 10 ... 44 floors.  You might try that in your situation. Just be certain to use different, non-overlapping, channels for the 2.4Ghz frequencies.

Yes, you can use an ethernet switch. I would and do.  Have a few cheap, unmanaged, US$20 8-port switches here.  I have a TP-link wifi router, BTW, but it wasn't stable, so it sits in a box, unplugged. Unfortunately, I didn't get around to installing it until after the return period had expired, so I'm stuck with it.

APs all work basically the same way.  The keys to mixing different vendor HW is to stay with standards and to avoid overlap of RF signals and to use different channels for every AP.  You only want 1 DHCP server on the network. Normally, the router does that, not the APs.

Good questions. Sorry I cannot say whether anything will work or not. No way to know until it is all connected and tested.

[http://arstechnica.com/gadgets/2015/10/review-ubiquiti-unifi-made-me-realize-how-terrible-consumer-wi-fi-gear-is/](http://arstechnica.com/gadgets/2015/10/review-ubiquiti-unifi-made-me-realize-how-terrible-consumer-wi-fi-gear-is/) might be helpful.

---

### Post by iokara08 on 2016-04-28
Hi again,

Thank you for the ''more than useful'' information. Comparing to the examples that you mentioned my case (building installation) is far simpler and I definitely believe that the unifi device will solve my problem. I am thinking that the installation of Unifi will give one more advantage, the reduction of devices and cabling installation plus less interference. 
Thats for now,
In case you need any travel information regarding the country just write to me. :cool:

Take care Fu!

---

