---
title: "Long distance wi-fi"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by funkyade on 2006-11-10
Hi,

Wondering if anybody has experience of connecting up two neighbouring installations approximately 500m apart via wi-fi or similar, so they can be on the same network, sharing resources etc...? The two sites to be connected are in a rural area with a few trees in between, one is at the top of a small incline the other is at the bottom of it, with dirt track connecting them.

OS will be ubuntu, what hardware (network cards, cabling, routers and so on) would anybody advise.

Is the distance too great?

Has anybody done this kind of thing before?

Any suggestions appreciated - am also googling extensively.

thx :-k

---

### Post by zgornel on 2006-11-10
This distance is not too big for classical 802.11 A/B/G. provided that you have a powerfull antenna.

---

### Post by skate1 on 2006-11-10
As the previous poster noted.  500M is probably too far for the standard antennas that come with an access point and client card.

You will need a set of directional antennas (and of course an access point and client card that can connect to the antenna).

[http://www.netgear.com/Products/AntennasandAccessories/OutdoorAntennas/ANT24D18v2.aspx](http://www.netgear.com/Products/AntennasandAccessories/OutdoorAntennas/ANT24D18v2.aspx)

---

### Post by Rhubarb on 2006-11-10
Or you can use a dish at either end.  D-Link makes them (or you can use an old satellite dish if you want to get your hands dirty).
[http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVUDLYZU93ygJVYLelXSNvhLPG3yV3oWYt/kP98f8p8Nqtm6jQ6VHqqnHtB84gJFNbu1avnJkwQuQ==](http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVUDLYZU93ygJVYLelXSNvhLPG3yV3oWYt/kP98f8p8Nqtm6jQ6VHqqnHtB84gJFNbu1avnJkwQuQ==)

It's should be able to to 500m at 48 or 54 MBPS no problems at all.
(A mate of mine setup 2 satellite dishes ~ 400m apart with excellent signal quality, and a few trees in the way).

---

### Post by esaym on 2006-11-10
I think the world record is like 30 miles with "legal" transmit powers or something like that ??

---

### Post by funkyade on 2006-11-11
Thanks folks.

Have found a few pieces of kit by Belkin and something called AirBridge. Belkin do a wireless router that has a range of 1500ft (500m) that may just do it, although I don't fancy working at the very limits of its range, however, in terms of cost it is a tenth of the 'pro' stuff. You get what you pay for though!

I was thinking of trying one of the Belkin devices at each end as the cost is neglible (in comparison) and their ranges will overlap. If it's a no-go then I think it may be the mini-dishes already mentioned...

Thanks again.

---

### Post by FrodoB on 2006-11-11
Great site with the information you need:

[http://www.seattlewireless.net/AntennaHowTo](http://www.seattlewireless.net/AntennaHowTo)

---

### Post by zgornel on 2006-11-13
> **FrodoB said:**
> Great site with the information you need:

[http://www.seattlewireless.net/AntennaHowTo](http://www.seattlewireless.net/AntennaHowTo)

Great site indeed.

---

### Post by Peepsalot on 2006-11-13
check this out, it's an open source firmware replacement for certain models of routers.
[http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F)

I'd recommend getting on of the compatible ones listed, and the firmware allows you to increase the output power.  Just be careful not to melt it ;)

I wonder if anyone has modded a watercooled router yet? :twisted:

[quote=The dd-wrt FAQ]
How can I increase my wireless range?

Many factors affect your range. What method you use to extend your range will depend on whether you are trying to increase the range inside a building or outside. Read the next two FAQ's below.

Consider getting a good antenna and try setting up your wireless devices with a clear line of sight. Best range is achieved by using one directional parabolic dish or yagi antenna and then disabling the other antenna on your router. For situations where you need omni-directional distance instead of directional linking, be sure to use a good omni-directional antenna and mount it high enough to broadcast signal in the are of focus. This is often 20 to 50 feet high, depending on the rated signal downturn of the the antenna.

Also, try increasing your router's transmit power to 84 mW (unless you have a Buffalo with a built-in amplifier). DD-WRT also has settings for frame burst and afterburner. You may see an increase in range by turning these off. If you are mostly interested in Internet access then 802.11b (as opposed to 802.11g) has longer range and may actually give you faster Internet speeds in longe-range, low-signal situations. (Be aware that you cannot use "802.11b Only" mode with WDS. If you're using WDS and WPA encryption, you must use "802.11g Only" mode.)

How can I increase range indoors?

Some buildings do not allow your signal to pass through very well. The usual reason for this is foil-clad plasterboard or insulation. In an effort to insulate buildings and keep heat in, new plasterboard is foil clad to reflect infrared energy back into the room. However this means you effectively have huge metal sheets stopping all radio waves, so mobile phones, baby monitors, audio radios, and WiFi will all have problems with signal. Doors and windows usually allow wireless to pass through nearly unaffected, so positioning your antennas so the signal lines up through these openings will help. Also, you need to consider using a proper CAT5 cable between the points since the speed and reliablility of this is far better. If you need wireless coverage, consider using more than one Access Point but wire them with network cable rather than attempting WDS repeater mode. Also, the WRT54G has a number of excellent 9db and 12db RP-TNC antennas available on eBay.

How can I increase range outdoors?

The most important thing for making your signal go far outside is HEIGHT! The higher in the building you position your radio the further it's signal will travel. Even a standard indoor unit with standard antennas can be used from 600m away! To go further you need to start using better antennas, the Access Point would work well with a 7db mounted just above roof hight, this will give you a good 600m to 1500m, it goes further in open areas and less far in built up areas. It's important to match the gain and height of your antenna to how far away you wish to recieve your signal. You may end up picking up signals that you would be better off not being able to see. Also the use of too much height with a 12db antenna would mean your signal does not reall come back to ground level for several km past where you wish to use it. The effect of this is that it seems your signal is weak and does not go very far. This is an illusion, the signal could be going way over your head. A lesser gain antenna at a lower height would yield a far stronger local signal and immunity for interferance from far away stray signals. 
[/quote]

The site has it's own forums too, which I'm sure are helpful.

---

### Post by funkyade on 2006-11-14
> I wonder if anyone has modded a watercooled router yet? LOL.

Both those links are extremely helpful. Thank you very much!

Now it's time to open my toolbox...

---

### Post by mimsmall on 2007-03-28
These prices seem reasonable. Linux drivers included.
[http://www.radiolabs.com/products/wireless/antennas/2.4gig/long-range-wifi-kit.php](http://www.radiolabs.com/products/wireless/antennas/2.4gig/long-range-wifi-kit.php)

---

