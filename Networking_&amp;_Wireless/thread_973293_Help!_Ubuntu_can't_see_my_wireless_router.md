---
title: "Help! Ubuntu can't see my wireless router"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by majeka on 2008-11-06
Hi there everyone,

1st off, I'm a semi-newbie so please be semi-gentle! 2nd, as this is my first ever post I'd like to say thanks to all those who help people out on this forum - I've benefitted several times from posts on here. Keep up the good work!

So, on with my question... 

I've just bought a Dell Studio and am trying to get Ubuntu (8.10) working on it. I've also just had Tiscali broadband put in: our router is a "Siemens Gigaset SE587 WLAN dsl" (at least that's what it says on it). The problem is I can't get ubuntu to see the router (wirelessly). It DOES connect, through that same router, with a wired connection. 

Through the wired connection I've installed and then tried (as in, wirelessly, with the cable removed) every available network manager that I can search for in the "add/remove programs", along with WICD (another, similar, program that I saw recommended in another post). The weird thing about all this is that these network managers CAN see other peoples' routers in my area. Quite a few other ones come up, but mine doesn't. I've tried entering all manner of things into the "connect to a hidden network" option, but all to no avail. There is a WAP key for the router, which I've been entering (although I've also tried each of the other encryption types, out of desperation). 

I still have ubuntu (7.10) on my old laptop and that saw my router straight away and connected no problem. I also have Windows Vista on this same laptop (the new one, with the problem) and that connects fine (in case that's relevant). 

I'm not sure what else to say (and hope I haven't wittered on too much) - I've tried googling for quite a while but no luck. I would really appreciate some help!

Thanks

---

### Post by Haans74 on 2008-11-07
I have the same problem. My setup is a Lenovo 3000 N200 (Intel 4965 wireless). I can connect to my wireless network at home (hidden, WPA2-PSK), guest-network at work (broadcast on, WPA2-PSK), I can see several ad-hoc networks broadcasted by other laptops in the vicinity, but the one wireless network I usually connect to at work (broadcast on, WEP) is not there. It worked from my previous Vista install on the same laptop, it's there in the XP-install on my work laptop, but nowhere to be found using Kubuntu 8.10.

I've tried adding it manually, both in Knetwork Manager and using the terminal, but no luck. It's driving me crazy. For a moment I thought it might be defaulting to the n-protocol, but my network at home is b/g, just like the network I can't find. Driving me bonkers!

---

### Post by brenbart on 2009-02-24
I realize this is not especially helpful but I have the exact same problem.

I have two hard drives for my Dell Latitude laptop, one with Ubuntu 7.10 (Gutsy Gibbon) and one with 8.10 (Intrepid Ibex).  The 7.10 install sees and can connect to a wireless router that is 20 ft away without a problem. The 8.10 version doesn't see it at all.

I also have installed a variety of wireless managers on my 8.10 drive and attempted to manually configure the connection without success.  If I put the 7.10 drive back in it sees it immediately.

I'm wondering if it's a driver issue...  It's been a year or so since I installed the 7.10 version and don't remember now if I had to install different drivers or not.

---

### Post by DerHesse on 2009-02-24
Maybe you cna check the brodcast channel the Accesspoint uses. As far as I know you should use Channels 1-10, but not above since 8.10.
 
Channels above 10 are not legal to use in USA, so maybe newer drivers may not even offer it? Is it politically correct to act like this? I don't think so. ;)

---

### Post by Venlaar on 2009-02-26
I am also having this issue. I have a Sony Vaio VGN-FZ180E with the Intel/Pro Wireless 4965 card. I just installed Intrepid 8.10 as dual boot with Vista. When I tried to connect to my WPA encripted network with Intrepid it never fully connects. I can connect fine when booting up in Vista on the same laptop. At one point after my initial boot and inability to connect to my secured network with Intrepid I tried to connect to a neighbor's unsecured network and was able to with no problem. After a reboot however I began having the same problem with it too. I found a post that suggested blacklisting IPv6 and I followed that. I can now connect again to the unsecured network but still cannot connect to my secured wireless router. From what I saw in the syslog the connection is getting associated and then disassociates with "reason 3". From other posts it looks like there are many having this problem. I am hoping that someone finds a solution soon.

---

### Post by CazperII on 2009-02-28
I also have a Lenovo n200 with the Intel 4965 wireless card. I ran into the same problem a while ago when I updated my router's firmware. My other laptop running XP could see the ssid of the Wifi network, but my Ubuntu laptop couldn't see it. 

Checking my router, it used channel 13 for the wireless network (the router changes it automatically to the channel with least interference). So I changed it manually to channel 1. Now the ssid showed up in Networkmanager. I connected, reconfigured the router to assign the channel dynamically and now Networkmanager can connect every time.

I think it's indeed a bug in either network manager or the Intel wifi driver. The bug is that not all the channels are scanned.

---

### Post by Ben Crisford on 2009-03-02
Same problem again ;).

My adapter is inbuilt and it won't find the network (and it definately works in windows).  I haven't tried wired, because my computer is so far from the router :(.

---

