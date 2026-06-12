---
title: "How to diagnose a bad motherboard?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by kcox5342 on 2009-12-28
Summary: how can I tell if my motherboard is starting to go faulty?

Background: I was just thinking this morning, this is the first desktop machine I've ever owned that was not put out by the people who made the OS.  I've been a Mac owner since 1996, an Amiga owner before that, and there were C-64's and Apple //e's in my distant past.  I have a laptop and a netbook which have been running Linux with no flaws.  Ah, and then there's my Linux desktop...

I bought it in February 2008 from TigerDirect as a semi-pre-built system.  It has a TF-7025 motherboard, a dual 3.0ghz AMD processor, and 2GB of RAM, but no HD or optical drives.  I installed those and a pcHDTV 5500 TV tuner card, and got mythtv up and working reasonably well for quite some time.  But, this fall, it started having issues, little ones at first, but lately it's been acting crazier and crazier.  I finally disconnected the boot drive, replaced it with a spare, and installed mythtv all over again, but even that hasn't stopped the crashes.  There have been times lately when the thing wouldn't even boot a live CD like Slax all the way to the desktop.  Sometimes letting it cool off before rebooting seemed to help, although not lately.

So.  Apart from just buying a new motherboard and installing it to see if it helps, is there any way to know if this is the problem before spending money on a new one?  I've already done that with the power supply, and added another fan, but that's not helping.  The problem could also lie in the CPU, the RAM, or the TV tuners.  On a related note, are some motherboards better than others for this kind of always-on server type of situation?

---

### Post by spiky001 on 2009-12-28
Dont know if this helps i had a prob which kept crashing machine turned out to be powersupply if you hav a spare to try, might not be this but might be easier to try ?

---

### Post by Raistlin355 on 2009-12-28
Ok first things first.  Look at the capacitors on the mobo to see if you have any that are blown, they are the little can looking things on it and if they are blown the top will be popped out.  If alls good there check your power supply with a tester or a multimeter.  If that checks out run memtest to check the memory.  If that checks out remove ALL add on cards and see if problems go away, if they do slowly add the cards one by one (shutting down between adding hardware of course) until the problem reappears. IF nothing changes at that point, I would say its the cpu or the motherboard, unfortunatly I don't know of a way to really test either, aside from looking for physical damage on the board.  I almost never run into a blown cpu in this situation, so it is probably your motherboard if you get to this point.  As far as good mobos go I use Gigabyte or Asus although I have been using Gigabyte more and more because Asus support sucks.

---

### Post by Zzl1xndd on 2009-12-28
> **Raistlin355 said:**
> Ok first things first.  Look at the capacitors on the mobo to see if you have any that are blown, they are the little can looking things on it and if they are blown the top will be popped out.  If alls good there check your power supply with a tester or a multimeter.  If that checks out run memtest to check the memory.  If that checks out remove ALL add on cards and see if problems go away, if they do slowly add the cards one by one (shutting down between adding hardware of course) until the problem reappears. IF nothing changes at that point, I would say its the cpu or the motherboard, unfortunatly I don't know of a way to really test either, aside from looking for physical damage on the board.  I almost never run into a blown cpu in this situation, so it is probably your motherboard if you get to this point.  As far as good mobos go I use Gigabyte or Asus although I have been using Gigabyte more and more because Asus support sucks.

Totally Agree that this is the best method, although I prefer to use a Power supply tester ( if you have one ). 

Also I agree with the Gigabyte, Asus comment only reverse them for me.

---

### Post by kcox5342 on 2009-12-28
Thanks for the quick responses.  I looked at the motherboard and don't see any blown capacitors.  I also replaced the power supply a month or so ago, it's got 650 watts now so it ought to be good.  I've run memtest on this machine and got weird results - after one crash, running memtest I got a screen full of crazy errors right off the bat, then I shut it off and let it cool for 20 minutes, and running memtest upon startup, everything looked normal again.

I guess my next question is, how do I know which motherboard to replace it with?  I would like something which can take the AMD 2X3.0Ghz CPU and the RAM that came with it, as well as my two TV tuner cards (or more!) and four SATA HDDs.  The options at Amazon and Tigerdirect are plentiful and confusing, and I know most of them aren't what I need.  What do I look for to narrow down my search?

And while I'm buying a new one, is it possible to get an optical or coaxial digital audio output?  This current motherboard promised 5.1 Surround Sound and came with six headphone-looking jacks which I have no idea what to do with.

---

### Post by natravis on 2009-12-28
> **kcox5342 said:**
> I've run memtest on this machine and got weird results - after one crash, running memtest I got a screen full of crazy errors right off the bat, then I shut it off and let it cool for 20 minutes, and running memtest upon startup, everything looked normal again.

Well this indicates that something is acting up once it gets a little heat from use. That could be RAM, CPU, or a component on the motherboard but out of the choices, RAM is most likely and most easily tested. Test each stick (one at a time) in the first (usually labeled 0) slot and see if you get one that fails while the others pass. If not, test sticks in first and second, then first, second, third, etc. Also, if you are running Memtest 86+, you should be able to look at the error and see where in the memory it is failing, i.e. if you have 2x512MB of ram and it reports a failure at 896MB, then it is either your second stick or slot that is bad. Let us know if you don't understand anything there and I will try to explain it better.

---

### Post by Raistlin355 on 2009-12-28
> **natravis said:**
> Well this indicates that something is acting up once it gets a little heat from use. That could be RAM, CPU, or a component on the motherboard but out of the choices, RAM is most likely and most easily tested. Test each stick (one at a time) in the first (usually labeled 0) slot and see if you get one that fails while the others pass. If not, test sticks in first and second, then first, second, third, etc. Also, if you are running Memtest 86+, you should be able to look at the error and see where in the memory it is failing, i.e. if you have 2x512MB of ram and it reports a failure at 896MB, then it is either your second stick or slot that is bad. Let us know if you don't understand anything there and I will try to explain it better.

Just to add, if the RAM modules test fine, don't forget the video card memtest tests this along with the RAM

---

### Post by Raistlin355 on 2009-12-28
> **kcox5342 said:**
> 
I guess my next question is, how do I know which motherboard to replace it with?  I would like something which can take the AMD 2X3.0Ghz CPU and the RAM that came with it, as well as my two TV tuner cards (or more!) and four SATA HDDs.  The options at Amazon and Tigerdirect are plentiful and confusing, and I know most of them aren't what I need.  What do I look for to narrow down my search?

And while I'm buying a new one, is it possible to get an optical or coaxial digital audio output?  This current motherboard promised 5.1 Surround Sound and came with six headphone-looking jacks which I have no idea what to do with.

Well as far as a new mobo your gonna get all kinds of suggestions, mine would be be (based on what you have typed above): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318")
or a Gigabyte equivalent.  However before you just start replacing stuff make sure to run the thorough tests that have been described here, all are good advise.

---

### Post by ovid9 on 2009-12-28
As far as a decent motherboard, here's the one I'm using. While I'm not 100% certain which CPU you have, this board can handle a variety of options. One of the best for the price. I have no complaints about it. 
 
Disclaimer, I do not work for gigabyte or newegg. This is just the link to the board.
 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128395](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128395)
 
Also, just because the PSU is new and rated for 650watts, doesn't mean it couldn't still be an issue. Some PSUs are...less well built than others and can do funky things. But I defer to those who have posted above me and are probably far more knowledgeable on the subject at hand.
 
Edit: Raistlin & I posted similar ones.  Don't know if you have an ATX or micro-ATX though.

---

### Post by doas777 on 2009-12-28
tbh, i troubleshoot around the mobo. if everything else is running fine, it;s probably it's fault. just be sure to test your ram carefully though. a study a few years ago, showed that 9 out of 10 canadian Pc techs would misdiagnose a bad mem module as a faulty motherboard, because they have simmilar symptomatology.

---

### Post by kcox5342 on 2009-12-28
Thanks again to all who have responded.  I have four RAM slots, with the leftmost two having 1GB sticks.  They're not officially numbered, but to make this discussion easier, I'm gonna call the leftmost one #1 and count up from there.  I've pulled the RAM in slot #2, and I'm running memtest.  I sincerely hope one of the two is the culprit, since the system could easily run with 1GB.

How long should I run memtest on each stick?  I've tried it before and could never tell when it was done.

I'm also reasonably certain this is a full sized motherboard.

---

### Post by lavinog on 2009-12-28
Sometimes, I find that pulling the memory out and reseating it fixes many problems.
Also did you overclock your system?  Try setting your bios settings to a safe setting (Some bios setups have a optimal and a safe or default setting)

---

### Post by lavinog on 2009-12-28
> **kcox5342 said:**
> 
How long should I run memtest on each stick?  I've tried it before and could never tell when it was done.

If it is a heat related issue, you may need to go through a couple of passes.  I don't think you would need to do more than 3 though.

To speed things up, do one pass with each module first...if you don't get any errors try again with more passes.

---

### Post by kcox5342 on 2009-12-28
First RAM stick failed after like 20 minutes.  I didn't see any address or anything in the fail-page, but I did take a digital snapshot of it for future reference.  I'll let it cool for a few minutes and then... Round two!  Fight!!

Also, I have not overclocked this system.  Two 3Ghz processors is plenty for me.  When I was a kid, computers had a single processor, which ran at one megahertz... uphill, both ways!

---

### Post by doas777 on 2009-12-28
> **kcox5342 said:**
> First RAM stick failed after like 20 minutes.  I didn't see any address or anything in the fail-page, but I did take a digital snapshot of it for future reference.  I'll let it cool for a few minutes and then... Round two!  Fight!!

Also, I have not overclocked this system.  Two 3Ghz processors is plenty for me.  When I was a kid, computers had a single processor, which ran at one megahertz... uphill, both ways!

if you replace the ram, make sure that your voltage matches that provided by the board. thedifferance between 1.8v and 2.0v can really ruin your day

---

### Post by kcox5342 on 2009-12-28
What memtest's round-one failure looked like:

[[IMG]http://img684.imageshack.us/img684/2614/1001785p.th.jpg[/IMG]](http://img684.imageshack.us/i/1001785p.jpg/)

(Click to enlarge)

Round two is at the thirteen minute mark and still going, which is 5 minutes longer than the first go-round.  My fingers are crossed!!

---

### Post by lavinog on 2009-12-28
428Mhz?
does the other module say the same thing?

---

### Post by kcox5342 on 2009-12-28
> **lavinog said:**
> 428Mhz?
does the other module say the same thing?

Yes, it does.  And it passed one round of memtesting, although it failed to boot from the HD shortly thereafter.  Why, what's the matter?

---

### Post by Bartender on 2009-12-28
To answer your question, memtest will just keep looping thru its test routines until you tell it to stop.  You could walk away for a week and when you came back it'd still be testing.

Most comments I've read say that ANY reported faults means toss the RAM.  I wouldn't go into this hoping for one good run out of four and you can call it good.

Another idea might be to take your RAM to a shop.  A good shop should have a dedicated RAM test jig.  You plug the RAM directly into the tester and test it.  This might cost you a few bucks but at least that way you're taking the motherboard out of the picture.

---

### Post by lavinog on 2009-12-28
> **Bartender said:**
> 
Most comments I've read say that ANY reported faults means toss the RAM.


There was a bug in older versions of memtest that reported faults when certain input devices were plugged in.

---

### Post by natravis on 2009-12-29
> **lavinog said:**
> There was a bug in older versions of memtest that reported faults when certain input devices were plugged in.

Operative phrase being "older". Presumably, he just downloaded this per our recommendation.

OP, if it fails Memtest repeatedly, then its dead RAM or slot. Also, your error count in Memtest is @ 94000+. No round two needed; we know something is absolutely broken. Easy to test either as long as you have one known good piece of RAM but you run the chance of messing it up with a bad slot (not likely but possible). As one other said, taking it to a shop with a RAM tester would also be an easy way and they shouldn't charge you much, if anything. They literally will stick it in, look at it, then pull it out. I know GeekSquad's do not have these devices (ex-agent).

---

### Post by kcox5342 on 2009-12-29
I've been running the version of Memtest that's on the hard drive installed with Ubuntu 9.04.  If there's a need for a newer version, tell me which Live CD I need.

---

### Post by Bartender on 2009-12-29
If you want to get a second opinion, just google memtest.  It's available as a download.

I see there's a Memtest 86+ now.  

Looks like there's an .exe for thumb drive on this page if you don't have a floppy drive. I'm pretty sure at least one of these can be used to burn to a CD also..

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

As natravis noticed, you're getting thousands of errors, not three or four, so something's definitely not right.  I think you can narrow the problem down to some extent.  

Tell me is this sounds like a plan.  If you run memtest with one stick of RAM in place, and you get thousands of errors with each stick, then that tells us it's probably not the RAM.  The likelihood of all your RAM failing catastrophically at the same time is slim.

If you can run memtest outside of the #1 slot, try it again, one stick at a time, in the next slot.  If you're still getting thousands of errors with each stick, then that tells us it's probably not the first slot.  Chances of all your RAM being bad = extremely low, chances that two of your slots are bad = not likely.  At least I wouldn't think so.  There must be a chip on the motherboard that controls RAM traffic, and if that's failing I imagine it would affect all the slots (?)

I guess it wouldn't really matter if you narrowed it down to slot or motherboard, because either way you're going to replace the motherboard, eh?

---

### Post by kcox5342 on 2009-12-29
The first stick of RAM failed spectacularly in slot #1, but the other stick of RAM passed twice in the same slot.  So I've kept the one and set aside the other for now.  1GB should be adequate at present.  However, I have two HDs with Ubuntu installed (one 8.04 and one 9.04) and neither of them would boot to completion after the memtest passed.  Also, if this had been a heat-related issue, I would expect the second stick to fail quicker than the first, but it didn't.

One of the other problems this machine has been throwing at me is some sort of graphical-crash.  I don't know what to call it, so I can't easily Google it, but back when it would boot, at times the screen would scramble and freeze and require a hard reboot.  Here's an example: [http://img684.imageshack.us/i/1001762.jpg/](http://img684.imageshack.us/i/1001762.jpg/)  It takes what's on the screen, looks like it has some sort of refresh-rate sync meltdown, and scrambles it while locking up.  I had tried playing with the NVIDIA driver to see if it helped, but it did not.  This was part of the reason I did a fresh install onto a spare HD, to see if the problems would persist.  And they did.  It even did this while I tried to boot from the HD yesterday, halfway through the boot process.  Back when it would boot, it would only crash like this when I was sitting at the machine (remember, it was used as a server, so a lot of the time I was elsewhere using it, and for a long time that worked fine.)  It would do this during local (but not network) mythtv-frontend TV viewing, OpenArena, and when I FTP'd files from my Mac over the LAN - but not small files, I could safely do a gigabyte or so before worrying.  Also, oggenc used to segfault on me like mad.  Does this add support to the bad motherboard theory?

---

### Post by cascade9 on 2009-12-29
> **lavinog said:**
> 428Mhz?
does the other module say the same thing?

> **kcox5342 said:**
> Yes, it does.  And it passed one round of memtesting, although it failed to boot from the HD shortly thereafter.  Why, what's the matter?

Thats out of spec range. It should be 400Mhz (DDR 800) tops. The timings (CAS 5-5-5-18) seems way to tight as well. 

Normally that would be a sign that you have overlclocked. By about 7%, just on speed....and the CAS rating make it worse. 

If its a 3.0 Ghz X2 then its one of 2 6000+ (there are 2 versions f that CPU.) Either way, they are at the edge of what a X2 CPU is capable of, and even  a7% overclock could be causing at least some, if not all of your problems. 

I would go into BIOS and make sure that its not overclocked. 

Also, if you go to get a new board, your looking for socket AM2 or AM2+, DDR2, i you have a microATX case, then its got to be a micro ATX board. If its a full ATX case (there should be a fair bit of sapce at the bottom of the case) then you could get a full ATX motherboard. 

That video issue could be caused by overclocking as well, if you are using the onboard video.

---

### Post by kcox5342 on 2009-12-29
OK, I've found the overclock setting page in the BIOS.  The top option, "Overclock Navigator", has been set to "Normal", versus "Automate Overclock" or "Manual Overclock".  Everything else is greyed out when it's set to "Normal", which I'm presuming means no overclocking.  I've never touched any of these settings before.

A quick check of Memtest with the non-failing RAM also shows not just 428Mhz but also the CAS at 5-5-5-18.  CAS is a new concept to me, and after a quick Googling, I'm still clueless about what, exactly, CAS measures, why 5-5-5-18 isn't normal, how a user like me could alter it, and why it might be part of my problem.  If there is a CAS FAQ or something similar worth reading, please point me in its direction.

Edit:  This page looks like it might be what I'm after, FAQ-wise:
[http://www.hardwarehell.com/articles/ras_cas.htm](http://www.hardwarehell.com/articles/ras_cas.htm)

---

### Post by cascade9 on 2009-12-29
If it says "CPU Frequency  200.9" then you shouldnt be overclocked. 

That is actually dodgy IMO, it should be '200.0'. Its not the 7% overclock that the RAM settings would make it appear, but still..not good. Some motherboards by some manufacturers used to do this all the time, give things a 0.5-1.5% overclock as 'stock' to make them benchmark better. 

Heres what I would do, but please, read cafefully. 


Go back to BIOS

change to 'manual overclock'. Drop the CPU frequency to 200.0. ((I'm not happy with the following but its the only way I can see to do what might help) Go down to 'DRAM configuration', go to 'timing mode', select 'max memory clock', then go to 'memory clock value or limi' *scratches head* it seems that it should be at DDR400 stock, but that might be an older revision of the BIOS. Anyway, if its at 400, try 533...if its at 800, try 667, 533 or 400 (I would go for 667 if its at 800). 

Restart. 

If you start memtest and it still says '428mhz/DDR857' then something is badly wrong....

For anyobdy else trying to help with this, here the BIOS .pdf from Biostar on that board-

[ftp://ftp.biostar-usa.com/manuals/TFORCE%20TF7050-M2/bios_TF7050-M2.pdf](ftp://ftp.biostar-usa.com/manuals/TFORCE%20TF7050-M2/bios_TF7050-M2.pdf)

I really dont know if that will help...and if you are going to try this, remember that if it fails (which it shouldnt but its always possible) you could get locked out with no way to boot. If that happens, you can take the side off the case, and either find the clear CMOS switch (I cant find directions online easy) and move it over for a few minutes, then move it back, or remove the battery for a few minutes, then put the battery back. Then you should go back to stock everything. You will have to setup your hdd, etc, again, but its not as bad as 0 bootage. 

BTW, there are a few other things you can do in BIOS that will not hurt, and may help. 

Main Menu- 
Go to 'standard CMOS features'
Try turning the floppy drive off, if its on (and you dont use one....no-one uses a floppy anymore, right?) 
Set it to 'halt on- all errors' 

Main menu- 
Go to 'advanced BIOS features'
set 'quick power on self test' to 'disabled' (this normally makes the board do more system checks on starting, so it takes longer to boot, but might find issues that are not normally found. I'd turn it back on if nothing happens once its been set to 'disabled' and booted fine)
Full screen logo show- disabled. 
summary screeen show- enabled. 

Main menu-
Go to 'integrated peripherals'
Onboard FDC controller- disabled. (if you dont have a floppy) 
Onboards serial port- disabled (if you dont use a serial port thingsie...nobody does anymore,right?)
Onboard Parallel Port- disabled  (if you dont use a par port thingsie...nobody does anymore,right?)


Well, thats my essay done for today LMAO. 

I really hope that helps ;)

---

### Post by cascade9 on 2009-12-29
I really hope tat this was your edit and I wasnt having a blonde moment and missing it before LOL-

> **kcox5342 said:**
> A quick check of Memtest with the non-failing RAM also shows not just 428Mhz but also the CAS at 5-5-5-18. CAS is a new concept to me, and after a quick Googling, I'm still clueless about what, exactly, CAS measures, why 5-5-5-18 isn't normal, how a user like me could alter it, and why it might be part of my problem. If there is a CAS FAQ or something similar worth reading, please point me in its direction.

CAS...er....easiest to just quote wiki- 

> **Column Address Strobe (CAS) [latency]("http://en.wikipedia.org/wiki/RAM_latency")**, or **CL**, is the delay time between the moment a [memory controller]("http://en.wikipedia.org/wiki/Memory_controller") tells the memory module to access a particular [memory column]("http://en.wikipedia.org/wiki/RAM#Memory_hierarchy") on a [RAM]("http://en.wikipedia.org/wiki/Random_access_memory") memory module, and the moment the data from given array location is available on the module's output pins.

[http://en.wikipedia.org/wiki/CAS_latency](http://en.wikipedia.org/wiki/CAS_latency)

Basicly, the lower the number, the faster the 'I want this info from this bit of RAM' message goes though the system. 

CAS 5-5-5-18 isnt that amazing, but its lower than a lot of older DDR2 (by older I mean 'not the last year, as time goes on speed goes up, CAS ratings drop. When I got my machine, early 2008, 7-7-7-x was pretty quick, and 5-5-5-x was _very_ top end RAM IIRC). For any given RAM, dropping the CAS rating is similar to uping the frequency. So not only is your DDR2 running faster than your motherboard should be running it (it says DDR2 800 max..er..somehwere I looked a while ago) but your also running tight timings.

---

### Post by kcox5342 on 2009-12-29
Thanks for all your help.  I'm in the DRAM configuration, but I can't find "timing mode".  I've got:

DQS Training Control - Skip DQS
CKE base power down mode - Disabled
CKE based powerdown - Per Channel
Memclock tri-stating - Disabled
Memory Hole Remapping - Enabled
Auto Optimize Bottom IO - Enabled
Bottom of UMA DRAM [31:24] - FC
DDRII Timing Item - Disabled

There's also a lot of greyed out items which get ungreyed when I enable the last one.  But I don't see "max memory clock" or anything which looks measured in mhz or has three-digit numbers next to it.  Here's what I could play with if I enable it:

TwTr Command Delay - 3 bus clocks
Trfc0 for DIMM0 - 75ns
(Ditto for Trfc1 - Trfc3)
(Twr) Write Recovery Time - 6 bus clocks
(Trtp) Precharge time - 3 clocks
(Trc) Row Cycle Time - 26 bus clocks
(Trcd) RAS to CAS R/W Delay - 6 clocks
(Trrd) RAS to RAS delay - 5 clocks
(Trp) Row Precharge Time - 6 clocks
(Tras) Minimum RAS Active T - 18 bus clocks

Edit:  Typed too soon... it's not in the DRAM Configuration submenu, it's in the main Overclock Navigator page.  And it's set to 400 by default.

---

### Post by kcox5342 on 2009-12-29
OK, switched to 533 and it's still behaving the same, but memtest does give different numbers:

Settings: RAM: 272MHz (DDR 545) / CAS : 4-4-4-12 / DDR-2 (64 bits)

---

### Post by cascade9 on 2009-12-29
Stiil dofgy, and still the RAM is running faster than specified. Not as badly, but thats seriously uncool. 

You could try running memtest again to see if its still giving errors. 

If your memtest still comes back faulty, you could also try updating the BIOS. which can be extra fun now that upgrading from, you guessed it, windows, is the most common way these days.

I have no idea if updating BIOS will work, hopefully it does, but I have this feeling that  your motherboard has some serious fault. :( 

You can try RMAing it (Returned materials authorisation) but that can take weeks in my experience,a dn sometimes its not worth it (I've heard of 'known dodgy' boards being claimed to be fine, and being sent back with a technicians bill) If thats too long, you might have to get a new motherboard. 

If it makes you feel any better, think of it as a minor upgrade,  if your running the onboard video on your current board, a 8200 (or even 8100 if you want the cheapest you can get) would be an upgrade on your current GPU. 

Maybe somebody else will have an idea.....but I'm fresh out, sorry. 

I hate dodgy hardware, I find it oddly depressing myself. Weird, considering how much time I end up playing with bad hardware, but hey, its $$$ for me (I fix peoples computers for cash).

---

### Post by kcox5342 on 2009-12-29
When you say 8200, do you mean a Biostar TF8200, as opposed to my current TF7025?  Google shows a Biostar TF8200 but it's not showing up when I search Amazon, Newegg or Tigerdirect.

And I know what you mean about hardware failure resulting in feelings of unhappiness far beyond what one dead computer should rationally mean.  I have to keep reminding myself to look at the big picture - I'm healthy, I'm otherwise happy, my car runs, and if mythtv had to be offline for a while, Christmastime is about as good a time as any, since TV is in reruns except for constant Crotchbomber coverage, and as cool as mythtv is, it isn't going to help me get tickets to see The Addams Family Musical or Avatar.  I think the uncertainty that's the worst - if my computer popped up a screen saying "BUY A NEW MOTHERBOARD", I'd be briefly irate but overall a lot happier than this endless "Is this the problem?  How'bout this?" that I'm going through.

---

### Post by cascade9 on 2009-12-29
I meant any microATX 8200 chipset board, like this one posted way before- 

> **Raistlin355 said:**
> Well as far as a new mobo your gonna get all kinds of suggestions, mine would be be (based on what you have typed above): [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318)
or a Gigabyte equivalent. However before you just start replacing stuff make sure to run the thorough tests that have been described here, all are good advise.

You wont need to install a biostar board. Your current board has standard micro-atx mounting holes, etc, so any standard microATX will fit. 

BTW, the geforce 7025 that you have doesnt support VDPAU 

[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)

The 8200 does. 

It should reduce your CPU use when watching stuff.

---

### Post by ovid9 on 2009-12-29
Biostar?  In my limited experience, I haven't run across many good things said about Biostar's boards except they tend to be inexpensive.  When I was building my computer a few months back I was looking at one and was warned away by many more experienced people since I was building my machine for longevity.  I'm sure they work fine for many people, but...
 
As with all hardware its sort of a crapshoot.  I don't know anything about your budget, etc, but since it really seems like your RAM isn't the problem, you can get a high quality board for $70-90.  
 
I work in car parts, so I understand the frustration of "what if that doesn't fix it" but there's always a balance of "how much effort do I put into making 100% certain this is the problem" and "I'm fairly certain this is it, can I afford to eat $90 if it doesn't fix my problem?"
 
Unless you can get it RMA'd under a warranty of some sort, I'd really suggest a different manufacturer like Gigabyte or Asus if replacement is the route you decide to go.

---

### Post by doas777 on 2009-12-29
> **cascade9 said:**
> 
BTW, the geforce 7025 that you have doesnt support VDPAU 

[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)

The 8200 does. 


beware the lower end of the 8000 series with ubuntu. I've had serious problems with TVOut on 83-8500 cards, so make sure if you want the more fancy features of the driver (like overscan control) that your card is fully supported. an 8800 seems to be well supported, largely due to how many of them are out there.

Op, it's time for some new Kit. I would recomend abit(if you can find one),  asus, or gigabyte for mobos. had quite a few biostar's die within 3 years.

---

### Post by kcox5342 on 2009-12-29
I've been in email contact with a techy friend of mine this morning and he had some good advice...

   Remove all the HDs and the TV tuner cards and try to boot from a LiveCD.  Which worked, I'm looking at Slax right now.  And then I imagine steps #2-#?? will be, try putting things back one at a time and see when the failure begins.  So maybe this was a TV tuner card issue?  Here's part of what I emailed to him:

   "When I was trying to reinstall a test system, I did find something weird.  When setting up mythtv, not once but twice it crashed at the same spot - when I was first scanning for TV channels.  Then I told it to forget about the first card and only use the second card, and it worked for a couple days like that, before flaking out again.  So,  maybe it's one of my TV tuner cards?"

   They're a pair of pcHDTV 5500's, btw.

---

### Post by cartisdm on 2009-12-29
> **cascade9 said:**
> I hate dodgy hardware, I find it oddly depressing myself. Weird, considering how much time I end up playing with bad hardware, but hey, its $$$ for me (I fix peoples computers for cash).

Yeah, hardware is a fickle beast.  I can't tell you how many times I've messed with testing faulty hardware.  Even motherboards that I've been 100% sure had a short in them would work just fine for days then completely crap out with the slightest change.

---

### Post by llawwehttam on 2009-12-29
To me it sounds like bad ram. If I were you I'd change it out and make sure it has decent cooling. Every time I've experienced frequent crashes ( at least ones that didn't completely kill the machine) they have been caused by my ram overheating.

---

### Post by ezsit on 2009-12-29
> I also replaced the power supply a month or so ago, it's got 650 watts now so it ought to be good.

I've replaced power supplies, brand new power supplies, because the voltages were not within spec, right from the factory. A new power supply is no guarantee that it is a good power supply.

---

### Post by cascade9 on 2009-12-30
> **kcox5342 said:**
> I think the uncertainty that's the worst - if my computer popped up a screen saying "BUY A NEW MOTHERBOARD", I'd be briefly irate but overall a lot happier than this endless "Is this the problem? How'bout this?" that I'm going through.
 
 If only it was that simple, my life (and yours, and 1000's of others) would be a lot easier....
 
 > **doas777 said:**
> beware the lower end of the 8000 series with ubuntu. I've had serious problems with TVOut on 83-8500 cards, so make sure if you want the more fancy features of the driver (like overscan control) that your card is fully supported. an 8800 seems to be well supported, largely due to how many of them are out there.
  
  Op, it's time for some new Kit. I would recomend abit(if you can find one), asus, or gigabyte for mobos. had quite a few biostar's die within 3 years.
  
  If the OP had no problems with a 7025, a 8100 or 8200 would be nothing but pure upgrade. :) 
  
  Abits dead, and the glory days of the nForce 2 (NF7-S) are long gone. After they got bought by universal they were never as good IMO. I was a huge fan of the older stuff back in the day though. 

> **ezsit said:**
> I've replaced power supplies, brand new power supplies, because the voltages were not within spec, right from the factory. A new power supply is no guarantee that it is a good power supply.

yep, same. One of the reasons why I only buy decent power supplies now (current favourites are corsair, seasonic and coolermaster for the whole case/power supply combo 'dont want to spend that much' area) 

> **kcox5342 said:**
> I've been in email contact with a techy friend of mine this morning and he had some good advice...

   Remove all the HDs and the TV tuner cards and try to boot from a LiveCD.  Which worked, I'm looking at Slax right now.  And then I imagine steps #2-#?? will be, try putting things back one at a time and see when the failure begins.  So maybe this was a TV tuner card issue?  Here's part of what I emailed to him:

   "When I was trying to reinstall a test system, I did find something weird.  When setting up mythtv, not once but twice it crashed at the same spot - when I was first scanning for TV channels.  Then I told it to forget about the first card and only use the second card, and it worked for a couple days like that, before flaking out again.  So,  maybe it's one of my TV tuner cards?"

   They're a pair of pcHDTV 5500's, btw.

Oh, snap. :| 

I should have said that ages ago, its normally the 1st thing I try. 

I'm still _very_ suspect on your motherboard being at least slightly dodgy, but how much of that is hardware, and how much of that is biostars settings, no idea. 

Hopefully it being caused by a turner card. I've never had exactly that happen, but I've had bad cards cause massive problems before *stares at creative*. If its not, at least its not a total writeoff, and a nice cheap motherboard should fix your problems *crosses fingers*

---

