---
title: "It it worth upgrading a processor for only +600 or Mhz?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Keith1212 on 2010-04-25
A pc i have extra currently has a AMD Athlon processor clocked at 1100 mhz. I want to put this [AMD Athlon XP 2100+]("http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%202100+%20-%20AX2100DMT3C.html") into it as its the best as far as i can tell that my mobo[(k7t266 pro2)]("http://www.cpu-upgrade.com/mb-MSI/K7T266_Pro2_%28MS-6380%29.html") can handle. Is it worth it for only +600 mhz normal or if possible overclocked for +1000 mhz?

Its pretty cheap to pick up the processor off ebay, just wondering if its even worth the trouble. The pc also has 1gb ram atm.

thanks for the help.

---

### Post by Cowboybebop79 on 2010-04-25
As usual ram is more important than processor speed so I would grab an extra gig of ram and if you have anything left over from your budget upgrade your processor as much as you can with that. Also it depends on what your using the system for if its just a bit of graphics and web browsing then what you've got at the moment is fine and I would save the money for a whole system upgrade. And 64bit makes a huge difference on Ubuntu as I have found out.

---

### Post by cascade9 on 2010-04-25
@ Cowboybebop79- umm...yeah, RAM helps, but as long as Keith isnt hitting the swap disk much (ie isnt using as much or more RAM than he has) adding RAM will make no difference. 

> **Keith1212 said:**
> A pc i have extra currently has a AMD Athlon processor clocked at 1100 mhz. I want to put this [AMD Athlon XP 2100+]("http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%202100+%20-%20AX2100DMT3C.html") into it as its the best as far as i can tell that my mobo[(k7t266 pro2)]("http://www.cpu-upgrade.com/mb-MSI/K7T266_Pro2_%28MS-6380%29.html") can handle. Is it worth it for only +600 mhz normal or if possible overclocked for +1000 mhz?

Its pretty cheap to pick up the processor off ebay, just wondering if its even worth the trouble. The pc also has 1gb ram atm.

thanks for the help.

Going from an Athlon 1100B (100Mhz FSB) to a Athlon XP 2100+ (133Mhz FSB) is a major jump. Dont forget, that without overclocking, that is over a 50% increase in clock speed. 

However.......just in case you dont know this, there are different types on Atlhon XP- Palomino, Throughbred, Thorton and Barton. Acording to MSI, you can only use a Palomino and the 2100+ version of that chip isnt very common- the t-bred is far more common. 

Still, if you can find one (or even a +1500-2000 version of the same chip if you cant) it will make a difference. I probably wouldnt try overclocking a Palomino much, esp a 2100+ that is as fast as those chips ever got. 

Link to the actual MSI page for that board- 

[http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=289](http://www.msi.com/index.php?func=prodcpusupport&maincat_no=1&cat2_no=&cat3_no=&prod_no=289)

BTW, I used a Athlon 1200C (133 FSB) for a long time, and when I moved to a 2200+ the difference was noticable.  Going from a 100 FSB model would make it even more noticable. ;)

---

### Post by Penguin Guy on 2010-04-25
**2000Mhz = 2 x 1000Mhz?**
Processor speed is not the same as *actual* computer speed, the amount of operations it does per second makes a big difference. You could get a 1000Mhz processor that is faster than a 2000Mhz processor.

**Bottlenecks**
Computers have 'bottlenecks' in them, meaning that if you get a really good CPU, it may be processing data too fast for your hard drive. CPU is more important for things like creating/extracting archives, whereas HDD speed is more important for things like boot time - you should keep this in mind when deciding what to buy.

Hope this helps you make a decision.

---

### Post by NightwishFan on 2010-04-25
I would go for another core rather than x amount of hz. Unless you know what your workload needs are, just get something economical and modern. You probably do not need anything over powered. Make sure the processor is compatible as well.

---

### Post by Keith1212 on 2010-04-25
WOW! thx for all the great replys. SO much good info to take in. 

This would not be my main pc. Atm im using my laptop for downloading, games, and serving media to my xbox 360. not all at the same time of course. Doing all this tends to keep my laptop tied down. I would like to use the desktop in the OP as my media hub. So i could connect to it when ever from my laptop and share the media on it. Maybe what i already have will do this fine, just haven't tried. 

What made me wanna upgrade so fast is when i played youtube vids on it they were very choppy. Maybe i need to change some settings to fix this. Guess ill give it a go.

I forgot to mention it has a Geforce4 MX440 agp 4x GFX card. Do you think this would stream large files to my xbox fine? Or what ever else i may need to do with it involving the sharing of files?

---

### Post by NightwishFan on 2010-04-25
More hz will give more speed to a single task. Another core or multi-threading will give you the ability to do more tasks in parellel, and awesome speeds in anything that is multi-core enabled (some video converters are). I think the xbox does all the gpu work if you stream to it. If possible, perhaps just get a new pc, it would be cheaper than a bunch of new parts.

---

### Post by anewguy on 2010-04-25
There are several things to consider here, some have been touched on.

If you change your processor and the front side bus speed changes from 100mhz to 133mhz, you would be best off upgrading your memory at the same time, unless you know your memory supports 133mhz.  Otherwise the additional bus speed will be wasted on one of the more important pieces of your computer.

Your memory capacity (you said 1gb) shouldn't be a problem.

Your hard disk is also important when it comes to speed, as mentioned above.  For example, if your current hard drive has a 5400 rpm spindle speed, and increase to a 7200 rpm drive is a good move.  If the transfer rate is 100mps, and your motherboard supports a higher transfer rate such as ata-133, then that would be a good move as well.  If your hard drive is SATA, I would doubt you could do much about the transfer rate but the rotational spindle speed could still make a difference.

But I guess 1 of the more important things would also be cost.  While increasing the speed of your processor can make a noticeable difference, the type of CPU your motherboard requires (as mentioned above) is a far more rare device to find, and with that is going to come a price.  New memory to match the increase in bus speed will come at a cost, and I think that motherboard probably uses just DDR memory.  *IF* you need to change your memory for the faster bandwidth, be aware that DDR memory seems to be more expensive than say DDR2 now.  A new disk drive isn't nearly the financial hit it once was.  Decent drives with high storage can be had for well under $100 - sometimes less than $50 is you watch close enough.

So, as much as I rarely say it, because I am on a limited income and know how hard of a hit it would be to me, I think you should way your options and costs versus getting a new motherboard/cpu/memory combination.  If you watch the net, you'll see that some places often have such combos on sale at a very good price (I won't mention any by name here because this isn't the place to "plug" any vendor).  The difference in chipsets, bus speeds, support for multi-core cpu's, faster memory, etc., would give you a better path for upgrades then the limited choices  you have now.  Just a thought.

I guess that's it for my 2-cents worth, if it's even worth that ;)

Best of luck!

Dave ;)

---

### Post by quadproc on 2010-04-25
> **Keith1212 said:**
> A pc i have extra currently has a AMD Athlon processor clocked at 1100 mhz. I want to put this [AMD Athlon XP 2100+]("http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%202100+%20-%20AX2100DMT3C.html") into it as its the best as far as i can tell that my mobo[(k7t266 pro2)]("http://www.cpu-upgrade.com/mb-MSI/K7T266_Pro2_%28MS-6380%29.html") can handle. Is it worth it for only +600 mhz normal or if possible overclocked for +1000 mhz?

I once commented to a co-worker regarding a processor that was claimed to run at 2.5 GHz.  What I said was "Yeah, that's how fast it can execute no ops".  It took him about two seconds to realize the implications of that statement, and then he said "That's cold."

quadproc

---

### Post by Keith1212 on 2010-04-25
the mobo has 3 ram slots. So i have 1x kingston 512mb 333mhz, and i have 2x 256mb. One of the 256mb is samsung ddr dimm n 32 wnd po 119429.1(not sure the mhz on it) the other is a kingmax thats covered by a thermal take metal houseing so no idea the mhz on it.

oh and my hdd for it is a 40gb seagate barracuda 7200 rpm drive. 

I'm still considering getting the processor since its cheap and seems to be an easy upgrade. Would i have to switch any jumpers on the board to let it funtion at the 133mhz?

EDIT: funny story bout this desktop im talking about. I found it on the side of the road with a huge dent in the case. Both sides were missing and it had some lawn clippings in it lol. Took it home completely disassembled and cleaned with alcohol and it booted up perfect. It only had 256mb ram and a 10gb hdd in it with win2k loaded on it. Was very slow and unusable until i put Ubuntu on it.

---

### Post by anewguy on 2010-04-25
> **Keith1212 said:**
>  funny story bout this desktop im talking about. I found it on the side of the road with a huge dent in the case. Both sides were missing and it had some lawn clippings in it lol. Took it home completely disassembled and cleaned with alcohol and it booted up perfect. It only had 256mb ram and a 10gb hdd in it with win2k loaded on it. Was very slow and unusable until i put Ubuntu on it.

Years ago, while working with mainframes, we had a flood that pretty much destroyed a data center.  We're talking big iron - big backplanes, big boards.  When we found out the center was self-insured, they wanted the equipment repaired.  Well, it's quite interesting to see people cleaning grass clippings, leaves, mud and everything else imaginable from a set of big backplanes.  We dipped the boards in water, using a soft brush to try to clean all the stuff off, then dried them with hair dryers and placed them on towels.  Consider now that all the equipment was powered up and running at the time of the flood, and you get an idea of the fun we had.  We couldn't even get a service processor to boot so we could run diagnostics.  We tried for several days - then they decided it was costing too much so they decided to buy new equipment.  The really "funny" thing to me was that in those days some punch cards were still in use, including a puncher attached to one the machines.  I don't know if you've ever seen the little rectangles that come out when you punch a card, but there were hundreds of thousands of those little things stuck like glue to EVERYTHING.

Ah for the good old days!

Dave ;)

---

### Post by Keith1212 on 2010-04-25
> **anewguy said:**
> Years ago, while working with mainframes, we had a flood that pretty much destroyed a data center.  We're talking big iron - big backplanes, big boards.  When we found out the center was self-insured, they wanted the equipment repaired.  Well, it's quite interesting to see people cleaning grass clippings, leaves, mud and everything else imaginable from a set of big backplanes.  We dipped the boards in water, using a soft brush to try to clean all the stuff off, then dried them with hair dryers and placed them on towels.  Consider now that all the equipment was powered up and running at the time of the flood, and you get an idea of the fun we had.  We couldn't even get a service processor to boot so we could run diagnostics.  We tried for several days - then they decided it was costing too much so they decided to buy new equipment.  The really "funny" thing to me was that in those days some punch cards were still in use, including a puncher attached to one the machines.  I don't know if you've ever seen the little rectangles that come out when you punch a card, but there were hundreds of thousands of those little things stuck like glue to EVERYTHING.

Ah for the good old days!

Dave ;)
wow i feel for ya having to do that work man. Good thing you was getting paid. I have worked at a cpl places that used the old punch cards so i can imagine the mess.

---

### Post by cascade9 on 2010-04-28
> **Keith1212 said:**
> WOW! thx for all the great replys. SO much good info to take in. 

This would not be my main pc. Atm im using my laptop for downloading, games, and serving media to my xbox 360. not all at the same time of course. Doing all this tends to keep my laptop tied down. I would like to use the desktop in the OP as my media hub. So i could connect to it when ever from my laptop and share the media on it. Maybe what i already have will do this fine, just haven't tried. 

What made me wanna upgrade so fast is when i played youtube vids on it they were very choppy. Maybe i need to change some settings to fix this. Guess ill give it a go.

I forgot to mention it has a Geforce4 MX440 agp 4x GFX card. Do you think this would stream large files to my xbox fine? Or what ever else i may need to do with it involving the sharing of files?

I can have a check tomorrow if yuo want...but I'm 99.99% sure that the 2100+/1GB system I have runs youtube videos perfectly. (I dotn know for sure because I use youtube maybe once every 2-3 months). 

It does have a GF6600GT, but I have a GF MX440 sitting around that I can put in to see for sure (and its running an awful SiS chipset thats not as nice as the VIA Kt266 in your computer). 

As long as you are getting the xbox to decode, there should be no problems with using a machine that old (or older!) to share media around. As long as you have a 100Mbit network card anyway (which I would almost be certain you have..if not they are worth about $1 these days). 

> **anewguy said:**
> If you change your processor and the front side bus speed changes from 100mhz to 133mhz, you would be best off upgrading your memory at the same time, unless you know your memory supports 133mhz. Otherwise the additional bus speed will be wasted on one of the more important pieces of your computer.

Well...before I really answer this I'm going to just say that I'll stick with the DDR rates (so 200 instead of 100, 266 not 133 and 333 not 166). I would guess that it would have all 266/333 memory. The 512MB stick is 333, I'm not sure about the samsung (I would need to see a pic, or have a much longer hunt with the info provided) and all the heatsunk DDR1 I've ever seen was minimum 333, most 400+. 

Even if it was only 200, its still not a bad upgrade. True, it wouldnt be as fast as 266, but I've run lots of CPU with asynchronous FSB/RAM speeds. BTW, the 333 is really 'wasted' in some ways, unless you have all 333 or better, then you might be able to drop the RAM timings. No, thats not something you will see many people do, but its an old trick and I can say from expereince that I would rather have 'tight' timings @ 266 over 'lose' timings at 333, etc etc. 

*tight timings on DDR1 is 2.2.2.6, normal tends to be more like 2-5.3.3.7, and lose would be 3.4.4.8. A lot of 'DDR400' was actually DDR333/266 with the timings losened up...... 

> **anewguy said:**
> 
Your hard disk is also important when it comes to speed, as mentioned above. For example, if your current hard drive has a 5400 rpm spindle speed, and increase to a 7200 rpm drive is a good move. If the transfer rate is 100mps, and your motherboard supports a higher transfer rate such as ata-133, then that would be a good move as well. If your hard drive is SATA, I would doubt you could do much about the transfer rate but the rotational spindle speed could still make a difference.

ATA133 was a joke. In theory, faster, but really...forget it. Anyway, with HDDs, you are much better off using a newer, more data-dense HDD if you are after tehe best speeds- a 'slow' moden 5400 can blow away older 7200s due to data density, firmware updates, more cache, beter cache, etc. 

If you want a fast PATA IDE drive, just get the latest 7200 you BIOS can support (which IIRC should be pretty much any PATA with that board....I know I dont have the 137GB limit with my Kt266a motherboard) 

> **anewguy said:**
> 
But I guess 1 of the more important things would also be cost. While increasing the speed of your processor can make a noticeable difference, the type of CPU your motherboard requires (as mentioned above) is a far more rare device to find, and with that is going to come a price. New memory to match the increase in bus speed will come at a cost, and I think that motherboard probably uses just DDR memory. *IF* you need to change your memory for the faster bandwidth, be aware that DDR memory seems to be more expensive than say DDR2 now. A new disk drive isn't nearly the financial hit it once was. Decent drives with high storage can be had for well under $100 - sometimes less than $50 is you watch close enough.

So, as much as I rarely say it, because I am on a limited income and know how hard of a hit it would be to me, I think you should way your options and costs versus getting a new motherboard/cpu/memory combination. If you watch the net, you'll see that some places often have such combos on sale at a very good price (I won't mention any by name here because this isn't the place to "plug" any vendor). The difference in chipsets, bus speeds, support for multi-core cpu's, faster memory, etc., would give you a better path for upgrades then the limited choices you have now. Just a thought.

You do have a point in some ways, but I'm pretty sure that the machine should do what the OP wants it to with a bit of an upgrade to the CPU alone. For the price that old athlons go for, upgrading is a much better option than a new machine IMO.

A quick look on...er..... a 'major internet auction site' and I found the right model for $12.50 US, buy it now, free shipping.

BTW, correct model is "AX2100DMT3C" ("AXDA2100DUT3C" is the palomino)

---

