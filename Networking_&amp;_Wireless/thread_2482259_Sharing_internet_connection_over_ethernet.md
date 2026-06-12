---
title: "Sharing internet connection over ethernet"
date: 2022-12-26
forum: Networking &amp; Wireless
---

### Post by timswait on 2022-12-26
I'm afraid, I'm not sure of the terminology for what I'm trying to do, but basically it's to make my ubuntu system look like a router to something plugged into the ethernet port. I have Ubuntu installed on a Raspberry Pi4, it's on a boat, used for various things including I want to watch TV with it. I have an HD Homerun device that will stream TV across a network. Normally you would plug the HD Homerun into your router, you'd also plug the Raspberry Pi into the router and then you could watch TV on the Raspberry Pi (or on anything else on the router network). However, as I'm on a boat I don't have a router or a network. I use my mobile phone hotspot for internet. So the Raspberry Pi can connect to the internet through WiFi from the phone, I can plug the HD Homerun into the Pi with an Ethernet cable, but the Homerun can't connect to the Internet through it and I can't access it from the Pi. So is there some way I can configure Ubuntu to make the Ethernet port look like a router to the HD Homerun, so give it a network to connect to (also accessible through the Pi), assign it an IP address and so on?

---

### Post by TheFu on 2022-12-28
There are lots of things a raspberry pi can do and it great at.  Then there are millions of things they really shouldn't be used to accomplish.  In a home environment, I'd have a clear stance on this.  The router needs to be a stand-alone device, doing nothing except routing and firewalling.  Nothing else.  Every network with more than 1 device **needs** a router.  So, if you are going to treat your r-pi as a router, then you'll need to setup it up as a router and get another NIC into it (or multiple NICs) or at least a dumb switch for the other wired devices to connect into.

You'll also use the phone as a modem.
```

Internet
&#9492;&#9472;&#9472; Modem
    &#9492;&#9472;&#9472; Router-Pi
        &#9492;&#9472;&#9472; HDHR

```
It is poor security to run stuff on the router, but don't most cellular networks do "carrier NAT" connections to the internet?
[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) is a how-to guide for this.  Since it is from 2016, details  have changed, but the big ideas are the same.

I don't think you actually need a router, BTW.  If the Pi and HDHR are directly connected, usually on the 169.x.x.x subnet, then you can manually setup a route from the Pi to the HDHR to access the streams.  Might be easier to setup DHCP on the pi to give the HDHR an IP, subnet, netmask and default gateway which would be to the Pi, however.

Networking isn't hard, but there isn't 1 agreed minimum for what that means.  To me, having an IP and netmask is "networking", but that won't allow lots of things that most people (including me) need that are separate, but important to make a network usable.
* DNS
* Default Route to the internet
are sorta key items.  Some might add that DHCP to provide clients with IPs, netmarks, default gateway, DNS are all needed.  They aren't, but it is expected by many people.

So, you'll need to decide which if those things you need, which you want and which are just too much hassle.
BTW, I don't think you need any internet for HDHR to work.  Mine work fine when the internet is down.  You can watch specific channels or even record specific channels using the HDHR REST interfaces.

To watch TV on channel 2.1, I use:
```
$ mpv http://hdhr5/auto/v2.1
```
or 
```
$ mpv http://172.22.22.25/auto/v2.1
```
if you don't have DNS working or didn't update the client /etc/hosts file. My hdhr5 is at 172.22.22.25.
The same URLs can be used with curl or wget to save the stream to a file for a specific period of time.  I use 'timeout' to control the length, but HDHR has a length option too that I didn't know about when I was creating my tv-record script. Recording in my script looks like this:
```
$TIMEOUT --preserve-status ${DUR}m $WGET -O "$OUTDIR/$TITLE-$DATE-$CH.ts"  $URL1$CH
```
with the different bash variables setup earlier in the script.
```
timeout --preserve-status 61m wget -O /Recordings/Murry-today.ts http://172.22.22.25/auto/v46.1
```
and I use 'at' to run the command at the specific time to start the recording.  Of course, Jellyfin can be used too.  I've never gotten the HDHomerun software on android to record anything and newer versions don't even allow watching TV.

---

### Post by timswait on 2022-12-28
Thank you for all you help on this. Actually I think it was actually working all along, I didn't really need to do anything. The problem was that I kept trying to see if it was connected or not by going to [http://hdhomerun.local](http://hdhomerun.local) in a browser. When I tried it out on a wired network then I could see it and do things like updating the firmware through the browser. However when I directly connected it to the RPi then I was getting a server not found error going to that address, so I assumed it wasn't connecting. However it turns out it was automatically getting a 169.254... address and when I did run the hdhomerun_config discover then it turned out it was finding the device fine. I guess this [http://hdhomerun.local](http://hdhomerun.local) just doesn't work in direct connection mode.
So basically, I was just being a numpty :blush:. It's now scanning for and finding channels, so it looks like I'm in business.  :D

---

### Post by TheFu on 2022-12-28
hdhomerun.local is using a protocol, "Zeroconf", that I don't use.  
On Ubuntu computers, it is usually provided by the "avahi" service.
That might be helpful for people who don't use normal networking.

[https://en.wikipedia.org/wiki/Zeroconf](https://en.wikipedia.org/wiki/Zeroconf)

WS-Discovery and mDNS are other related terms you may see.

---

