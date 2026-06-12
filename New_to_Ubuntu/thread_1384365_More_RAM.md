---
title: "More RAM?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by hatridge on 2010-01-18
today i will be installing ubuntu on a friends old computer. It has windows xp on it now. This machine does not have enough RAM. My question is....if I double up the RAM by plugging in card into the extra slot...and boot from Linux cd...will linux recognise the RAM automaticaly or do I need to adjust my BIOS first?

---

### Post by warfacegod on 2010-01-18
Almost certainly it will see and using it.

---

### Post by baizon on 2010-01-18
If your Board supports (and recognize) that memory Linux will detect it also.

---

### Post by hatridge on 2010-01-18
thanks...Hardware was never my thing...but it's time I dove into the deep end...

---

### Post by J V on 2010-01-18
how the hell does windows run if its got too little ram to install ubuntu? How much does it have?

---

### Post by audiomick on 2010-01-18
Be careful how you handle the RAM. From what I have read, it is very sensitive to static electricity. Don't touch the contacts, avoid standing on nylon carpet, etc. while your are working on it. It is not a bad idea to earth yourself to the chassis of something before you start.

---

### Post by pirateghost on 2010-01-18
> **audiomick said:**
> Be careful how you handle the RAM. From what I have read, it is very sensitive to static electricity. Don't touch the contacts, avoid standing on nylon carpet, etc. while your are working on it. It is not a bad idea to earth yourself to the chassis of something before you start.
and be sure and take off your tinfoil hat also.

in 11 years of working with hardware, not once have i killed RAM due to static....

---

### Post by switch10 on 2010-01-18
yes it is best to ground yourself (touch the case) before handling any part in your PC.  Thats why most components come in an anti-static bag.   

If the computer is running XP, Ubuntu will have no problem running.

---

### Post by audiomick on 2010-01-18
> **pirateghost said:**
> and be sure and take off your tinfoil hat also.

in 11 years of working with hardware, not once have i killed RAM due to static....

At the risk of sounding like a boring pedant...

I've never killed any components either, however "from what I have read" includes that packaging of some RAM sticks.

Apart from that, I have seen static do some weird things, including completely crashing the control console of a conference system. And I didn't even touch it, just my toolcase on the floor next to the table it was on...

Anyway, it doesn't hurt to be careful, and it would be a pity to be the one in one hundred thousand.

---

### Post by hatridge on 2010-01-18
248 MB of Ram and it hardly runs xp ...but it does....slooowly. She asked for some help so I am going to help her first by getting her  a Gig, then Ubuntu and out of the windows sink hole. Yes to the anti static....thanks. I'll let you know if I burn up.

---

### Post by Paqman on 2010-01-18
> **pirateghost said:**
> and be sure and take off your tinfoil hat also.

in 11 years of working with hardware, not once have i killed RAM due to static....

Not that you know of, but you absolutely will have reduced the lifespan of everything you have handled incorrectly. ESD is no joke, and is taken very seriously within industry. Just because you can't see it, doesn't mean it isn't real. In some applications (such as working with explosives and pyrotechnics) ESD can cause some very unpleasant effects.

---

### Post by warfacegod on 2010-01-18
> ...some very unpleasant effects.

That's an interesting way of saying "Blow yourself to the Moon"!

---

### Post by pirateghost on 2010-01-18
> **Paqman said:**
> Not that you know of, but you absolutely will have reduced the lifespan of everything you have handled incorrectly. ESD is no joke, and is taken very seriously within industry. Just because you can't see it, doesn't mean it isn't real. In some applications (such as working with explosives and pyrotechnics) ESD can cause some very unpleasant effects.
LMAO...tell that to the machines that I built 10 years ago that are still running today.....my point was that some people take it to the extreme, when just using COMMON SENSE would suffice....although, most people lack that gene.

---

### Post by audiomick on 2010-01-18
> **pirateghost said:**
> ...my point was that some people take it to the extreme, when just using COMMON SENSE would suffice....although, most people lack that gene.

Your right, including the gene in a lot of cases. It is just that what is common sense to you might not occur to someone at the first attempt at changing hardware components. That's why I do the boring pedant thing...;)

---

### Post by albert s on 2010-01-18
for my tuppence, just wondering that if your PC only has 248 of RAM now, do you think it will actually be able to see 1G.?
I would question whether the board is new enough to handle that.

---

### Post by audiomick on 2010-01-18
> **albert s said:**
> for my tuppence, just wondering that if your PC only has 248 of RAM now, do you think it will actually be able to see 1G.?
I would question whether the board is new enough to handle that.

good question, actually...

---

### Post by mk1w86 on 2010-01-18
> **audiomick said:**
> good question, actually...

Yes, what are the specs of the machine **hatridge**, processor, hard drive size etc. :-s

You have probably seen this but here are the hardware requirements for Ubuntu:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by warfacegod on 2010-01-18
A good way to find out how much RAM your system can have is to go here:

[http://www.crucial.com/]("http://www.crucial.com/")

and use the _Crucial Memory Advisor tool._

---

### Post by Paqman on 2010-01-18
> **pirateghost said:**
> .....my point was that some people take it to the extreme, when just using COMMON SENSE would suffice....

It's nothing to do with common sense. It's about using correct technique. Very few IT people i've met have an engineering background, and thus have bad habits. You won't find an electrical engineer or technician handling components without taking ESD precautions.

---

### Post by mk1w86 on 2010-01-18
> **Paqman said:**
> It's nothing to do with common sense. It's about using correct technique. Very few IT people i've met have an engineering background, and thus have bad habits. You won't find an electrical engineer or technician handling components without taking ESD precautions.

What kind of precautions would you suggest that may be of help to the OP? :-k

I usually wear an anti-static wrist band to ground myself, avoid touching contacts on boards and do not work on carpeted floors etc. although I am no expert in this area.

---

### Post by audiomick on 2010-01-18
> **mk1w86 said:**
> I usually wear an anti-static wrist band to ground myself, avoid touching contacts on boards and do not work on carpeted floors etc. although I am no expert in this area.

Sounds pretty good to me. If you can't get a hold of a wrist band, regularly touching something metal that is connected to the ground is a fair second best.

---

### Post by warfacegod on 2010-01-18
General steps should be to wear sneakers or boots with rubber soles (basically all shows) not just socks. Touch the metal frame of the computer case before any parts, and perhaps snug surgical gloves wouldn't be remiss (although probably overkill).

Aside from that, don't worry about it. Unless you happen to have a secret level 5 cleanroom laboratory in your basement like I do, there's not much else you can do.

---

### Post by baddog144 on 2010-01-18
The whole point is 'better safe than sorry'.
The chances of killing your RAM through ESD are not huge, but they're still there, and it's worth taking the precautions.

---

### Post by daniell59 on 2010-01-18
When I build my computer I just wait for a humid day.

---

### Post by egalvan on 2010-01-18
The BIOS mem_init routines will scan for any available RAM.
Depending on the chip-set, it may or may not find it all.

Also, the BIOS may natter at you if it finds the amount of RAM has changed since last boot....
if the new size corresponds to the amount installed, then all is fine.
If not, then you may have compatibility problems.


So...
Install the RAM sticks, boot the LiveCd and run a "mem-test".
Let it run at least 30 minutes.

If all is well and fine, well fine then, all is well. :)

---

### Post by egalvan on 2010-01-18
[QUOTE=warfacegod;8686579with **rubber **sole and perhaps snug surgical gloves 
[/QUOTE]

Reducing ESD buildup is all about having good conductivity to allow the charge to bleed off, preferably to a good ground.

Rubber soles and rubber gloves will insulate you electrically, allowing a build-up of a static charge.


That is why ESD safety practices specify such things as

touching the metal parts of the machine being worked on

wearing an "anti-static" wrist band

standing on "anti-static" matting

having "anti-static" counter-top


all of these depend on conductive elements...
conductive metal
conductive foam
conductive fabric


And yes, the semi-conductor industry spends millions on anti-static measures.
The threat is real.

Small, 
but real.


I once burned out two RAM boards, back to back, when I accidentally dis-connected the ground lead on the tool I was using.
$300 in five minutes.
(known good boards, having been tested previous to installation)

Yeah, small
but real.

---

### Post by warfacegod on 2010-01-18
> Rubber soles and rubber gloves will insulate you electrically, allowing a build-up of a static charge.

If this is the case then why is it that when I walk around my house in socks, I am constantly zapped when I touch a doorknob but when I wear my boots I don't get zapped at all?

---

### Post by llawwehttam on 2010-01-18
I wear no gloves, wear staticy wooley jumpers, stand on nylon carpets, wear no wrist straps and work on a wooden desk.

I have never had any problems with static.
I probably just jinxed myself tho lol

---

### Post by Paqman on 2010-01-18
> **mk1w86 said:**
> 
I usually wear an anti-static wrist band to ground myself, avoid touching contacts on boards and do not work on carpeted floors etc. although I am no expert in this area.

Yep, between using a wrist strap and handling the boards by the substrate that's perfectly good enough. Make sure your wrist-strap has at least 1M ohm of resistance in it though, for safety. I've bumped into ones that didn't before.

---

### Post by audiomick on 2010-01-18
> **warfacegod said:**
> If this is the case then why is it that when I walk around my house in socks, I am constantly zapped when I touch a doorknob but when I wear my boots I don't get zapped at all?

Your socks pick up a static charge through rubbing against the floor and that transfers to you. When you touch a doorknob, you create a path to earth through the door, discharge yourself and get zapped. The material in the soles of your boots doesn't build up a charge. I have one pair of sneakers that I don't dare to wear to work (as a sound engineer) because they pick up a static charge everywhere.

I find it helps to touch the wood first, instead of the doorknob, or even the glass, if it is a glass door. I think this is because it supplies a path to earth same as the doorknob, but with a higher resistance, so the discharge is less sudden.

It also helps if you can make contact on a large surface all at once instead of a fingertip, so the discharge takes place more spread out.

Best of all is to only wear pure wool or pure cotton socks, and only use floor coverings made of natural substances, like wool carpets and wood.

---

### Post by warfacegod on 2010-01-18
From now on, I'm doing all of my repairs naked.

---

### Post by audiomick on 2010-01-18
> **warfacegod said:**
> From now on, I'm doing all of my repairs naked.

photos? ;)

---

### Post by no2498 on 2010-01-18
only thing ive not seen is
leave it plugged in just not on
the power cord has a ground in it

and as for the memory her computer had to be very slow
a stick of 256 would help a lot

---

### Post by Paqman on 2010-01-18
> **no2498 said:**
> only thing ive not seen is
leave it plugged in just not on
the power cord has a ground in it


I've heard that too, but I don't think it's good practice. Unplugging something before working on it is basic safety stuff.

---

### Post by audiomick on 2010-01-18
> **Paqman said:**
> I've heard that too, but I don't think it's good practice. Unplugging something before working on it is basic safety stuff.

I end to think so too. That is the (only) good thing about German power points: the earth is exposed, so you can just touch that to discharge yourself. A tap is good too, if the water pipes are metal.

---

### Post by warfacegod on 2010-01-18
> **audiomick said:**
> photos? ;)

Absolutely not.

---

### Post by audiomick on 2010-01-18
> **warfacegod said:**
> Absolutely not.

Oh well. Probably wouldn't be able to sell them anyway...:D

---

### Post by warfacegod on 2010-01-18
> **audiomick said:**
> Oh well. Probably wouldn't be able to sell them anyway...:D

Shots of naked guys fixing computers aren't in demand anymore?

---

### Post by theozzlives on 2010-01-18
> **hatridge said:**
> 248 MB of Ram and it hardly runs xp ...but it does....slooowly. She asked for some help so I am going to help her first by getting her  a Gig, then Ubuntu and out of the windows sink hole. Yes to the anti static....thanks. I'll let you know if I burn up.

248 is an odd amount. It probably has a 256 MB stick and shared video memory. If any, you may be able to go to 512. Check with the motherboard manufacturer's website.

---

### Post by -kg- on 2010-01-18
As an aside:

The [Microsoft Tech Site]("http://technet.microsoft.com/en-us/library/bb457057.aspx") says:

> ...Although it is recommended, Windows XP does not require 128 MB of RAM. The operating system can run with 64 MB of RAM.

With 256 MB of RAM, it should run quite sufficiently, depending on what exactly you're running.  It might be that XP is just "jammed up," especially if it's been up and running for a while, and perhaps been to a few "bad" sites or received a few "bad" emails.  A lot of times, it's sufficient to have just run XP for a while.

Of course, more RAM is a good thing (up to a point, but 256 MB is well below that point).  It would help performance of XP, and it will definitely help the performance of Ubuntu.

Also, listen to what they're saying about protecting the RAM chip from static electrical discharge, but don't get all paranoid about it.  I've been working on (and replacing) various memory cards, chips, transistors and ICs for around 35 years now, and I have yet to have a problem.  I built my current desktop from the ground up.

Don't work on a carpeted floor, just to be safe.  Grab the chassis of the computer, just to be safe.  Definitely don't touch the pins of the RAM card or the pins of the RAM chips on that card.  But I don't think you need to drive a series of grounding rods in your back yard, tie them together, and run a braided grounding strap to the wrist band of your moon suit.  That would be overkill. ;)

A RAM upgrade is one of the easiest upgrades you can perform.  Just pay attention and be a little careful, and you should have no problems.

---

### Post by walt.smith1960 on 2010-01-19
A couple thoughts on this thread.

[LIST]
[*]I've checked a few different machines running Karmic via system>administration>system monitor. They all seem to be using around 225-250Mb. RAM running the O.S. and Firefox. If I had less RAM than that I assume Karmic would be using swap which would slow things down. It seems like 512Mb. would be good. With more applications running, more RAM is likely better. I don't even WANT to know how much RAM Windows Vista would use doing the same job:shock:
[*]With Newer machines  selecting"shut down" in the operating system  doesn't remove all power. The only way to remove all power is to unplug unless the power supply has a switch. It would be nice to be able to leave a machine plugged in in order to have the ground, but what is the risk of plugging and unplugging components where the motherboard may have power on it?
[/LIST]

---

### Post by PenguinInside on 2010-01-19
It's not a bad idea to discharge yourself before working with hardware.

But another thing to be aware of when installing RAM is to be sure which way it goes in (left or right, not up and down).  Pay attention to the notches, they differ if you plug it in left vs. right.

There's only one way, and if you mess it up, you can fry the RAM as well as the mainboard.

Generally, Linux has never not detected RAM for me.

---

### Post by PenguinInside on 2010-01-19
> **walt.smith1960 said:**
> A couple thoughts on this thread.

[LIST]
[*]With Newer machines  selecting"shut down" in the operating system  doesn't remove all power. The only way to remove all power is to unplug unless the power supply has a switch. It would be nice to be able to leave a machine plugged in in order to have the ground, but what is the risk of plugging and unplugging components where the motherboard may have power on it?
[/LIST]

Well, there are debates on that. Some people say leave it plugged in because you have a path to ground (the third pin of the cable).

Others say unplug.  Do you have a voltage tester? It's a little thing you can get from a hardware store to tell you if a piece of metal has live current in it. (Note: the parts of a computer other than the inside of a power supply will only have live current if there's a fault.) Does your computer give you a shock if you touch the case? If so, be sure to unplug.

---

### Post by qyot27 on 2010-01-19
> **-kg- said:**
> With 256 MB of RAM, it should run quite sufficiently, depending on what exactly you're running.  It might be that XP is just "jammed up," especially if it's been up and running for a while, and perhaps been to a few "bad" sites or received a few "bad" emails.  A lot of times, it's sufficient to have just run XP for a while.

Of course, more RAM is a good thing (up to a point, but 256 MB is well below that point).  It would help performance of XP, and it will definitely help the performance of Ubuntu.
As someone who finally got a proper 256MB->512MB upgrade to work a couple days ago (and a new graphics card about three weeks ago), I can confirm that yes, XP runs just fine with 256MBs if you keep things tidy.  Heck, I even do video editing/encoding on this thing, and have since 2003 - including a 720p60 video which was done in After Effects using a couple of really cheap shortcuts.

Ubuntu generally is snappy with 256MBs, too, although if there's any configuration weirdness (like it automatically choosing Normal desktop effects when the comp can't handle it*), it will be strained.  The solution, of course, is to turn off the desktop effects, and/or use a lighter-weight desktop environment.

*the i810e chipset's onboard graphics did this to me on 8.10, 9.04, and 9.10; *really* annoying and even makes the LiveCD nigh unusable until you turn off the desktop effects (if you actually go to the desktop in it, that is - if you select Install from the boot screen then you just have to live with it).  Either way, it also defaulted to 16-bit color when the onboard can easily handle 24-bit True Color (and I do mean plain 24-bit, not RGB32/RGBA, which is 24-bit aligned or 24-bit+8-bit alpha). It was actually the non-support of '32-bit' True Color that prompted me to get the graphics card I mentioned.  I really underestimated how powerful said card (Nvidia GeForce 6200 PCI variant from EVGA, from 2004) was too, as games that wouldn't even run or did so at around 12fps can now run at the 60fps they were designed for.  Sadly, that's only under XP; the performance under Wine is awful if they even run at all.

Now, with 512MBs, honestly I can't immediately see as much of a difference as I could from putting in the graphics card, but I do know it's there (then again I don't run resource-heavy background services like an anti-virus or Ad-aware).  Things seem to load a little faster and some tasks seem more stable - and this is on both Ubuntu (faster most noticed with the speed in which all the panel components, mainly the clock, load at startup) and XP.

I would recommend that if the system is prebuilt (for example, an eMachines like mine is - specifically I have the T1110), you can use any number of sites to find out the specific type of RAM you need.  Memory matching customizers are on Kingston's website, Crucial was already mentioned, and there's also Memorystock - I bought the 256MB module of Kingston PC133 168-pin SDRAM I needed from them, and I only had to pay $24 USD for it (it could have been $18, but I went with the Priority Mail option instead of free First Class).

The only problem I had was that if I had both sticks installed, Windows would error out with the 'BIOS is not fully ACPI compliant' warning and restart; couldn't even get into Safe mode.  Ubuntu 9.10, on the other hand, could detect and use all of it without issue, even when XP was having a mental breakdown over it (before you ask, memtest confirmed nothing was wrong with the RAM, and XP could use either stick in either slot without going crazy, just not both at once).  After going around in circles for a few days in many different directions and being told there's nothing wrong with the BIOS and that that's a misleading error because full ACPI compliance has been standard for years, it turned out it really *is/was* a problem with the BIOS' ACPI compliance when using 512MBs of RAM, and flashing it with a slightly-newer version (literally; the original was August 2001, the update was October 2001) cleared the issue right up.  So be aware of that.  I wouldn't worry about Ubuntu seeing it, though, as I mentioned it had no problem seeing/using it all (using x264 on --preset placebo, the RAM usage went up over 300MBs, and probably would have gone higher if I'd let the process continue - and yes, that was pre-flashing it).  Just know what you're doing if you have to flash the BIOS; you don't want to kill the motherboard.


Yay for rambling posts.

---

### Post by mk1w86 on 2010-01-19
> As an aside:

The Microsoft Tech Site says:

[QUOTE]...Although it is recommended, Windows XP does not require 128 MB of RAM. The operating system can run with 64 MB of RAM.
[/QUOTE]

Whenever I see that I think it refers to pre SP2.  I have always found that XP SP2 has required 512MB to run smoothly.  On any machine with less than 256MB I use Windows 2000.

---

### Post by audiomick on 2010-01-19
> **mk1w86 said:**
>  I have always found that XP SP2 has required 512MB to run smoothly.

My last computer simply ground to a halt when I tried to install sp2 on it.
One of the stepping stones on the road to Ubuntu...
;)

---

### Post by warfacegod on 2010-01-19
I had a Compaq Evo *D500?* it had a 1.7 P4 and 256 MB RAM. It was originally bought by Connecticut Light and Power. They bought around 500 of them and only used about 35 or so then sold them all when they discovered that Windows XP Professional (no SP) ran like a pig on it. After 2-3 months I put in another 512 MB RAM in it for a total of 768. After disabling about 90% of the services, ran only decently.

It damn near took flight when I put Ubuntu 7.04 in it.

---

### Post by mastablasta on 2010-01-19
> **warfacegod said:**
> I had a Compaq Evo *D500?* it had a 1.7 P4 and 256 MB RAM. It was originally bought by Connecticut Light and Power. They bought around 500 of them and only used about 35 or so then sold them all when they discovered that Windows XP Professional (no SP) ran like a pig on it. After 2-3 months I put in another 512 MB RAM in it for a total of 768. After disabling about 90% of the services, ran only decently.
 
It damn near took flight when I put Ubuntu 7.04 in it.
 
 
I bet they had the WinXP ready sticker on them :D
 
256 MB runs the WinXP SP3 OK, But you need some disk space and forget about multitaksing with multiple programmes. One task works relativelly OK though. If i could  be safe that removing firewall and antivirus wouldn't have any consequences it would run relativelly ok.
 
Ubuntu is doing OK with 256, Xubuntu even better...Not to mention Puppy or DSL, it's like a whole new computer.... :)

---

### Post by warfacegod on 2010-01-19
> **mastablasta said:**
> I bet they had the WinXP ready sticker on them :D
 
256 MB runs the WinXP SP3 OK, But you need some disk space and forget about multitaksing with multiple programmes. One task works relativelly OK though. If i could  be safe that removing firewall and antivirus wouldn't have any consequences it would run relativelly ok.
 
Ubuntu is doing OK with 256, Xubuntu even better...Not to mention Puppy or DSL, it's like a whole new computer.... :)

It did indeed have the sticker. Before I upgraded the RAM, opening IE while the Task Manager was open would bring the system to its knees. It's things like that that brought me to the conclusion that Windows isn't compatible with itself.

---

### Post by cascade9 on 2010-01-19
I've built a lot of computers, and never had anything blow from static yet. I dont use an anti-static wrist strap (annoying), antistatic desktop mats (not needed IMO) or antistatic floor mats (really, thats just going to far LOL).
 
 I do try to follow basic static awareness however...I tend to have a lugin computer right next the one I am working on, and touch it now and again throughout the build (when I start, touch the case, when I have to go away and come back to work, touch the case, etc). 
 
 > **walt.smith1960 said:**
>  
[LIST]
[*]With Newer machines selecting"shut down" in the operating system doesn't remove all power. The only way to remove all power is to unplug unless the power supply has a switch. It would be nice to be able to leave a machine plugged in in order to have the ground, but what is the risk of plugging and unplugging components where the motherboard may have power on it?
[/LIST]
 
 
 If its ATX, unplug it. IMO. I unplug everything, ATX without a switch, ATX with a switch, AT. 

> **PenguinInside said:**
> Well, there are debates on that. Some people say leave it plugged in because you have a path to ground (the third pin of the cable).

Others say unplug. Do you have a voltage tester? It's a little thing you can get from a hardware store to tell you if a piece of metal has live current in it. (Note: the parts of a computer other than the inside of a power supply will only have live current if there's a fault.) Does your computer give you a shock if you touch the case? If so, be sure to unplug.

Unplug it because there is always a bit of power going through ATX boards (unless they have a switch at the back and its turned off). The power switch on ATX is electrically controlled, so if it will turn on, its got power. AT actually has a 'hard' power switch (remember the having to wait to get the 'its safe to turn off your computer now' msg?) IMO the hard power control is the one advantage AT has over ATX.

---

### Post by cascade9 on 2010-01-19
> **warfacegod said:**
> I had a Compaq Evo *D500?* it had a 1.7 P4 and 256 MB RAM. It was originally bought by Connecticut Light and Power. They bought around 500 of them and only used about 35 or so then sold them all when they discovered that Windows XP Professional (no SP) ran like a pig on it. After 2-3 months I put in another 512 MB RAM in it for a total of 768. After disabling about 90% of the services, ran only decently.

It damn near took flight when I put Ubuntu 7.04 in it.

Heh, I've used worse. Some model compaq with P4 1.6, 128MB SD RAM..and 8MB of that being used for onboard video. Those things were slower than a wet week..you could start a program, go away make a cup of coffee and come back and it would just be finishing opening LOL. 

Those SD ram P4s were horrible. They were made for expensive RD-RAM memory, and using them with SD ram (non-DDR) crippled them. It took up till the later 533Fsb + 512K cache models running 845 chipsets with DDR 266+ before P4s ran properly.   

> **warfacegod said:**
> It did indeed have the sticker. Before I upgraded the RAM, opening IE while the Task Manager was open would bring the system to its knees. It's things like that that brought me to the conclusion that Windows isn't compatible with itself.

Hey, it worked, right? Those stickers dont mean 'will work nicely', just 'will work' ;)

---

### Post by warfacegod on 2010-01-19
Plugged vs. Unplugged

Heavy Weight Title Bout at Madison Square Garden.



Always unplug. Period. Leaving an electrical device connected to a power feed while you are tinkering with it is just flat out stupid. It is dangerous and anyone advocating the practice is being highly irresponsible.

I own and run (trying to anyway) a Remodeling Business. I will never let my guys mess with even a light switch if the power is connected to it. Not only is there a risk of injury or death, there is also the possibility of property damage. I once accidentally touched my wrist to two capacitors inside an *unplugged* PTAC unit. My arm went dead for about 6 hours.

What if you need to loosen a screw and you are distracted, startled, *not paying attention*, or just slip? What happens? Will you simply scratch your motherboard? Will you slide your screwdriver into your PSU? Does nothing happen? Do you get zapped and your fingers tingle? Will you get zapped and have it stop your heart? You don't know!

I have *never* seen an appliance with a sticker on that says "Go ahead, leave it plugged in". They all say "Unplug before service".

THERE IS ALWAYS A CHANCE, HOWEVER REMOTE, OF SOMETHING GOING BADLY WRONG IF YOU LEAVE AN ELECTRICAL APPLIANCE PLUGGED IN WHEN YOU WANT TO FIX IT!

---

### Post by warfacegod on 2010-01-19
> **cascade9 said:**
> Heh, I've used worse. Some model compaq with P4 1.6, 128MB SD RAM..and 8MB of that being used for onboard video. Those things were slower than a wet week..you could start a program, go away make a cup of coffee and come back and it would just be finishing opening LOL. 

Those SD ram P4s were horrible. They were made for expensive RD-RAM memory, and using them with SD ram (non-DDR) crippled them. It took up till the later 533Fsb + 512K cache models running 845 chipsets with DDR 266+ before P4s ran properly.   



Hey, it worked, right? Those stickers dont mean 'will work nicely', just 'will work' ;)

It turned on if that's what you mean. The thing that got me was that Compaq sold 500 hundred of these to my *power company*!

---

### Post by audiomick on 2010-01-19
> **warfacegod said:**
>  I once accidentally touched my wrist to two capacitors inside an *unplugged* PTAC unit. My arm went dead for about 6 hours.

Good point. Lots of power supplies have some rather large capacitors in them. There is a type of amplifier from Crown (but this is not the only thing that has done it to me) that will always give you a belt if you touch the pins on the power cord just after turning it off and unplugging. Another good one is the flash charging circuit on a camera.

Moral is: even when you have unplugged, there might be some volts in there somewhere....

---

### Post by mrbiggbrain on 2010-01-19
> **walt.smith1960 said:**
> 
I've checked a few different machines running Karmic via system>administration>system monitor. They all seem to be using around 225-250Mb. RAM running the O.S. and Firefox. 

The default setup for ubuntu is much in the way of overkill. I have gotten a base ubuntu minimal running wicd, firefox, fluxbox, rox, pidgion all at the same time in about 98mb of ram. I have built this system off both intrepid, jaunty and karmic minimals. the truth is that many of the services and programs that the default runs are unneeded by older computers.

---

### Post by warfacegod on 2010-01-19
You're also a Mac too, too!

---

### Post by cascade9 on 2010-01-19
> **warfacegod said:**
> It turned on if that's what you mean. The thing that got me was that Compaq sold 500 hundred of these to my *power company*!

Of course they did. Compaq dont really care if your 'new' P4 1.7Ghz feels, and for all normal tasks, is slower than the 1Ghz P3 it replaced, they just want sales.'Yes, we have the new intel 1.7Ghz!!! machines here. So fast! its nearly twice as fast as your current 1Ghz machines. Cant we send a rep out to help your with your purchase?'

I would bet, if its anything like the other corps I've worked with, theres 500 of those..things!..sitting on workers desks, with them sweating over how slow they are ('please wait a minute, sir, while I bring your records up'). Then, there are 25 people in management, who have 2Ghz/512MB machines, and 3-5 'upper management' types who virtually never use the computers, and they have 2.2Ghz/512MB RD-RAM machines. :|

> **audiomick said:**
> Good point. Lots of power supplies have some rather large capacitors in them. There is a type of amplifier from Crown (but this is not the only thing that has done it to me) that will always give you a belt if you touch the pins on the power cord just after turning it off and unplugging. Another good one is the flash charging circuit on a camera.

Moral is: even when you have unplugged, there might be some volts in there somewhere....

Yep, this can happen. Its 1 reason why people who dont know anything about power supplies really shouldnt open them. 

BTW, there is a neat way to drain the caps on a desktop machine. Unplug, then hit the 'power' button. The caps get drained trying to start the computer. It should work on other equipement as well, but to be honest, I'm not sure about how healthy it is for the caps. Its probably not bad to do it for occasional maintenance but I'd try to avoid doing it often....

---

### Post by warfacegod on 2010-01-19
If my memory serves, these things were slated for use in monitoring the power grids. Totally irresponsible on Compaqs part for selling them for that use. Of course, CL&P, ought to have done there homework before dropping nearly half a million dollars on computers they couldn't use for the purpose they had in mind. And my wife wonders while our power rates are so high. It's things like that and the State of Connecticut in the '70s, forcing CL&P to stop generating their own power and buy it from someone else. On an aside, I would love to see these old dinosaur burner power plants get shutdown and have nukes replace them.

Yep, knew about the power button trick, should have  mentioned it myself, thanks.

---

### Post by Roger Allott on 2010-01-19
> **PenguinInside said:**
> It's not a bad idea to discharge yourself before working with hardware.

Ron Jeremy gives similar advice, I believe.

---

### Post by warfacegod on 2010-01-19
> **Roger Allott said:**
> Ron Jeremy gives similar advice, I believe.

I believe Ron Jeremy is more of a software expert. Or maybe that would be wetware.

---

### Post by swoody on 2010-01-19
> **pirateghost said:**
> and be sure and take off your tinfoil hat also.

in 11 years of working with hardware, not once have i killed RAM due to static....

That is like saying in the 15 years I've been driving that I speed and never wear a seatbelt, but I've never been in a car accident. It is not good practice, and it's not the safe way to do it. Yes it may work for you this time, but next time you could fry a $200 CPU.

To the OP: Yes, once you install the new RAM Ubuntu will recognize and utilize it. Also, as it seems that you are helping out a friend, please don't install Ubuntu unless you have cleared it with that person. We don't want our beloved OS looked at as if it's a virus or malware that has wound up on their computer. If you do get the green light, then rock on! Just be prepared to become their own personal 'Ubuntu support technician' in the future :)

-Woody

---

### Post by qyot27 on 2010-01-19
> **mastablasta said:**
> 256 MB runs the WinXP SP3 OK, But you need some disk space and forget about multitaksing with multiple programmes. One task works relativelly OK though. If i could  be safe that removing firewall and antivirus wouldn't have any consequences it would run relativelly ok.
With my SP3 setup (although this was largely true for SP2, SP1, and even RTM), there's ZoneAlarm Free, Firefox with Adblock Plus, and Spybot - for Spybot, immunize whenever you update; I also do both standard and registry scans with CCleaner fairly often and keep the Temp cache clear.  And I've not had to deal with viruses or malware for years.  I did have AdAware for a long time but it eventually stopped detecting anything at all, and since it took up so many resources, it wasn't worth it anymore (Spybot doesn't have to run all the time, the immunization feature being the reason why).  The antivirus situation was much the same - besides, I know enough now about removing virii manually that I don't need one sucking up even more resources.

Generally speaking, I can turn on the computer, go pour myself a cup of coffee, and when I come back everything'll be fully up and running and finished loading.

---

### Post by warfacegod on 2010-01-19
> **qyot27 said:**
> With my SP3 setup (although this was largely true for SP2, SP1, and even RTM), there's ZoneAlarm Free, Firefox with Adblock Plus, and Spybot - for Spybot, immunize whenever you update; I also do both standard and registry scans with CCleaner fairly often and keep the Temp cache clear.  And I've not had to deal with viruses or malware for years.  I did have AdAware for a long time but it eventually stopped detecting anything at all, and since it took up so many resources, it wasn't worth it anymore (Spybot doesn't have to run all the time, the immunization feature being the reason why).  The antivirus situation was much the same - besides, I know enough now about removing virii manually that I don't need one sucking up even more resources.

Generally speaking, I can turn on the computer, go pour myself a cup of coffee, and when I come back everything'll be fully up and running and finished loading.

Give Glary Utilites a whirl.

---

### Post by patros on 2010-01-19
> **pirateghost said:**
> and be sure and take off your tinfoil hat also.

in 11 years of working with hardware, not once have i killed RAM due to static....

I have, although only twice in about 16 years.

---

### Post by Sylslay on 2010-01-19
It is best to ground yourself  before handling any part in your PC, touch metal heater/radiator in room and since than don't touch Yours jumper with bore hands.
PS. 1Gb is recomeded now a days. 2Gb could be to much for weak/ very old CPU.

---

### Post by qyot27 on 2010-01-19
> **warfacegod said:**
> Give Glary Utilites a whirl.
Any particular reason aside from variety?  It looks like it just does the exact same things my current solutions do, and they've not failed me yet.

---

### Post by warfacegod on 2010-01-19
I have found that Glary and Ccleaner together are top notch at bringing Windows back from the grave. For instance, each will catch Registry Issues that the other will miss. Glary has a number of useful tools whereas Ccleaner has only only a few. Empty folders finder, Duplicate files finder, Registry compactor, to name a few (mostly because I can't remember any others, been three years since I've used it consistently). I'm not saying give up Ccleaner but use them both if you like.

If you defrag then you might like Defraggler. Slow but good.

---

### Post by Paqman on 2010-01-19
> **warfacegod said:**
> 
If you defrag then you might like Defraggler. Slow but good.

Or Auslogics Disk Defrag. Fast and good.

---

### Post by warfacegod on 2010-01-19
> **Paqman said:**
> Or Auslogics Disk Defrag. Fast and good.

I was never a fan of Auslogics fondness for connecting to the net without telling me or the constant offers to buy.

---

### Post by PenguinInside on 2010-01-19
> **cascade9 said:**
> 
BTW, there is a neat way to drain the caps on a desktop machine. Unplug, then hit the 'power' button. The caps get drained trying to start the computer. It should work on other equipement as well, but to be honest, I'm not sure about how healthy it is for the caps. Its probably not bad to do it for occasional maintenance but I'd try to avoid doing it often....

Thanks for the tip. I hadn't thought about this before, but it does make sense.

---

### Post by cascade9 on 2010-01-20
+1 to ccleaner. Great little program. :) 

> **qyot27 said:**
> With my SP3 setup (although this was largely true for SP2, SP1, and even RTM), there's ZoneAlarm Free, Firefox with Adblock Plus, and Spybot - for Spybot, immunize whenever you update; I also do both standard and registry scans with CCleaner fairly often and keep the Temp cache clear.  And I've not had to deal with viruses or malware for years. 

When I finished using XP, I was down to just a firewall (online armour as I found it slightly better than zone alarm and used a lot less resources). I would install an anti-virus, and run hijackthis, just before I did my 6-12monthly reinstall just to see how much junk I had picked up-mostly I had nothing. 

I would have run anti-virus all the time but I found it too much of a performance hit. 

BTW, if you still play with XP, nLite is really worth a try.

---

### Post by ovid9 on 2010-01-20
Well, since you posted a couple days ago, you might have already installed Linux.  If your friend didn't want to spend any money, you could install Puppy (or another light version of linux).
 
A friend of mine just put Puppy on an archaic Dell laptop (10 years old) and it works just fine.  She gets online with it now and is happy to have a spare computer.   Just another option if keeping costs down is a goal.

---

### Post by qyot27 on 2010-01-20
> **warfacegod said:**
> I have found that Glary and Ccleaner together are top notch at bringing Windows back from the grave. For instance, each will catch Registry Issues that the other will miss. Glary has a number of useful tools whereas Ccleaner has only only a few. Empty folders finder, Duplicate files finder, Registry compactor, to name a few (mostly because I can't remember any others, been three years since I've used it consistently). I'm not saying give up Ccleaner but use them both if you like.

If you defrag then you might like Defraggler. Slow but good.
Yep, I've used Defraggler several times in the past.  I also use Speccy.  Piriform just makes great apps, IMO.  That compactor function sounds interesting.

[quote=cascade9]BTW, if you still play with XP, nLite is really worth a try. [/quote]
Aye, I used nLite about a year and a half ago to slipstream SP3 into my Pro disc along with some other configurational things (and it makes driver-related things easier too, I suppose).  I need to go through it all again sometime and trim down stuff and make sure the updates are all there.  It's probably too much to hope for that an SP4 will be released that collects all the updates from SP3's release through the end of XP's support cycle, though.

---

### Post by warfacegod on 2010-01-20
The first time I used Glary, it sped up my system by about 25% across the board.

---

### Post by hatridge on 2010-01-21
ah...all went good, I took out the 256 and filled both slots with two 512's. I booted up into windows to make sure it took. Then installed Ubuntu  without a hitch. No sparks. Thanks all.
:popcorn:

---

### Post by warfacegod on 2010-01-21
> **hatridge said:**
> ah...all went good, I took out the 256 and filled both slots with two 512's. I booted up into windows to make sure it took. Then installed Ubuntu  without a hitch. No sparks. Thanks all.
:popcorn:

How did you get 2 512 cards into each slot?

---

### Post by Sir Jasper on 2010-01-21
Hi wfg,

Two slots with two 512&#347;;  not two slots with 4 512s.

As Albert would say Get it, then we would say Got it, then he would say Good.

Best banter regards

---

### Post by warfacegod on 2010-01-21
> **Sir Jasper said:**
> Hi wfg,

Two slots with two 512&#347;;  not two slots with 4 512s.

As Albert would say Get it, then we would say Got it, then he would say Good.

Best banter regards

It was a joke. I know you can't put 2 RAM cards in one slot.

---

### Post by hatridge on 2010-01-21
well the motherboard had 2 ram slots. .....only one slot had 256.....took it out. put 512  in one slot and another 512 in the other slot.....simple no?

---

### Post by warfacegod on 2010-01-21
> **hatridge said:**
> well the motherboard had 2 ram slots. .....only one slot had 256.....took it out. put 512  in one slot and another 512 in the other slot.....simple no?

I'm going to stop telling jokes.

The way you wrote your last post made it sound like you put 2 cards into each of two slots for a total of four cards. I know you didn't because that would be impossible.

It was just meant to be amusing commentary.

I promise, no more jokes. warfacegod is now all business, totally serious with grin wiped from face.

Now please excuse me while I retrieve my chicken from across the road.

---

### Post by Sir Jasper on 2010-01-21
Hi again,

Of course I knew that you know, but now you know that I know.

I have once bettered Euclid, but I have never bettered Albert (as you have).

The Glary (for Windows) Disk Usage Analyser is almost instantaneous and by far the best I have seen. By partition, by directory, by file type and with the top 200 file space huggers listed in descending order. Plus right click, context menu, analysis. It would be ideal if ´buntu could replicate that speed and depth.

My regards

PS I only read the opening post here and the last few; else I would refrain from banter - except it seems the original question is resolved.

PPS Your chicken reminded me of a true story (I deplore jokes) about the Bird Impressionist interviewed for a star spot. They&#341;e two (not four) a penny said the threatrical agent - so he opened the window (not Windows) and flew away.

---

### Post by warfacegod on 2010-01-21
> **Sir Jasper said:**
> Hi again,

Of course I knew that you know, but now you know that I know.

I have once bettered Euclid, but I have never bettered Albert (as you have).

The Glary (for Windows) Disk Usage Analyser is almost instantaneous and by far the best I have seen. By partition, by directory, by file type and with the top 200 file space huggers listed in descending order. Plus right click, context menu, analysis. It would be ideal if ´buntu could replicate that speed and depth.

My regards

PS I only read the opening post here and the last few; else I would refrain from banter - except it seems the original question is resolved.

...And knowing is half the battle.

---

### Post by hatridge on 2010-01-21
....with a hammer and some determination i could put fit more than one card per slot. Nothing is impossible.

---

### Post by warfacegod on 2010-01-21
> **hatridge said:**
> ....with a hammer and some determination i could put fit more than one card per slot. Nothing is impossible.

With a hammer and some determination, I could level an mountain (excluding my divine powers of course) but will it work?

I'm gonna go try it on my wife's computer.

---

### Post by pricetech on 2010-01-21
> **hatridge said:**
> ....with a hammer and some determination i could put fit more than one card per slot. Nothing is impossible.

With a big enough hammer, you can accomplish anything.

---

### Post by warfacegod on 2010-01-21
> **pricetech said:**
> With a big enough hammer, you can accomplish anything.

Will an 8 lbs. sledge suffice?

---

### Post by pricetech on 2010-01-21
> **warfacegod said:**
> Will an 8 lbs. sledge suffice?

Is that all you got ??  I eat 15 lb sledgehammers for lunch !!!

---

### Post by warfacegod on 2010-01-21
> **pricetech said:**
> Is that all you got ??  I eat 15 lb sledgehammers for lunch !!!

No. I have two 8 lbs'ers. One for each hand.

---

### Post by hatridge on 2010-01-21
[IMG]file:///home/jim/Desktop/Safety-Streetlight.jpg[/IMG]

---

### Post by warfacegod on 2010-01-21
> **hatridge said:**
> [IMG]file:///home/jim/Desktop/Safety-Streetlight.jpg[/IMG]

That's not determination anymore. That's obsession.

How's the RAM working?

---

