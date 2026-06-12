---
title: "Blocking Samsung's TV firmware update domains"
date: 2023-04-10
forum: Networking &amp; Wireless
---

### Post by vidtek on 2023-04-10
I have recently moved from my BT copper broadband to Virgin fibre.

The BT router has been sent back to BT.  It had an easily configurable firmware which allowed the blocking of selected domains to a chosen IP address on my home network.

The virgin modem is a dreadful piece of kit, it's wireless is next to useless, and it has a very basic interface, with no domain blocking facility.  I configured it to act as a modem only.

I dragged out an old modem/router I had lying around the workshop, an old Post Office labelled VMG3925-B10C.   The wireless is ten times better on both bands than the new Virgin router but I cannot work out how to block domains on it.

These are the domains I wish to block:

otn.*\.samsungcloudcdn\.com$
.*samsungotn\.net$
*.msecnd.net
*.samsungotn.net
*.samsungcloudsolution.net
*.samsungcloudcdn.com 

Anyone got some ideas?

Cheers Tony.

---

### Post by #&amp;thj^% on 2023-04-10
Tony have you tried looking here, (It's been sometime now since I've used one) you want to block specific websites navigate to  "Childsafe" via your Virgin Media login and you can block categories of websites as well as specify individual address's to block.

---

### Post by vidtek on 2023-04-10
@ifallen - Thanks for this suggestion-just tried it but it does not recognise any of them as valid addresses.  I may have to remove the wildcards and list each and every one.  May take some time though.

Cheers Tony

---

### Post by #&amp;thj^% on 2023-04-10
Tony see if they have cheat sheet for those domains.
It makes me very happy on Desktops/Severs we have "/etc/hosts", my block list there is far too long to post here.
Never mind I found one, please go through them carefully: [https://raw.githubusercontent.com/Perflyst/PiHoleBlocklist/master/SmartTV.txt](https://raw.githubusercontent.com/Perflyst/PiHoleBlocklist/master/SmartTV.txt)

---

### Post by vidtek on 2023-04-11
@1fallen 
Thanks again for this.  I will snoop on each one as the tv tries to auto-update and see which are relevant.   Samsung are so sneaky with this.   They build-in so many crappy apps that I just use it basically as a monitor for my linux box, the apps and menu system make it a real pain to even get off-air tv - the basic function of a tv.  To get off-air tv is about 8 menus deep and multiple button presses.
The WAF is zero since I bought this-she goes into the bedroom to watch tv now when I'm not around, she can't work it out poor dear.

---

### Post by TheFu on 2023-04-11
**pi-hole** is designed specifically to do this.  [https://pi-hole.net/](https://pi-hole.net/) 
I run a pair in LXD containers under Ubuntu on x86-64 systems (AMD Ryzens). If you have an old Raspberry Pi laying around, that can do it.

Using an old router is usually a terrible security failure. All versions of the Wifi standards from wifi-6 all the way back to 802.11b have security flaws that are easy to access.  Never trust wifi.  The oldest wifi that might still be getting patched for all the known security problems would be wifi-5 (802.11ac).

The wifi alliance has been trying to simplify their marketing ... sadly, they've failed and added more confusion, sorta like how the USB guys have screwed their marketing.  [https://www.howtogeek.com/853833/wi-fi-5-vs-wi-fi-6/](https://www.howtogeek.com/853833/wi-fi-5-vs-wi-fi-6/) tries to explain.

For wifi routers/access points(APs), I'd only consider these brands:
[LIST]
[*]Asus
[*]Ubiquiti
[*]Mikrotik
[*]Netgear (sometimes, but usually far to expensive for the capabilities)
[*]Home built router running OPNSense without any wifi capabilities  <--- mine
[/LIST]
Asus for non-technical home users.
Ubiquiti for nerds that want full control over their APs
Mikrotik for nerds that like all-in-one. Typically installed by experts.

I've used all of these.  Currently using a PCEngines AMD64 APU2 routing device. It gets updates about every 2 weeks from the OPNSense team. I bought the device around 2015 and expect to get at least another 5 yrs of service from it. It will have maintenance patches all this time.  Not bad for $140 all in and providing enterprise capabilities.

For most home users, Asus is the cheap, easy, answer. Look at the $80 wifi-5 routers.  Don't get caught up in their $150-$400 offers. 99% of us don't need that.  Asus provides best-in-class patching thanks to a lawsuit they lost brought by the FTC. They have about 15 yrs more of FTC mandated monitoring.  I'm not a fan of big govt and the FTC has done many terrible things, but this is 1 situation where a company was caught with highly deceptive and harmful practices which has completely turned around a specific business area (network equipment).

Consumer routers lose security update support after about 5 yrs, best case.  So, replacing a consumer router every 5 yrs should be expected.  Or get off that treadmill and built your own APU2 (or something similar), install OPNSense, learn to use it and know that like pfSense, it will have support for decades.

---

### Post by vidtek on 2023-04-11
> **TheFu said:**
> **pi-hole** is designed specifically to do this.  [https://pi-hole.net/](https://pi-hole.net/) 
I run a pair in LXD containers under Ubuntu on x86-64 systems (AMD Ryzens). If you have an old Raspberry Pi laying around, that can do it.

Using an old router is usually a terrible security failure. All versions of the Wifi standards from wifi-6 all the way back to 802.11b have security flaws that are easy to access.  Never trust wifi.  The oldest wifi that might still be getting patched for all the known security problems would be wifi-5 (802.11ac).

The wifi alliance has been trying to simplify their marketing ... sadly, they've failed and added more confusion, sorta like how the USB guys have screwed their marketing.  [https://www.howtogeek.com/853833/wi-fi-5-vs-wi-fi-6/](https://www.howtogeek.com/853833/wi-fi-5-vs-wi-fi-6/) tries to explain.

For wifi routers/access points(APs), I'd only consider these brands:
[LIST]
[*]Asus
[*]Ubiquiti
[*]Mikrotik
[*]Netgear (sometimes, but usually far to expensive for the capabilities)
[*]Home built router running OPNSense without any wifi capabilities  <--- mine
[/LIST]
Asus for non-technical home users.
Ubiquiti for nerds that want full control over their APs
Mikrotik for nerds that like all-in-one. Typically installed by experts.

I've used all of these.  Currently using a PCEngines AMD64 APU2 routing device. It gets updates about every 2 weeks from the OPNSense team. I bought the device around 2015 and expect to get at least another 5 yrs of service from it. It will have maintenance patches all this time.  Not bad for $140 all in and providing enterprise capabilities.

For most home users, Asus is the cheap, easy, answer. Look at the $80 wifi-5 routers.  Don't get caught up in their $150-$400 offers. 99% of us don't need that.  Asus provides best-in-class patching thanks to a lawsuit they lost brought by the FTC. They have about 15 yrs more of FTC mandated monitoring.  I'm not a fan of big govt and the FTC has done many terrible things, but this is 1 situation where a company was caught with highly deceptive and harmful practices which has completely turned around a specific business area (network equipment).

Consumer routers lose security update support after about 5 yrs, best case.  So, replacing a consumer router every 5 yrs should be expected.  Or get off that treadmill and built your own APU2 (or something similar), install OPNSense, learn to use it and know that like pfSense, it will have support for decades.
@TheFu
In my mate's shed I found an old TP-Link Archer VR2800 router that will run open wrt so I may have a go at that.   I really don't want the hassle of using a dedicated pc or raspberry, there's enough junk next to my computer in the attic as is.   Also here in the UK our electricity costs have rocketed (read quadrupled) in the last year, my electric bill was almost £7,000 for my house in 2022 (big house - small family), so not too keen on adding more permanently powered up stuff.   I haven't wrestled with pi-hole yet, it looks promising.  
As far as wireless security is concerned, my wi-fi doesn't extend to the road, and the nearest property is well beyond wi-fi range.  I use no security at all and have never had a problem, I may as well live on a farm in the country. 
   
Thank you for the time and effort you have put in to assist me, it is very much appreciated.

Cheers Tony.

---

### Post by #&amp;thj^% on 2023-04-11
> **TheFu said:**
> 
Consumer routers lose security update support after about 5 yrs, best case.  So, replacing a consumer router every 5 yrs should be expected.  **_Or get off that treadmill and built your own APU2 (or something similar), install OPNSense,_** learn to use it and know that like pfSense, it will have support for decades.

The only way to surf...
I'm glad you always bring this to the forefront, I just go along with what the OP asked for help with. (makes it easier, not better but easier )

---

### Post by TheFu on 2023-04-11
Beware that wifi can reach 20 miles with a good antenna. 10 miles with the other guy having a good antenna.  If you were hacked, I doubt you know it.

A raspberry pi is 10W, peak. If you can find a r-pi v2, you'll be all set to run a pihole DNS filter.  Of course, if you leave 1 of your more powerful computers on all the time, running a pihole inside an LXD container is pretty easy. You'll have a DNS for your LAN too, if you like.

I understand power costs going up.  Since 2014, I've been specifically replacing any system that used over 65W of power with a lower power alternative AND consolidating services into just 2 computers (I need redundancy).  I didn't really expect the power bill to show anything, but it has.  A new Ryzen 5xxx system paid for itself in power savings in less than 2 yrs.  It worked so well, that I replaced another system.  The power bills are like they were 15 yrs ago here ... and about 50% less for what most people in similar homes pay here just by adding a little insulation, calking gaps to the outside, raising the A/C thermostat in summer 2°F and lowering it in winter 2°F.


About 25% of my home is missing insulation since Xmas due to some burst water pipes.  It is amazing how long it takes to get people at any price to show up and fix things.  In theory, by next week, that will all be fixed. It was supposed to be handled last week. Sigh.  Fortunately, insurance pays for higher living costs until repairs are completed.  I'd never have thought that insulation in a single wall and over the garage would have made so much difference to the entire house heating.

---

### Post by Tadaen_Sylvermane on 2023-04-11
I have to ask. Why are firmware updates for a tv a bad thing? Why are you trying to block them in the first place? They can typically only help things. Maybe I missed this in the thread. Updates are rarely a bad thing...

---

### Post by #&amp;thj^% on 2023-04-11
> **Tadaen_Sylvermane said:**
> I have to ask. Why are firmware updates for a tv a bad thing? Why are you trying to block them in the first place? 

In my case my TV (samsung) was hacked during an upgrade, and have since placed it on a managed switch, that I now control.
Samsung sent me e-mail saying they are monitoring my account for any fraud, but I'll do my own firmware upgrades myself from now on. 
TheFu has mentioned this several times now here in UF. (Phone's too)

---

### Post by vidtek on 2023-04-11
> **TheFu said:**
> Beware that wifi can reach 20 miles with a good antenna. 10 miles with the other guy having a good antenna.  If you were hacked, I doubt you know it.

A raspberry pi is 10W, peak. If you can find a r-pi v2, you'll be all set to run a pihole DNS filter.  Of course, if you leave 1 of your more powerful computers on all the time, running a pihole inside an LXD container is pretty easy. You'll have a DNS for your LAN too, if you like.

I understand power costs going up.  Since 2014, I've been specifically replacing any system that used over 65W of power with a lower power alternative AND consolidating services into just 2 computers (I need redundancy).  I didn't really expect the power bill to show anything, but it has.  A new Ryzen 5xxx system paid for itself in power savings in less than 2 yrs.  It worked so well, that I replaced another system.  The power bills are like they were 15 yrs ago here ... and about 50% less for what most people in similar homes pay here just by adding a little insulation, calking gaps to the outside, raising the A/C thermostat in summer 2°F and lowering it in winter 2°F.


About 25% of my home is missing insulation since Xmas due to some burst water pipes.  It is amazing how long it takes to get people at any price to show up and fix things.  In theory, by next week, that will all be fixed. It was supposed to be handled last week. Sigh.  Fortunately, insurance pays for higher living costs until repairs are completed.  I'd never have thought that insulation in a single wall and over the garage would have made so much difference to the entire house heating.

I feel your pain.  Since brexit a great many of the Eastern European skilled workforce have repatriated and we now have bricklayers earning £250,000 a year.   Getting plumbers and sparkies is pot luck and wait and wait....

As a tv engineer I am aware of electromagnetic propagation and know there is no danger for my installation.

---

### Post by TheFu on 2023-04-11
> **Tadaen_Sylvermane said:**
> I have to ask. Why are firmware updates for a tv a bad thing? Why are you trying to block them in the first place? They can typically only help things. Maybe I missed this in the thread. Updates are rarely a bad thing...

More and more IoT updates are done to monitize the TV customer.  If a TV is connected to any network, it is likely to be phoning home and reporting what is being watched and listened to.  Even if you only use your own media, not broadcast or purchased commercial optical media, they do fingerprinting and send the finger print to the mothership.  Do you really want to be more product being sold?

[LIST]
[*][https://www.nextgov.com/emerging-tech/2022/03/smart-devices-spy-you2-computer-scientists-explain-how-internet-things-can-violate-your-privacy/363107/](https://www.nextgov.com/emerging-tech/2022/03/smart-devices-spy-you2-computer-scientists-explain-how-internet-things-can-violate-your-privacy/363107/)
[*][https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/](https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/)
[*][https://www.pcmag.com/how-to/how-to-stop-smart-tvs-from-snooping-on-you](https://www.pcmag.com/how-to/how-to-stop-smart-tvs-from-snooping-on-you)
[*][https://www.theverge.com/2021/11/10/22773073/vizio-acr-advertising-inscape-data-privacy-q3-2021](https://www.theverge.com/2021/11/10/22773073/vizio-acr-advertising-inscape-data-privacy-q3-2021)
[/LIST]
I have other articles, but they've been moved behind paywalls.  Glad that I added them to Wallabag, so the articles can't be taken away.

Be careful using any IoT device, which includes any cell phone.

---

### Post by BBQdave on 2023-04-11
> **Tadaen_Sylvermane said:**
> I have to ask. Why are firmware updates for a tv a bad thing? Why are you trying to block them in the first place?

For me, it was a printer-copier that was "phoning home" for updates on my home network. It was exploited, and allowed access past router firewall and other security measures on my home network.

So family using Windows was under attack :(

There was no patch or solution provided by the copier manufacturer, so the copier was unplugged from the network. We use a USB stick to load files for print.

Fast forward a few years, and still have the copier-printer unplugged from the home network. But, I am happy with the security service with my current ISP, it actively scans the home network and shuts down suspicious activity - one being cell phone applications "phoning home" to suspect sites.

---

### Post by vidtek on 2023-04-12
> **TheFu said:**
> More and more IoT updates are done to monitize the TV customer.  If a TV is connected to any network, it is likely to be phoning home and reporting what is being watched and listened to.  Even if you only use your own media, not broadcast or purchased commercial optical media, they do fingerprinting and send the finger print to the mothership.  Do you really want to be more product being sold?

[LIST]
[*][https://www.nextgov.com/emerging-tech/2022/03/smart-devices-spy-you2-computer-scientists-explain-how-internet-things-can-violate-your-privacy/363107/](https://www.nextgov.com/emerging-tech/2022/03/smart-devices-spy-you2-computer-scientists-explain-how-internet-things-can-violate-your-privacy/363107/)
[*][https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/](https://www.nytimes.com/wirecutter/blog/data-harvesting-by-companies/)
[*][https://www.pcmag.com/how-to/how-to-stop-smart-tvs-from-snooping-on-you](https://www.pcmag.com/how-to/how-to-stop-smart-tvs-from-snooping-on-you)
[*][https://www.theverge.com/2021/11/10/22773073/vizio-acr-advertising-inscape-data-privacy-q3-2021](https://www.theverge.com/2021/11/10/22773073/vizio-acr-advertising-inscape-data-privacy-q3-2021)
[/LIST]
I have other articles, but they've been moved behind paywalls.  Glad that I added them to Wallabag, so the articles can't be taken away.

Be careful using any IoT device, which includes any cell phone.

Absolutely, agree 100%.

---

### Post by vidtek on 2023-04-12
The tv was absolutely flooding my network with calls to the mother ship.   I decided the safest and most effective way to counter this was to pull the RJ45 plug altogether.
Wow, what a reaction.  Every time I turn the set on it demands an internet connection emblazoned across the centre of the screen.  Samsung are desperate to milk their customers for every drop of personal information they can milk out of them.  The TV is beautiful, but I will never buy another Samsung product again.
Thanks again everyone for your input and comments, you have all been a great help.  Tony

---

### Post by #&amp;thj^% on 2023-04-12
> **vidtek said:**
> The tv was absolutely flooding my network with calls to the mother ship.   I decided the safest and most effective way to counter this was to pull the RJ45 plug altogether.
Wow, what a reaction.  Every time I turn the set on it demands an internet connection emblazoned across the centre of the screen.  Samsung are desperate to milk their customers for every drop of personal information they can milk out of them.  The TV is beautiful, but I will never buy another Samsung product again.
Thanks again everyone for your input and comments, you have all been a great help.  Tony
Well that will make 2 of us then, no more Samsung  Smart (I can't help but chuckle on the smart part) TV's
Yup pull the plug....

---

### Post by TheFu on 2023-04-13
> **1fallen said:**
> Well that will make 2 of us then, no more Samsung  Smart (I can't help but chuckle on the smart part) TV's
Yup pull the plug....

I stopped buying TVs around 2008. We switched to projectors.  65 inch screens seem so very tiny. ;)

---

### Post by vidtek on 2023-04-13
I've gone the other way.  I had a dedicated home theatre room in OZ but here in the UK I'm in a granny/grandad flat, so 55inch is the biggest I can fit and that was an uphill battle and involved lots of grovelling and many meals out for the lovely Jane !

---

### Post by SeijiSensei on 2023-04-13
Can your projector provide the same 4K detail that my 65" Hisense displays?

---

### Post by TheFu on 2023-04-13
> **SeijiSensei said:**
> Can your projector provide the same 4K detail that my 65" Hisense displays?

There are 4K HDR projectors.  If all your content is bluray, that could make sense. 
I've always considered BluRay to be broken by design and it is clear that 4k streaming services aren't really in 4k.

If you've never had a projector at home, it is hard to compare.  You just don't know.
But if you find yourself watching content in bright, direct, sun, then perhaps a projector isn't for you.  OTOH, if you can even slightly control the light in the viewing room, the experience can be good to great.  We have 2 windows in the bedroom. 1 has black out curtains over it and the other just has normal blinds.  It gets morning sun from 8-10am, that's it. We don't use the projector then, though it isn't bad with the blinds closed.

We have 4 projectors.  2 are small travel 720p models that were pretty cheap (Epson/Optoma). We started out with them and became addicted. Good for movies.
Have a full-size no-name Chinese, loud, 1080p projector that was $200.  It is bright and loud. All the Chinese projectors seem to be similar. Lasted about 16 months.  The company has disappeared, but the same projector is being sold on Amazon with 1 character different in the company and model name. I think they disappear every year as part of their business model.

And the main projector is a wonderful Epson.  No android TV.  No network.  It is connected to a raspberry pi to provide all content.

If you think you are getting 4K content from streaming or broadcast or CATV services, know that there is very little true 4k content. It is upscaled 1080p.  Local upscaling is really good these days.

---

### Post by #&amp;thj^% on 2023-04-13
> **TheFu said:**
> know that there is very little true 4k content. It is upscaled 1080p.  Local upscaling is really good these days.

Couldn't agree more, and upscaling gets better as time progress's.
The price to replace/availibilty those bulbs is a bit concerning though,

---

### Post by TheFu on 2023-04-13
> **1fallen said:**
> Couldn't agree more, and upscaling gets better as time progress's.
The price to replace/availibilty those bulbs is a bit concerning though,

The cost of consumables for any hardware is an issue.  As part of my purchase choice, I looked up the lamp life and how much it would cost to replace.  That was a key reason why I picked Epson over other brands.  3 of my 4 projectors don't use bulbs.  The expected lifetime is 30-50K hours.  That's usually over 10 yrs.

I stopped buying inkjets because the consumables were too expensive.

---

### Post by SeijiSensei on 2023-04-14
> **TheFu said:**
> If you think you are getting 4K content from streaming or broadcast or CATV services, know that there is very little true 4k content. It is upscaled 1080p.  Local upscaling is really good these days.
I've watched many 4K streams on my TV that aren't "upscaled 1080p." Our Planet on Netflix is one example. There's a degree of vibrancy and detail in many of the sequences in that show that are visible because of the increased resolution.

Some sporting events are telecast in 4K; the Red Sox outlet NESN just upgraded all its equipment to deliver native 4K streams for their games. They look distinctly better than 1080p, but the content doesn't really take advantage of the format. A pitcher looks more or less the same in either format. Many of the shows on Disney+ like The Mandalorian are in native 4K. The difference is clearly visible.

> **TheFu said:**
> I stopped buying inkjets because the consumables were too expensive.
Me, too, though I don't print all that much any more.

---

