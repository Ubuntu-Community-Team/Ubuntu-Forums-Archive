---
title: "Wireless problems in 8.04 - a possible cause?"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by yello_ubu on 2008-07-19
I'm new to Ubuntu so forgive me if I use the wrong terms etc.

My wireless connection using out-of-the-box 8.04 and a Netgear WG511T card disappeared at some stage in the last few weeks. I don't know why or when as I run wired. 

I only discovered it because I tried putting Ubuntu on my wife's Acer Aspire laptop... but I was darned if I could get wireless (Broadcom BCM94311MCG) working on it. I searched and tried; fw-cutter, ndiswrapper, etc etc etc... NOTHING worked and, believe me, I tried everything I could find on forums. With all installations (ndiswrapper, fw-cutter), I got to a point were everything looked good, as though it should work... but I could never see a network (sudo iwlist scan).

As a part of the problem diagnosis, I put the tried and trusted WG511T card in the wife's laptop, configured it up... but that didn't work. So I tried it in my laptop and it didin't work there either... despite it doing so around a month ago. Again, everything looks okay configuration wise but it just doesn't see the network.

So I'd been starting to look at my router (Netgear FWG114P) in conjunction with some other wireless tools. KWiFi displayed the channel and frequency... this made me try another approach. I tried some other channels on the router. I live in France so my router region was set to French. No French channel worked... 

BUT...

...I change the router to the 'Europe' region and bingo (viola!), the network is found and I can log on!!

SO...

Is there any chance that some 'regionalisation' has gone on recently?

My repositories are all set to French sites and I run Ubuntu in English. Is there something somewhere that restricts the wireless frequencies scanned? 

Note, the WG511T card works fine on the 'France' or 'Europe' regions when in the wife's laptop running Vista. I also have an Asus Eee 701 running Ubuntu, and that also logs on wireless to the network.

Sorry if I'm way off the mark, but there is definitely something region based going on, either in my set up or in recent Ubuntu updates.

---

### Post by phantomjoker on 2008-07-19
ok - search in synaptic for 'network common'

there should be a folder of common network drivers... give this a go.

---

### Post by ugm6hr on 2008-07-19
> ...I change the router to the 'Europe' region and bingo (viola!), the network is found and I can log on!!

I never knew there were specific regions for broadcast frequencies.  Most routers merely have channels 1-12, although some may be technically illegal in your country.

I believe any one channel not working is usually due to a neighbouring wifi broadcasting on a similar channel.  Can't explain why it would work on Vista, but not Ubuntu, unless this is a wifi range issue.

---

### Post by yello_ubu on 2008-07-20
> **phantomjoker said:**
> ok - search in synaptic for 'network common'

Okay, I'll give this a go and see what happens.

> **ugm6hr said:**
> I never knew there were specific regions for broadcast frequencies.  Most routers merely have channels 1-12, although some may be technically illegal in your country.

I'd always assumed that, like cordless phones etc, certain frequencies are prohibited because they're used by emergency services or air traffic control or whatever. It seemed natural enough to me that this would vary country by country.

The 3 channels I have on the 'French' setting on my Netgear router are;

11 - 2.462GHz
12 - 2.467GHz
13 - 2.472Ghz

There are 13 channels in the 'Europe' setting; 2.412GHz to 2.472GHz (so 11, 12 & 13 overlap). 

I established a connection on channel 2 2.417GHz. There are no other wireless devices around here and my laptop sits right next to the router (hence me running wired!).

---

