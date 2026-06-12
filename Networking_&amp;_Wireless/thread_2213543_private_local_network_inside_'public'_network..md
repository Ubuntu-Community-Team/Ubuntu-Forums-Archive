---
title: "private local network inside 'public' network."
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2014-03-27
Hi All,

I have a question about how to create a 'private network' inside another already existing network.

My situation is as follows.

I'm starting a new business and I'm going to a trade show.

The show organisers do not allow extra wifi networks without a license (read V. Expensive).

My colleagues and I only realy need a single internet connection. 

My intention is to use a single pc that will act as a print server, and 'local' web server (for collection / storage of new potential clients, etc). This I can set up easily.

But my question is how to connect the other devices to this one in a 'secure' manner.

The other devices are a collection of Android and iPad.

At first I figured I could share the connection over bluetooth, but the android tablets don't allow reverse tethering via their bluetooth adapters (shame as this seemed like a very nice solution, and would probably work).

Next I think about a wifi hotspot on the main server pc, and my research tells me it is like a wifi router, so although this will most likely work, the organisers don't allow it
> 
The use of Wireless Routers/Wireless Access Points is strictly prohibited ...

which seems a bit ridiculous.
I spoke to the organisers and they said something about the extra wifi networks causing potential problems with the signal and connectivity, which seems far fetched to me.
I intend to go to another show at earls court later in the year and apparently they charge £100 per day per connection to wifi (sounds like a cause for trade standards to me ;).

So I now thinking of a VPN type setup.

Which would be as follows.

Main server pc, plugged into a wifi router (for connecting to the main wifi network), or with a wifi adapter. ~ I don't want to use a 'hardwired connection as the price is ridiculous (£250 install, £30 per day).

The tablets all have wifi.

All devices will obtain an IP address from the organisers DHCP server.

I want to create a small personal network with just these devices in, that is secure and hidden.

Here are some possible solutions I have considered.

I've just thought that maybee I should install 'own cloud' on my server. Will it be able to provide most of what I require ?

Should I just go with a wifi router, and hide it in a cupboard, and hope the IT staff aren't that clever, and hide the ssid of my network?

If I do use a 'wifi hotspot' to tether my devices to my server (so the server acts like a router), can I claim that technically it is diferent to a 'wifi router' and hence thier IT don't know what they are up to? Or claim that they are actually connecting via a reverse tether over bluetooth.

What do the IT industry do when they go to a exhibition ? I guess they have some very clever wheeze (and don't stand for the 'extra wifi routers interfere with our network' which to me seems nonsense.)

Your thoughts and help are much appreciated.

David.

---

### Post by Lars Noodén on 2014-03-27
The second option is not possible: you can't hide a wifi net and, especially on the 2.4 GHz  band, you [will cause interference and there will be enough of that](http://blogs.aerohive.com/blog/the-wireless-lan-training-blog/wifi-back-to-basics-24-ghz-channel-planning) as it is with mice, keyboards and other wireless devices.  Hopefully they will use the 5GHz band instead as there are more channels and less overlap of frequencies.

I would go with the first option, the VPN, but it will be slow and shaky since the base is wifi.

---

### Post by theDaveTheRave on 2014-03-27
@lars noden.

Thanks for the interesting blog link.

Makes for good reading, and I can now ask more sensible question when I contact the wifi provider.

I don't know exactly how they work their AP's, it may be that I can ask for a dedicated network name, so my problems will not be so bad.

I must admit I have looked into the VPN, and it seems alittle bit daunting to set up.

David

---

