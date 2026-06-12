---
title: "Options for maintaining connectivity when the power is cut?"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by jetsam on 2019-11-08
Right, so PG&E (Pacific Gas and Electric) in California has decided they can switch our power off when it seems like they might accidentally start a wildfire because they "forgot" to spend the money to maintain their power lines. 

I'm regrettably old school on this one.  Can anyone give me a hint about how to use a cellphone cheaply to maintain a decent, if not stellar, internet connection?  Can a cellphone be made to act as an AP for a desktop or laptop, even though the electricity, and along with it, the cable company and its cable modem, has gone dark?  Can you do it without paying for an expensive "tethering" plan?

Thanks in advance.

BTW: Hey all, been gone from the forums for a while...  Glad the forums still seem to thrive.

---

### Post by TheFu on 2019-11-08
Consider a "mifi" device, which connects using cell-data, but provides a local wifi AP for lots of clients. But it depends on which cellular data company works in your location if that is available. Google "MiFi Routers"

Cell towers cutoff from power will fail after a few hours too, just like cable data does.  They are tied back to the providers using fiber, just like other businesses.  If those lines fail, no data.

Have you considered a satellite-based internet connection?  The latency will be bad for now, Hughes is one of the providers.  SpaceX is claiming they will be a low-latency ISP in a few years.  I know the USGovt is excited about it, but they have deeper pockets than we do.

---

### Post by jetsam on 2019-11-08
Thanks for the tips.  It all seems (relatively) expensive for an individual.  My cell phone provider is too bare bones I think for mifi.  They had an option in 2015, but it's gone from their website now.

Hmmm.....  I suppose I could get a different provider.  Wait a second now...  here's a [video of Cathy being guided to use a ZTE mobile hotspot.]("https://www.youtube.com/watch?v=_NXOD4TKtro")

I think I'll have to talk to someone and see if they still offer this and how much it is.

Satellite sounds cool.  I hadn't even thought about it.  It's definitely something I'll keep an eye out for.   For the time being, I guess I'm stuck buying a HAM radio for emergency comms only (I'm not licensed-- at least not yet), and I'll just have to make do if the black outs come back.  A lot of "community charging points" popped up during the last blackout, and you could probably get wifi at some of them at least.  I'll rev up an old laptop for portable wifi.  I'll get a power bank or two, and that should be enough for now.

Thankfully, the cell towers didn't go out during our last black-out, which lasted 48-72 hours or so depending on where you were in the state.  A smart phone got us online during the second day, which helped maintain our (very small scale) internet sales without falling behind and taking a hit to our feedback.  Now there's a new APC UPS in the home office room so we'll be better off than we were, at least.  

Progress, not perfection...  

Cheers!

---

### Post by TheFu on 2019-11-08
UPS systems get really expensive if you want more than a few hours of uptime.  In a business, perhaps the right answer is to put up public/static data on a webhost with multiple discrete locations at least 500 miles apart.  This is a well-understood strategy.  With just public information, you could use CloudFlare CDN caching for free.
 
A whole house generator with 2K-5KW of continuous power might be a reasonable solution.  Solar and wind aren't too useful where I live, so people get natural gas or propane powered generators.  This can be hooked into house wiring with manual or automatic start for $5K.  

After Katrina, some of my family lived with a gasoline generator for 4 months. It was sized to run the fridge and a few small things like a laptop. Took 3 months for internet to be available nearby.  He was hosting a few non-profit websites from a business connection at home, but decided paying $5/month for a VPS in a real data center with redundant power, redundant networking, redundant storage, was a better deal.  Of course, he still makes daily backups. The non-profit pays those bills happily.

Cellular service is deemed critical by the telecoms, so that's the priority.  Power teams and telecom teams work to restore cell service first - well, after the local trauma center gets power and comms.  

If you have someone with a health issue that requires power and/or communications, then there are lists at the utilities so their service is also a slightly higher priority, at least in the US.

If all you need it a tiny charger for USB stuff, then there are fire-powered chargers that also boil water for around $120.  When we are in dense woods with no direct sunlight, we still need boiled water and having a way to charge a radio/gps/smartphone can be good.

I realize you are in California.  Any chance you'd move?  There are lots of wonderful places without all the issues that come with living there, including much lost costs of living and govts that don't over-regulate everything.  I've lived in 9 different states - there are nice places everywhere.  Really.

Of course, there are many, many, other considerations with redundant solutions and were we each live. ;)

---

### Post by uRock on 2019-11-08
I think cell providers are required by law in the US to have backup power, though their systems can be set with QoS to only allow 911 and emergency services to use them during the outage.

If I were living in the area you're in, then a backup generator may be a good investment. Without going into politics, PG&E's systems will likely get worse before the state gov takes it over and may never get better if the state doesn't do it right.

---

### Post by jetsam on 2019-11-08
:)  Sticking with sunny Cali for the time being...  I'm probably a lifer.  I've spent too long in the Northeast with their "snow" and "hurricanes" to want to leave this climate behind again.  

Who knows a decade hence?  I guess that's the question, really...

Katrina was something awful.  My Dad was part of a spontaneous amateur fundraiser in his pick-up neighborhood jazz band for Katrina.  They just went to the local supermarket and put out a hat.  I think they only got a few hundred, and then donated it to somewhere-- prob. the Red Cross, maybe some other NGO, I'm not sure.  

Man...  three months.  That's more than I would hold out for, I think.    PG&E says be ready for 5 days, which seems a stretch.

We're looking into solar.  It will take a while to get a full install, so I'm mostly just filling in around the edges for now.  We'll have some pretty good capacity if there's a new blackout within the year.  

I really like the UPS.  We're good for about 80 minutes of run time after the power goes, and it can recharge cell phones.  It's set to preserve battery power, so the attached computer gets shut down in 5 minutes, then we have 75 minutes of backup battery store for running computers, charging cellphones, etc...

We may get one of those trucker fridges for keeping our meat and dairy in for a few weeks.  They run on 14.4 volts and can be run on the smallest of solar installations, so that's a likely solution long term.  About $150 for a small one.   It's like a cooler that refrigerates, and it's fine in the back seat of a car.

A van is a distant possibility.  Things aren't really dire when the power goes, just dull mostly-- hopelessly boring.  Although the imagination can run away with you when your grocery store throws out all the ice cream and opens in the dark...   

Ever seen _Shaun of The Dead_?  Lol, it was a lot like _Shaun of the Dead_ around here, (minus the zombies, of course.)   Well, for the most part, no zombies....  Though there was that one guy at the Safeway store I wasn't too sure about...  He mighta' been a zombie, but other than him, no zombies...

People are funny when the power goes down.  There's a local supermarket with a generator that stayed open during the whole affair, and people really appreciated the service.  I surely did.

All the gas stations shut down!  That was the biggest surprise.  You'd think a gas station would be able to run a generator, wouldn't you?  They're run by frickin' energy companies!

Thanks again for the feedback.  Lots of food for thought.

---

### Post by SeijiSensei on 2019-11-08
I've subscribed to both T-Mobile and ATT, and both offer the ability to use your phone as an access point.  On T-Mobile, it's free.  I haven't tried to use the option on my ATT account, so I don't know what the charges are, if any.  I've done this a couple of times when the power went out.

Modern phones have very long-lived batteries so you could probably use this option for a decent number of hours.  My older phones have had replaceable batteries so I always had a spare or two if the need arose. My current phone, an LG Stylo 4, has a battery which cannot be replaced, but which holds a lot more charge than the earlier ones with replaceable batteries.

[https://www.computerworld.com/article/2499772/how-to-use-a-smartphone-as-a-mobile-hotspot.html](https://www.computerworld.com/article/2499772/how-to-use-a-smartphone-as-a-mobile-hotspot.html)

---

### Post by rsteinmetz70112 on 2019-11-08
Some cell phones or tablets can function as hot spots, that's probably easiest. You may be able to tether your phone to a laptop, depending the phone and your wireless provider. Maintaining power for a long time with batteries can be difficult, although a small gasoline generator to recharge batteries can be had pretty cheaply. You can also use your car to charge battery packs but may need an inverter for the laptop.

It depends on how much time you need to stay online.

---

### Post by TheFu on 2019-11-08
> **uRock said:**
> I think cell providers are required by law in the US to have backup power, though their systems can be set with QoS to only allow 911 and emergency services to use them during the outage.

If I were living in the area you're in, then a backup generator may be a good investment. Without going into politics, PG&E's systems will likely get worse before the state gov takes it over and may never get better if the state doesn't do it right.

All telecom systems have battery backups that should last at least 6 hrs in the USA. It is a regulated industry. The central offices, DSLAMs all have battery backup for 6+ hrs.  I don't recall seeing a CO that didn't have a generator capability, but have only been to about 100 of those that also housed work centers for the telecom technicians. Massive flooding can easily take out a CO, but class 5 telecom data centers should never, ever, ever, fail.  We did monthly full testing of our DCs and would run for a few hours on the generator every month in each DC.

Cellular service is non-regulated, so backup power is whatever each provider decides for each location.

---

### Post by jetsam on 2019-11-08
Growing up in the 70's, Ma Bell's old land lines just never went down as far as I can recall.  They were almost a secondary power system, too, apparently.  40 volts (AC?), not really enough to be dangerous, just enough to make you think twice about wiring it yourself...  I think you had to call a service tech to get a new phone installed, and you had to rent that phone, and you were happy to do so...

Without going too Archie Bunker, it's one bit of tech that has truly gotten worse in recent years.  Losing our AT&T landline is my one big regret about getting cable internet.  I don't think we needed to get the whole bundle, but it almost wasn't an option to split our plans and keep the land lines with the old system.  It was corporate mergers what done it.  At&T@home became some other company became Comcast cable, and before I knew it we still had our old phone hardware attached to a landline, but everything was coming into the house through the cable modem, and all the blinky green leds lights went out when the power did....

Cell towers are supposed stay up as long as they have either battery back ups or backup generators installed.  At least one locally must have something like that.  We're near a hospital and the fire station, and the county seat is just a mile down the road.  The antennas that come out of the civic center roof are many and varied in size and (and, I'm sure, function.)  There's a scary, almost haunted looking ham shack down an alleyway on the drive way to the civic center.  I've wandered the meadow there, but not asked questions ;)  Off the parking lot in the other direction, an old national guard armory...  they hold a good used book sale there every year.

I think what I'm getting at, in a round-about way, is that I'm pretty sure there might be a first responder or two that hangs around our neighborhood.  I doubt communications will ever fully go down at the regional level, and they certainly won't locally.  The civic center was built in the 1950's, it's cold war approved!  The fallout shelter is not on any map I know of, but surely...  it's there, somewhere...

---

### Post by jetsam on 2019-11-08
Just got a shiny new Android Moto phone.  Thanks for your input, all.  I think I'll be good....  need to work with it a bit and try out that  PdaNet+ app.  

I'll update the thread once I get it working or not.  I was offered a lot of other options at the various cell provider storefronts today, but they all kind of suck (money, if nothing else...)  All those Salesmen and wanna-be contract lawyers...   Yikes.  T-Mobile seemed to have the most competitive offers, but I think I'll stick with my current provider for now.  It's multi-network, so it may be the best option for maintaining connectivity in the event of a blackout, anyway.  It will have the flexibility to choose the tower with internet access over the one with just basic voice because it isn't tied to a single network. 

Cheers,
jetsam

---

### Post by rsteinmetz70112 on 2019-11-09
Legacy Telcos had 46v DC Power (thanks to  Edison) with Battery backup, usually 8 hours and that was backed up with usually diesel generators and significant fuel supplies, which could be replenished. I once designed a facility which had 12 hour UPS backup dual generators and a 14 day fuel supply. 
This are no longer the norm.
After the federal levees failed in New Orleans cell service failed after a while but text services continued unaffected. The main switching equipment went down not because backup power failed but because the AC cooling towers failed due to lack of make up water.

---

### Post by jetsam on 2019-11-12
This is cool.  pdanet+ is now running my internet connection, tethered via my cellphone to my pc through a usb cable.   I unplugged my office switch to simulate an internet blackout.  I'm streaming YouTube audio and making this post now, and it friggin' works! 

...and that's cool.

Thanks all for your input.  Marking solved.

edit: padnet+ isn't perfect.  It's crying out for an open source clone, to be honest...  still.  It's free as in beer, and it works.  I had to pretend to be a developer, though, and jump through some hoops to make it chooch.

---

### Post by jetsam on 2019-11-12
Aw, heck...

...pdanet+ may not be Linux friendly.  The problem is it requires a small application on the PC it's connected to in order to function.  There's a mac os X version, a windows (7 through 10) version...

...you may have guessed the issue.  There's no Linux version I can see.

"More platforms to come... " it says on the download page...

Marking the thread unsolved until this can be resolved.  The Mac version might be adaptable, or something through Wine....  What a pain!

---

### Post by jetsam on 2019-11-12
Fewf!  There's a solution by just setting some proxy settings in Firefox.

Video walkthrough here:
[PdaNet+ with Linux]("https://www.youtube.com/watch?v=NqTw8M26-tk")

Same channel, how to set the proxy at the system level to allow updates, etc...
[PDANet+ with Linux revisited]("https://www.youtube.com/watch?v=kP7kagBc_3k&feature=youtu.be")

He's running Ubuntu/Mint Mate.

Marking the thread solved again.

Cheers,
jetsam

---

### Post by jetsam on 2019-11-12
I don't like quadruple posting much ( ;) ), but I have some fresh info about the performance of this system.

It basically works "smart."  If it has a wi-fi connection available, it will use that and can run (as far as I can tell) all day, maybe longer...  When and if the wi-fi connection goes away, the phone connects through the cell phone network and starts using the cell phone data plan...  It seems to intelligently reset your browser sessions when it does this.  I had to re-log into the Ubuntu forums; I think the session got reset.  

So basically, data usage at least for me is not a big issue.  Since I have an "expando" data plan and only get charged in lumps for what I use, the system will only use as much plan data as it actually needs to.  The nice thing is that, under those circumstances, it's data that I'm perfectly happy to pay for.

I couldn't be happier with the performance of the set-up in general.  It more than meets my needs.  As long as the cell phone network is alive and well, we can connect.  If the power goes out at our house, we have an 80 minute battery backup plus a handful of power banks...  We're all set for the next PG&E based block party.  Heck, we could probably provide connectivity to the neighborhood the next time things go dark...

Cheers all...
No promises, but I may write up a how-to for this at some point.

---

