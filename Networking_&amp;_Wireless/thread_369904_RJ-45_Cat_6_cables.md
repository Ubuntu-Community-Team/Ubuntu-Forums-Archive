---
title: "RJ-45 Cat 6 cables"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by aliyanage on 2007-02-25
Hi all,

Maybe someone can help me out on this one. I am trying to get the cabling done at work, now what exactly is the difference between a cat5 and a cat6 RJ-45 cable and which premises have to be furfilled by the jack to be able to use cat6 RJ-45 cables?

regards
aliyanage

---

### Post by koenn on 2007-02-25
Both are cables with 8 wires (4 pairs). The difference is in the way the cables are made, but practically the categories indicate what speeds the cable will support. for a 100 mbps network, cat5 should be OK, for 1000 mbps you require at least cat 5e or cat6. 

If you're going to install new cables, i'd seriously consider cat6. Maybe the difference in price is an object, but those cables are going to be there for a while, and you don't know what the future will bring. New desktop PC's already have gigabit network cards and you may need those speeds in the future - voice, video, huge data transfers, bandwith-hungry applications ...

RJ45 is just a standard modular plug for 8 wires (4 pairs) - works with any category 

[http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)
[http://en.wikipedia.org/wiki/Category_6_cable](http://en.wikipedia.org/wiki/Category_6_cable)

---

### Post by Jose Catre-Vandis on 2007-02-25
Yep, CAT6 all the way from me too. ensure you follow the same wiring protocol throughout your install (there are two formats) and be sure to check that all your NICs (Network Interface Cards) are up to scratch and can auto negotiate for full duplex. No horizontal runs of more than 100yds/90m. Think hub and spoke when connecting network devices up.

---

### Post by aliyanage on 2007-02-25
thank you guys,

well so the jack that you plug doesn't need any requirements I guess. So let me make a little summary on this for me to check:

-NIC (fullduplex support)?
-is it worth it data tranferwise?

am I correct?

---

### Post by RandomJoe on 2007-02-25
I believe you can buy jacks that aren't rated to the highest speeds, so you have to watch for that.  It will have to do with the way the jacks are wired.  Any jack is going to impose an impedance bump on the line, and the quality of said jack will determine how large / disruptive that bump will be.

I haven't seen a network card in quite a long time that wouldn't do full duplex.  I suppose some of the really cheap $10 CompUSA-special-type cards might not, but just about everything else should.

And to preface what I'm fixing to say/ask, I would certainly use 5e or (preferably) 6 to wire a new office.  As was mentioned before, the cable's going to be there for a long time so do it right!

That said...  Here at home, and especially when I am working on jobsites in less-than-ideal conditions, I've had occasion to use some truly crappy cabling and have been amazed how resilient Ethernet is.  I've run 100Mbps over roughly 80ft of unpaired _thermostat wire_ out on a jobsite, and I run GigE over scrap / leftover Cat5 and old punch blocks here at home without issue.  Not to mention the abuse some of my patch cords see (stepped on, pinched under furniture, so on).  

Now, the 100Mbps link wasn't fully utilized, but it was a good solid connection for the duration of the time I needed it. My GigE runs here at home frequently sees high utilization and based on others' reported data rates for similar functions I'm not seeing much in the way of speed degradation.

So with that in mind, just when does the lesser-quality cabling turn around to bite you?  Is it primarily an issue with runs that come close to the maximum Ethernet run length?  Or more a function of cheap cable will eventually break down sooner than the higher quality stuff?

I can actually afford to go buy a box of CAT6 and all-new blocks and jacks, I'm just cheap... ;)

---

### Post by koenn on 2007-02-25
I can think of ta couple of things re. cabling. 
Back in the 10 mbps days, it was not uncommon to split a utp cable over two connectors, each using 2 pairs 'cause that's all they needed for 10 mbps, or use 2 pairs for data and 1 or 2 others for telephone. Sounds "efficient" - you save half of the cable cost ... until 100 mbps and gigabit come around and you have to re-do all the cabling or remain stuck with 10 mbps

I recently was at a site where they installed a new telephone system, and some of the phones simply refused to work - apparently due to sub-standard cabling and/or interference with other pairs in the same cable.the same unit would work just fine on other outlets with newer/better wiring. 

As for data, ethernet and TCP can handle quite a bit of errors so you never notice the effects of sloppy connections or not completely up to standard cabling. How ever, the error correction requires re-transmission etc so for time-sensitive applications (voice, ...) and/or when the network is used at near full capacity, i guess you'll notice the effects.

lastly, if you're having trouble with network appliances and software, the guy you want to fix it will just blame it on sub-standard cabling and in stead of having your problem fixed, you'll end up with endless discussions whether or not cabling has anything to do with it. Not something you can afford in most professional environments. 

So, do-it-yourself cheap creative solutions are OK for home, but in a professional context, it's a different ball game.

---

### Post by topak on 2008-07-08
make it a [cat6 cable installation](http://www.aaa-avad.com). more value to your money! :KS

---

