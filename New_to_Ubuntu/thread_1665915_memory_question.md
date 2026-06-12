---
title: "memory question"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by garyhibdon on 2011-01-13
not sure exactly where to put this posting at, so i thought id try here.

how much memory can ubuntu 10.10 support? i know windows XP would only support 3.8gigs.

any ideas?

---

### Post by dFlyer on 2011-01-13
32 or 64 bit system?

---

### Post by garyhibdon on 2011-01-13
32 bit. sorry, thought i had put that in there.

---

### Post by Chris Edgell on 2011-01-13
I would have thought it would be the machine not the release...am I wrong?

Or maybe each has it's limits and you go by whichever one comes first...

---

### Post by mikewhatever on 2011-01-13
32 bit OSs can't see more then 4GB, but then, some of the memory addresses are reserved, so that you get 4-the reserved amount. How much is reserved depends on the machine.

---

### Post by garyhibdon on 2011-01-13
i have an asus P5KPL-am epu and it SUPPOSEDLY supports  8 gigs. thats why i was wondering. the price difference between 4 gigs and 8 gigs is like $100 so yeah

---

### Post by Verbeck on 2011-01-13
> **mikewhatever said:**
> 32 bit OSs can't see more then 4GB, but then, some of the memory addresses are reserved, so that you get 4-the reserved amount. How much is reserved depends on the machine.
how about enabling PAE?

---

### Post by cascade9 on 2011-01-13
Better question- why do you want 8GB? For most people its pointless....... 

> **Chris Edgell said:**
> I would have thought it would be the machine not the release...am I wrong?

Or maybe each has it's limits and you go by whichever one comes first...

Yes, both have limits.

---

### Post by Paqman on 2011-01-13
> **garyhibdon said:**
> i have an asus P5KPL-am epu and it SUPPOSEDLY supports  8 gigs. thats why i was wondering. the price difference between 4 gigs and 8 gigs is like $100 so yeah

Unless you're doing something really hardcore you're unlikely to see any performance improvement between 4GB and 8GB, so i'd pocket the difference if I was you.

I have 4GB, and never use most of it except when I run fat VMs. Ubuntu will run quite happily on 1GB.

---

### Post by -kg- on 2011-01-13
Really quite entertaining! :P

> **Paqman said:**
> Unless you're doing something really hardcore you're unlikely to see any performance improvement between 4GB and 8GB, so i'd pocket the difference if I was you.

Until when?  I remember years ago I had a computer that had around 38 GB of hard drive space in 3 hard drives.  People told me I was crazy to have that much hard drive space...what was I going to use that space for?  Now...***"You only have 38 GB of HD space?  How can you do anything with that?  You need more!"***

Same with memory.  I have a laptop that I bought in 2000 with WinME installed.  When I upgraded to XP, I had to increase the memory in it to the max in order to run XP with any semblance of speed.  Max memory?  364 MB.

> **Paqman said:**
> I have 4GB, and never use most of it except when I run fat VMs. Ubuntu will run quite happily on 1GB.

How much longer will 1 GB run efficiently?  4 GB?  8 GB?  I don't know, and neither does anyone else.  My little laptop is still running...I have Ubuntu 10.04 running on it, and with 364 MB it just barely runs.  It may be that Ubuntu 20.04 will just barely run on 1 GB of RAM.

If you can afford it and want it, go for it...you'll either find a use for it, or might need it in the future.  Same goes with processor cores.  Currently there is very little software that uses multiple cores to maximum effect, but I use one of them....BOINC distributed computing projects.  BOINC will use every processor core available...if you have a quad core processor, it will process 4 work units simultaneously.

32 bit Ubuntu (and Linux in general, if I'm not mistaken)_will recognize over 4 GB of RAM if you use the PAE enabled kernel.  I personally use 64-bit Ubuntu, even though I don't have over 2 GB of RAM on any of my computers.  If they have a 64-bit processor, I have the 64-bit OS installed.  I haven't had any major problems with the 64-bit kernels for several releases now.

---

### Post by 1clue on 2011-01-13
I've heard/read bad things about PAE, including a diatribe from Linus Torvalds.  If they're right, then fortunately enough I haven't ever had to use it.

Yes, 32 bit systems are limited to 4G unless they have some scheme for accessing more, such as PAE.

I'm running 12G on a 64-bit system.  If I don't have any VMs running then I don't often get above 4G used.  I have managed to run out of 6G, just barely.  I used it as an excuse to double it, but the thing is I was using all sorts of tmpfs so part of that was the tmpfs.  64-bit systems are supposedly more memory hungry than a 32 bit system.

If you use a large database under heavy load, or virtual machines, or some other service that takes huge memory, then you can run out of 4G.  You would have had to install whatever it is deliberately, I don't know of anything installed on a generic system that does that without you knowing about it.

---

### Post by garyhibdon on 2011-01-13
ok i guess heres what it boils down to. my comp has an asus p5kpl-am epu mother board and a pentium duo core runnin 3.1 Ghz per @ 1.99 gigs of ram. i used to over clock computers to WAY over their "max capacity" and thats the goal for this comp. its the reason i picked the components it has in it. the issues im having are ram, and the ability to overclock it any further ( im assuming theres some software to do so further, but thus far ive found nothing). im shooting to have a computer pushing ATLEAST 6 Ghz w/ max ram but its turning out to be quite a load of work, considering this computer started with windows XP, especially considering XP couldnt control half of my components to their fullest capabilities.



as an after thought, what exactly is PAE and what are its uses/designations?

---

### Post by -kg- on 2011-01-13
> **1clue said:**
> I'm running 12G on a 64-bit system.  If I don't have any VMs running then I don't often get above 4G used.  I have managed to run out of 6G, just barely.  I used it as an excuse to double it, but the thing is I was using all sorts of tmpfs so part of that was the tmpfs.  64-bit systems are supposedly more memory hungry than a 32 bit system.

Well, I'm running Lucid 10.04 on an AMD 64 3200+ processor with 1 GB of RAM.  Of course, I'm running BOINC, processing Seti@Home work units, my browser, and Rhythmbox (playing Coast To Coast AM).  According to System Monitor, I'm running 100% processor, with just under 60% of RAM used, and around 50.1 MB of swap space used.  Doesn't seem to be too memory hungry to me.

> ...the issues im having are ram, and the ability to overclock it any further...

I don't think this issue has to do with quantity of RAM...I think your issue is with quality of RAM (or cooling...or your processor/front end's ability to handle that level of over-clocking).  Generally, the problems start when you approach or exceed the limit of your specific hardware's limit of capability, not the "amount of hardware" you have.  No OS or software will magically adjust that limit.

---

### Post by mikewhatever on 2011-01-13
> **garyhibdon said:**
> ...



as an after thought, what exactly is PAE and what are its uses/designations?

[https://secure.wikimedia.org/wikipedia/en/wiki/Physical_Address_Extension](https://secure.wikimedia.org/wikipedia/en/wiki/Physical_Address_Extension)

Search for pae kernel in the repositories.

---

### Post by garyhibdon on 2011-01-13
i dont think i explained myself that well. im wanting to overclock it, the core temp is still very low, and its running smoothly, so i have no real issues. i just was trying to find out the maximum ram that 10.10 32bit would utilize so that i could max it out. and then im going to continue my search to overclock the cpu further. its a playtoy. no real use for doing this, im doing it just because i can and i want to. im well read on the procedures as far as the bios and hardware are concerned, so thats not an issue.

---

### Post by robert shearer on 2011-01-13
Going at it from another direction.....
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

perhaps faster with less stress on hardware..??

---

### Post by garyhibdon on 2011-01-13
Thank you!!!!!

---

### Post by garyhibdon on 2011-01-13
> **robert shearer said:**
> Going at it from another direction.....
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

perhaps faster with less stress on hardware..??


definetly a different approach to the task, but not exactly what im shooting for, though i appreciate the effort. im shooting for numbers i can see, and the initial times required to load the os into the ram doesnt really seem to equal out with the speed you "gain"

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> i have an asus P5KPL-am epu and it SUPPOSEDLY supports 8 gigs. thats why i was wondering. the price difference between 4 gigs and 8 gigs is like $100 so yeah
  
  Thats got a max RAM of 4GB, thats chipset limit (g31 chipset) 
  
 > **-kg- said:**
> If you can afford it and want it, go for it...you'll either find a use for it, or might need it in the future. Same goes with processor cores. Currently there is very little software that uses multiple cores to maximum effect, but I use one of them....BOINC distributed computing projects. BOINC will use every processor core available...if you have a quad core processor, it will process 4 work units simultaneously.
 
 
 There is point after which it becomes easier, cheaper (and faster!) to get a 'reasonable' amount of RAM for the time, and if you need more upgrade later.

> **garyhibdon said:**
> i dont think i explained myself that well. im wanting to overclock it, the core temp is still very low, and its running smoothly, so i have no real issues. i just was trying to find out the maximum ram that 10.10 32bit would utilize so that i could max it out. and then im going to continue my search to overclock the cpu further. its a playtoy. no real use for doing this, im doing it just because i can and i want to. im well read on the procedures as far as the bios and hardware are concerned, so thats not an issue.

RAM either has '0' effect on overclocking, or it actually HURTS your max overclock. Not that you have to worry about that, you've only got 2 RAM slots...

> **garyhibdon said:**
> definetly a different approach to the task, but not exactly what im shooting for, though i appreciate the effort. im shooting for numbers i can see, and the initial times required to load the os into the ram doesnt really seem to equal out with the speed you "gain"

Want to load fast? Minimal install, then xfce4 or lxde. No unneeded junk. That is going to help your boottimes more than overclocking will. 

A faster HDD (or better yet a SSD) makes more difference to boot times than overclocking as well.

---

### Post by garyhibdon on 2011-01-13
im looking for run fast, not just load fast. i do EVERYTHING on this comp and sometimes, the loading becomes a bit of an issue. well, it is to me because i have higher expectations for my computer, this has become the poster child for people i know to kill microsoft. lol its petty, but i need it faster in all aspects.

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> im looking for run fast, not just load fast. i do EVERYTHING on this comp and sometimes, the loading becomes a bit of an issue. well, it is to me because i have higher expectations for my computer, this has become the poster child for people i know to kill microsoft. lol its petty, but i need it faster in all aspects.

Minimal install +xfce4 (or fluxbox, or lxde but personally I dont like lxde) is still the way to go. 

Most of the time,  unless you are running wayyyyy to many tabs in a brwoser, or doing a lot of multitasking, the CPU will be throttled down, so overclocking wont help as much you might think.....

---

### Post by garyhibdon on 2011-01-13
i do a severe amount of multitasking. once upon a time a had a pentium 1 overclocked to 1gig of output. thats basically the idea im shooting for. im known to have 3 and 4 instances of diablo 2 running as well as a music player and a couple of internet tabs open. my mind works too fast for my own good and every time i happen to have a "wild tangent" thought, ill follow it, no matter the work load on whatever im using. basically im working towards the extreme computing world.



EDIT: and yes im aware that its kind of pointless, but its a hobby of mine.

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> i do a severe amount of multitasking. once upon a time a had a pentium 1 overclocked to 1gig of output. 

Now, now, no need to move into complete fantasy.

A pentium 1 would be lucky to break 300MHz. IIRC 351Mhz was the reccord with a P1.

---

### Post by garyhibdon on 2011-01-13
ok. never said it worked long. it actually overheated and had a . . "meltdown"



you made me wonder. so i looked. now i feel as dumb as this guy


[http://www.overclockers.com/forums/showthread.php?t=626984](http://www.overclockers.com/forums/showthread.php?t=626984)

---

### Post by garyhibdon on 2011-01-13
at the moment, according to cpuid-z ive got 3390mhz output, just for reference

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> ok. never said it worked long. it actually overheated and had a . . "meltdown"

you made me wonder. so i looked. now i feel as dumb as this guy

[http://www.overclockers.com/forums/showthread.php?t=626984](http://www.overclockers.com/forums/showthread.php?t=626984)

Its simply impossible to get a P1 to 1GHz. Ever. They dotn have a high enough multiplier, 3.5 is the max 'from the factory' and even if you found an unlocked P1 its still goignt o be limited to 5.5 on a super socket 7 board. Times that by 100MHz (super socket 7 FSB) you get 550MHz. Its possible that you could find a super socket 7 that does 120MHz FSB, for 660MHz.

> **garyhibdon said:**
> at the moment, according to cpuid-z ive got 3390mhz output, just for reference

Measuring in pure MHz is pointless. You could have a CPU with slower MHz and be faster, quite easily.

---

### Post by garyhibdon on 2011-01-13
> **cascade9 said:**
> Its simply impossible to get a P1 to 1GHz. Ever. They dotn have a high enough multiplier, 3.5 is the max 'from the factory' and even if you found an unlocked P1 its still goignt o be limited to 5.5 on a super socket 7 board. Times that by 100MHz (super socket 7 FSB) you get 550MHz. Its possible that you could find a super socket 7 that does 120MHz FSB, for 660MHz.
you didnt read that forum evidently. that was the power output it was reporting. not necessarily the ACTUAL output unless 1000mhz isnt a gig

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> you didnt read that forum evidently. that was the power output it was reporting. not necessarily the ACTUAL output unless 1000mhz isnt a gig

The power output? *blinks* Either you've linked to the wrong forum, or are conused, or both. 

I'll stick by what I was saying. Its IMPOSSIBLE to run a p1 at 1GHz. Ever. Even with liquid nitrogen cooling, becuase you simply cant set a socket 7/super socket 7 motherboard that high. 

there is a reason why the K6-3s (which were devil overclockers, the best CPU ever realsed in s7/ss7 format) toped out at about 660MHz. Iit wasnt a chip limit, it was a chipset/motherboard limit.

---

### Post by garyhibdon on 2011-01-13
so your telling me that my motherboard is the reason that my duo core will only clock 3.14Ghz?

---

### Post by cascade9 on 2011-01-13
> **garyhibdon said:**
> so your telling me that my motherboard is the reason that my duo core will only clock 3.14Ghz?

No, I was saying that you cant possibly have got a P1 to 1GHz. Considering that the link you provided was to a p1 overclocking disuccion, I'm guessing you are confused. 

BTW, you could at least be consistent. Above you said "3390mhz" now you are saying "3.14Ghz" (3140MHz). Which is it? :P

---

### Post by garyhibdon on 2011-01-13
cpuid-z reported 3390mhz
mybios says 3.14ghz.
computers never lie

---

### Post by garyhibdon on 2011-01-13
ok so i got bored and started playin in the bios. o/c WAY too high and had to do a hard start.
 
 
turned it back on and got "the black screen of fail"
 
uncompression error
 
 -- system halted
 
any ideas?

---

### Post by cascade9 on 2011-01-13
Probably CPU-Z making a mistake, its done it in the past.....

*edit- um, seriously? Dont try insane overclcks, they lead to sweat and swearing. Research before you go pushing things, and remember that a decent Core2Duo (let alone a Core2Quad) is expensive these days. If the magic smoke comes out, overclocking is NO FUN AT ALL.

---

### Post by garyhibdon on 2011-01-13
it wasnt anything insane. it registered 3.31ghz with low mb/core temps so i restarted to let it run and i gave me that error message. no crazy overclock and no smoke. pretty much need a new install of ubuntu huh?

---

### Post by cascade9 on 2011-01-13
Low temps dont mean much at all. If they did, you could overclock to 10GHz+ with liquid nitrogen. 

Different motherboards, CPU, RAM and power supplies have different limits. ust because CPU 'X' overclocked to 3.5GHz on motherboard 'Y' with power supply 'Z' got to 3.X GHz doesnt mean that your setup will do the same.....even if its exactly the same on paper.

---

### Post by 1clue on 2011-01-13
What you're saying doesn't really make much sense, except that you want to overclock everything to the point where it melts just because there's a setting for it.

Go buy better hardware.  Then run it at the speed it's designed to run at.  Or maybe have your parents buy it?  It seems that you don't really care much about hardware failure.

There's a law of diminishing returns with overclocking, the faster you push the clock the slower the bus can get the lines to the proper voltage spec.  Just because your system says it's twice as fast as stock does not in any way mean you have twice the computing power.

3 copies of diablo?  You're talking about the game right?  Seriously?  WTF?

Spend your time on things that eliminate bottlenecks in your system without causing instability.  That link about running the entire OS in RAM is very interesting, it may give you some significant and worthwhile gains.

---

### Post by Paqman on 2011-01-13
> **-kg- said:**
> 
How much longer will 1 GB run efficiently?  4 GB?  8 GB?  I don't know, and neither does anyone else.  My little laptop is still running...I have Ubuntu 10.04 running on it, and with 364 MB it just barely runs.  It may be that Ubuntu 20.04 will just barely run on 1 GB of RAM.

If you can afford it and want it, go for it...you'll either find a use for it, or might need it in the future.

IMO you'd be far better off buying what you actually need now, then upgrading if you need more in the future, as it'll be cheaper by then. But hey, it's your money, do what you like!

---

### Post by garyhibdon on 2011-01-13
hardware malfunctions are as serious a worry for me as they are for anyone else.and im not doing it "just because it can", im doing what i can with what i have. i bought this setup last year and it runs great. just looking for a little more speed. if i "bought the equipment i want" everytime it slowed down, id never have money left over just because technology is CONSTANTLY moving forward, and it typically seems to be at an exponential rate. while i understand the points of view of everyone, i suppose i'm just not explaining myself that well, so ill just go back to research. thank for all the ideas though
and yes, 3 instances of diablo 2 the game.
 
i run several bots pretty constantly. and i like to actually play once in a while

---

### Post by cascade9 on 2011-01-14
> **1clue said:**
> What you're saying doesn't really make much sense, except that you want to overclock everything to the point where it melts just because there's a setting for it.

Go buy better hardware.  Then run it at the speed it's designed to run at.  Or maybe have your parents buy it?  It seems that you don't really care much about hardware failure.

There's a law of diminishing returns with overclocking, the faster you push the clock the slower the bus can get the lines to the proper voltage spec.  Just because your system says it's twice as fast as stock does not in any way mean you have twice the computing power.

I'm not quite as anti-overclocking as you 1clue, but in the hand of the inexperienced, or overly hopeful its not a geat idea. 

BTW,agree 100% on 'pushing things can make the computer slower'. To parahrase, higher clocks do NOT always equal faster. Its actually normal for there to be a 'sweet spot', a point where a decrease OR increase to the clock slows the system down.  

> **garyhibdon said:**
> hardware malfunctions are as serious a worry for me as they are for anyone else.and im not doing it "just because it can", im doing what i can with what i have. 

If hardware malfunctions are a worry, then you shouldnt be going around attempting overclocks that lead to serious errors. 

> **garyhibdon said:**
> i bought this setup last year and it runs great. just looking for a little more speed. if i "bought the equipment i want" everytime it slowed down, id never have money left over just because technology is CONSTANTLY moving forward, and it typically seems to be at an exponential rate. while i understand the points of view of everyone, i suppose i'm just not explaining myself that well, so ill just go back to research. thank for all the ideas though
and yes, 3 instances of diablo 2 the game.
 
i run several bots pretty constantly. and i like to actually play once in a while

You could run D2 bots on a different computer on a network easy enough.. 

To get a good overclock, you need 3 things- research, restraint and an eye for details. You've already said that you've got limited restraint (post #22 in total, and 'bored, playing in the BIOS and set the overclock way to high'), you dont have an eye for detail (quoting different speeds from BIOS and CPU-Z) your research is laughable....1GHz p1 (yawn) and finally "I'm shooting for 6GHz..." Yeah, right. Without liquid nitrogen, your not.

IMO, you would be best of not playing with overclocking.

---

### Post by 1clue on 2011-01-14
Both you guys who referenced my post took it to be much more antagonistic than I meant it.

I'm not really anti-overclocking.  I won't do it on my hardware because reliability is much more important than speed, and the system is more than fast enough for what I'm doing now.  And because I don't have the patience for it.

Gary, I don't see anyone who's actually antagonistic to you.  Thing is though, you're on a Linux forum.  Don't throw crap out there to BS us.  There's always somebody out there who knows EXACTLY what you're talking about better than you do, and some of them will call you on it.

So stop exaggerating and people will stop calling you on it.

Use some valid-to-your-case benchmark as an indicator for your success.  For example, running 3x your game and a video, measure CPU load over an hour span.  If you get too carried away with your clock, then you lose performance.

---

### Post by Paqman on 2011-01-14
> **garyhibdon said:**
> just looking for a little more speed.

More RAM is not the place to go looking for that, unless you're short on it in the first place.

---

### Post by Paqman on 2011-01-14
> **garyhibdon said:**
> just looking for a little more speed.

More RAM is not the place to go looking for that, unless you're short on it in the first place.

---

### Post by garyhibdon on 2011-01-14
i only have 2 gigs atm, and i was going to upgrade that anyway. i was just trying to get ideas, but as i said, i dont seem to be able to properly express what it is i'm attempting to accomplish

---

### Post by dFlyer on 2011-01-14
Use a pae kernal, and I believe you can use as much memory as you want.

---

### Post by garyhibdon on 2011-01-14
> **dFlyer said:**
> Use a pae kernal, and I believe you can use as much memory as you want.


i have been able to find several links on what pae is, but nothing as to how to initiate this technology. any recommendations?

---

### Post by garyhibdon on 2011-01-14
and by the way, just noticed that i had missed a couple of posts, so i thought i'd respectively answer in kind to each.
First off, i cant help that cpu-z and my bios are not giving the same information, and thats ALSO in reference to the multiple cracks at the 1ghz p1. just telling you what the bios stated. the computer didnt even run long enough to load any kind of windows. it fried itself in mere moments.
Secondly, the comment about a 6Ghz computer was NOT in ANY  way shape or form saying that i wanted THIS computer AS IT SITS to do that, i said im working TOWARDS that goal.
Lastly, these confusions are the reason that i had mentioned the fact that nothing i was saying was being taken as i had anticipated.
i made this post to get hardware/software ideas for reaching my goal.
i am not a liar, dont treat me as such. my intentions just dont ever seem to be understood the way i intend them to, so please understand that. Now, back to the constructive help, should you all not mind.

p.s. im well aware that someone out there knows more then me. tis the reason i asked ;)

---

### Post by garyhibdon on 2011-01-14
can accompany a picture should you ask.

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
    Socket Designation: Socket 775
    Type: Central Processor
    Family: Other
    Manufacturer: Intel            
    ID: 7A 06 01 00 FF FB EB BF
    Version: Pentium(R) Dual-Core CPU E5300 @ 2.60GHz            
    Voltage: 1.3 V
    External Clock: 249 MHz
    Max Speed: 3800 MHz
    Current Speed: 3237 MHz
    Status: Populated, Enabled
    Upgrade: Socket LGA775
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Characteristics: None

got ANOTHER different number. hmmmm thats using ```
 sudo dmidecode
```

---

### Post by cascade9 on 2011-01-14
> **garyhibdon said:**
> i have been able to find several links on what pae is, but nothing as to how to initiate this technology. any recommendations?

Dont bother? 64bit is faster, doesnt have the drawbacks of PAE (PAE can only use 3/4GB per porcess). 

> **1clue said:**
> Both you guys who referenced my post took it to be much more antagonistic than I meant it.
 
 Nah, not really, I guessed where you were coming from.... 

> **garyhibdon said:**
> and by the way, just noticed that i had missed a couple of posts, so i thought i'd respectively answer in kind to each.
First off, i cant help that cpu-z and my bios are not giving the same information, 

Then settle for one method, dont use them interchangeably. BIOS should be the correct value.  

> **garyhibdon said:**
> and thats ALSO in reference to the multiple cracks at the 1ghz p1. just telling you what the bios stated. the computer didnt even run long enough to load any kind of windows. it fried itself in mere moments. 

No, your BIOS would never had said 1GHz for ANY P1. EVER. 

> **garyhibdon said:**
> Secondly, the comment about a 6Ghz computer was NOT in ANY  way shape or form saying that i wanted THIS computer AS IT SITS to do that, i said im working TOWARDS that goal.

'Working towards' being new CPU, new motherboard and new RAM? You'll still need liquid nitrogen to get to 6GHz. (OK, possibly phase change would do it as well, but I'm not sure on that). 

> **garyhibdon said:**
> Lastly, these confusions are the reason that i had mentioned the fact that nothing i was saying was being taken as i had anticipated.
i made this post to get hardware/software ideas for reaching my goal.
i am not a liar, dont treat me as such. my intentions just dont ever seem to be understood the way i intend them to, so please understand that. Now, back to the constructive help, should you all not mind.

p.s. im well aware that someone out there knows more then me. tis the reason i asked ;)

Considered that you've hit the limit from your CPU/motherboard/RAM/etc? Ohhh, while I remember, you've got a 'EPU' motherboard, thats asus power svaving tech. A 'normal' (non-EPU) version would probably overclock better.

Like I said above, just because somebody has got CPU 'A' to X GHz doesnt mean that your setup will.....

---

### Post by garyhibdon on 2011-01-14
didnt realize that the standard asus would have been better on clocking. thanks, also, for that bit of info. and where exactly is the world record right now. ive seen LOTS of various numbers recently, and 6Ghz doesnt seem to be THAT high up there. though i also realize that the vast majority are fake, ive not seen a definite 2010 record. one "record" was from '09 and that was over 9Ghz( still possibly fake). so upon initial research, 6 seemed quite feasible. but either way, thats an "eventually" goal. looking for quick tips and tricks to speed what i have(or can afford) out.


EDIT: as an after thought, got the duo running 3250 mhz. nothing higher is stable or faster on what i have, atleast not that ive found

---

### Post by cascade9 on 2011-01-15
The fastest I can think of now is 8200MHz-

[http://www.xbitlabs.com/news/cpu/display/20100125132945_World_s_Overclocking_Record_Beaten_8_20GHz_Clock_Speed_Reached.html](http://www.xbitlabs.com/news/cpu/display/20100125132945_World_s_Overclocking_Record_Beaten_8_20GHz_Clock_Speed_Reached.html)

No benchmarks, so it probably wasnt stable, or even close to stable. That is an old trick, 'max bootable to windows' overclocking. Totally pointless.  

6GHz you arent going to do without exotic cooling (probably liquid nitrogen), a VERY overclockable chip, great memory and a great motherboard.

4GHZ is about as far as core2duo chips can be pushed on air cooling (that is going to take a good overclocking chip, great memory/motherboard/power supply and heatsink). 6GHz, or even 5GHz, is dreaming.

---

### Post by NightwishFan on 2011-01-15
Not that my input is really useful or anything, I just want to chime in a plus one for not overclocking. The only thing a few extra khz of cpu power would be good for is a raw CPU bound load. Most desktop users and even servers need a balanced set of performance and first and foremost reliability. It will take some research to see where your system is weak, and it is probably NOT the cpu.

---

### Post by garyhibdon on 2011-01-15
> **NightwishFan said:**
> Not that my input is really useful or anything, I just want to chime in a plus one for not overclocking. The only thing a few extra khz of cpu power would be good for is a raw CPU bound load. Most desktop users and even servers need a balanced set of performance and first and foremost reliability. It will take some research to see where your system is weak, and it is probably NOT the cpu.



thats true in most cases and thats exactly what ive been trying to find out.
the balance is the hardest part, and thats why ive been on here asking about this and that, its just to find out a ball park figure of what i can expect. i know no two setups are going to give the same output, and thats where the "ballpark figure" comes into play.
o/c-ing is more bragging rights, and this i understand, but as i said, its just a hobby of mine. And thank you cascade for the honest, earthbound opinion. the average ive been seeing is about 4Ghz on an i7, so i know its quite feasible. its just overclocking is the only way i know to speed up an existing setup to support what is being attempted, short of expansion/replacement. 


On a different note, do you think that running 10.10 64 bit would be a little faster, or slower. i hear 64 bit os's are more memory hungry, which is what made me stick with 32 bits. i just find myself at a loss as to some of the specifics as far as thats concerned, so any input is appreciated. also, how big of a difference is there between 32 bit and 64 bit as far as commands and installs are concerned.

as im sure youve noticed, im shooting for a balance of the best performance and application support.



EDIT: and also, had to turn down the output on the cpu some more, became unstable again. i am paying attention to whats going on, just got to find out whats safe and whats not.

---

### Post by NightwishFan on 2011-01-15
I have used Ubuntu 64-bit for years. It is not memory hungry enough to be a disadvantage. I can still boot a gnome desktop in 386mb of ram. Give it a go!

---

### Post by cascade9 on 2011-01-15
> **NightwishFan said:**
> Not that my input is really useful or anything, I just want to chime in a plus one for not overclocking. The only thing a few extra khz of cpu power would be good for is a raw CPU bound load. Most desktop users and even servers need a balanced set of performance and first and foremost reliability. It will take some research to see where your system is weak, and it is probably NOT the cpu.

Yes, a few kHz isnt goignt o make much difference. But even a tiny overclock is well into the MHz.

Who wouldnt take a bit more CPU power, even if its not the weak point? BTW, viewing things as CPU alone is a VERY limited view on overclocking, and its more than possible to 'improve' other areas as well. You dont always sacrifice reliability, provided that you know what you are doing and dont try to push the envelope to hard.

Example of all the above? I used to run an AMD 2200+ (stock 1795MHz (133 x 13.5) @ 1.65volts). I ran it for well over a year overclocked and undervolted (1826MHz (166 x 11) @ 1.525volts). Not just extra core MHz, but I also got more memory bandwidth, and it used less power into the bargin. 

BTW, that chip ran fine at higher frequencies, but then I would have had to bump the voltage, which could have led to early chip death. As it stands, that CPU is still running in my mums computer, after 7+ years in service....

> **garyhibdon said:**
> thats true in most cases and thats exactly what ive been trying to find out.
the balance is the hardest part, and thats why ive been on here asking about this and that, its just to find out a ball park figure of what i can expect. i know no two setups are going to give the same output, and thats where the "ballpark figure" comes into play.

Seriously, dont go looking for 'ballpark figures'. Its counter-productive. 

> **garyhibdon said:**
> o/c-ing is more bragging rights, and this i understand, but as i said, its just a hobby of mine. 

If thats the case, just get good at photoshopping CPU-Z screenshots. :P 

> **garyhibdon said:**
> And thank you cascade for the honest, earthbound opinion. the average ive been seeing is about 4Ghz on an i7, so i know its quite feasible. 

If you had a i7, this comment might matter, but you dont. You have a Core2Duo. You cant compare chips from one series/architecture to a totally different series.  

> **garyhibdon said:**
> its just overclocking is the only way i know to speed up an existing setup to support what is being attempted, short of expansion/replacement. 

On a different note, do you think that running 10.10 64 bit would be a little faster, or slower. i hear 64 bit os's are more memory hungry, which is what made me stick with 32 bits. i just find myself at a loss as to some of the specifics as far as thats concerned, so any input is appreciated. also, how big of a difference is there between 32 bit and 64 bit as far as commands and installs are concerned.

as im sure youve noticed, im shooting for a balance of the best performance and application support.

EDIT: and also, had to turn down the output on the cpu some more, became unstable again. i am paying attention to whats going on, just got to find out whats safe and whats not.

You can speed up by installing more minimal DEs, minimising your installed program base, making sure that /root and /home as as close to the beginning of the drive as possible, moving to 64bit (about 5-10% faster on average, but a lot faster than that in some places), etc.. 

You really need to realise this- faster clocking does NOT always equal faster performance. Just clocking up sure works if you are trying to get bragging rights, but if you want to squeeze the absolute most from your system, the fastest clock possible is normally slower (in performance) than a slower clock. Errors hurt.

---

### Post by Paqman on 2011-01-15
> **garyhibdon said:**
>  
On a different note, do you think that running 10.10 64 bit would be a little faster, or slower. i hear 64 bit os's are more memory hungry, which is what made me stick with 32 bits.


There is a marginal increase in the memory footprint, but not enough to make any difference unless you're critically short on RAM already. This is more than made up for by a small performance increase across the board, and a large performance increase in CPU-heavy tasks like video transcoding.

I don't see any point in throttling a 64-bit chip down to 32-bit, personally.

> also, how big of a difference is there between 32 bit and 64 bit as far as commands and installs are concerned.

No difference at all.

---

### Post by garyhibdon on 2011-01-15
well thank you all for the input, seems to be going quite productively.
i'm well aware that i7 and core2's are not even remotely similiar, and i wasnt referencing them being so, was just stating that that was the average o/c ive seen lately.

the last 2 questions i have about this are:

1) can i just transfer my files from the 32 bit over to the 64, if so how?

2) would 2 gigs of ram be sufficient for the time being?


EDIT: sorry for the idiosyncratic questioning, but i've just not messed with 64 bit os's.

---

### Post by Paqman on 2011-01-15
> **garyhibdon said:**
> 
1) can i just transfer my files from the 32 bit over to the 64, if so how?


To switch to 64-bit you need to reinstall. If you've got a separate home partition then you can keep everything intact there. Otherwise, just back up your data, then copy it back onto the new 64-bit system.

> 
2) would 2 gigs of ram be sufficient for the time being?


For almost everything you'd want to do, yes. The only thing I ever do that requires more than that is running VMs.

---

### Post by cascade9 on 2011-01-16
> **garyhibdon said:**
> well thank you all for the input, seems to be going quite productively.
i'm well aware that i7 and core2's are not even remotely similiar, and i wasnt referencing them being so, was just stating that that was the average o/c ive seen lately.

Overclocking a i7 to 4GHz is easier than getting a Core2Duo to 4GHz from everything I've seen. If you know that the 2 chips arent the same, you should know that however overclocking goes on one is no relection on how the other overclocks.

---

### Post by garyhibdon on 2011-01-16
well no see, i have been considering a little mb/cpu update. its tax  time, etc. so yeah. that was the chip i was considering, which is the  reason i mention it, more to assure myself then anything else. the  problem is that the i7's multiplier is lower then the e5300 from what  ive seen,IF im looking in the right areas and the cache isnt much bigger  isnt that much higher also, so ive not been too sure where the  difference in clocking capabilities came into play. but thats not the  point really, as i dont have one. lol thanks for the info though

---

### Post by cascade9 on 2011-01-17
I dont get it.

You bought your current machine a year ago, you seem to have bought a motherbaord at least just on the idea that 'it can overclock', you are unable to get it to 4GHz so you start a thread here...

Now your thinking for buying an i7 and your are worring about the multi?!?!?? 

Just get a Core2Quad and 4GB DDR2, shove that in your current motherboard, stop worring about overclocking. With a qaudcore and at least twice the cache you've got now, you system should run well even with "3 and 4 instances of diablo 2 running as well as a music player and a couple of internet tabs open".

---

### Post by 1clue on 2011-01-17
We got a meter reader.

---

### Post by garyhibdon on 2011-01-17
i started this thread to get an idea of how to speed this machine up. the overclocking idea was brought up based on the fact that most cpus can work faster then they do at the initial setting. While i understand that max performance does not mean highest clock, i'm simply trying to get an idea, as i said, on how to make this faster, to handle what im trying to do, and to understand how exactly some of the information i have correlates together.

---

### Post by NightwishFan on 2011-01-17
My bottom line opinion is faster is subject to personal opinion. There is no universal way to define "faster" in a machine. Generally "fast enough" from all aspects is what you should look for.

---

### Post by 1clue on 2011-01-17
I'm 45 years old.  I've been using computers since before I shaved, when you used a teletype to enter information and to get it out.  I remember the first time I used an Apple ][, an Atari, a Commodore PET, and TRS-80's.  I remember loading programs off an audio cassette tape machine.

I've tweaked the performance of a whole lot of my computers.  To date, I have never found overclocking to be necessary or even advantageous.

On top of that, you keep referencing core2duo clock speeds and i7 clock speeds interchangeably.  There is something fundamentally wrong about that.  That's why we keep getting on you about it.

Let me try a metaphor:

You have a Honda Accord running down the freeway at 70 mph.  Right next to it, you have a large freight truck going at the same speed.

In one way, the two vehicles are going the same speed.  In another way, the truck has much more hauling capacity, so even if it were going much slower it would still be faster than the car if both are fully loaded.  In yet a third way, if both vehicles are carrying nothing but the driver, the car is much better than the truck because it gets 40 mpg compared to the truck's 3 mpg.

Your reference of the same clock speed between those two processors is similar to the car/truck metaphor.  We've already established that you don't like the speed of your existing computer.  But we haven't really established the load you're carrying in my mind, probably enough to justify a quad core maybe but an i7?  In my experience the extra cores don't really come into play unless you're running something very parallel, or virtual machines.  If you're running everything under your user account you will probably be wasting your money.

Moreover, if your system is graphics-bound rather than cpu-bound then your i7 won't be any faster than the core2duo.

There is nothing "eco-friendly" about an i7.  It sucks power like crazy, and if you tweak it to 4ghz it will use a boatload of power even if it's idling.  I found an article on overclocking an i7 which uses almost exactly my hardware, only the memory on mine is better and the disk on mine is faster.  I took a look at the power consumption and shuddered.

Do you have real data from some authority about the resources your system needs to run your applications?  Or maybe you've done diagnostics to see if your shortfall is CPU or memory or disk platter speed or card bus speed or video processing speed or ....?

You talk about not having money to continually upgrade computers.  I doubt there's anyone on this forum who spends money to get a new system every year, at least not something like a game machine.  Tell us what you've done to eliminate bottlenecks.  Sometimes the thing you need to do to more than double your speed doesn't cost any money at all.

There are a huge number of factors that limit a computer's suitability for a particular task.  You seem to be fixate on one of them.

Sorry if this turned into a rant.

---

### Post by garyhibdon on 2011-01-18
1clue, you seem to be very insightful and have actually made it clear to me what you were trying to ask, and i appreciate that. to be honest, i'm not really sure WHERE the shortcomings of my computer are, and thats reason ive been asking so many random off the wall questions, and making references to other things, is because i honestly dont have any ideas. you and cascade both seem to have an acknowledgeable grasp on what you're talking about, and i've been attempting to tap into that well of knowledge, but as ive said before, i suppose i dont really know exactly how to express what i'm trying to get. 


so lets do it this way. start from point "A" and go from there. my computer isnt really slow, ESPECIALLY not when you compare to the machines i HAVE used. it just seems to be lacking something, and ive not been able to ascertain where exactly the issues lie. it is VERY fast when you turn it on, it loads the initial log-in screen for ubuntu up in mere moments. on average it takes about 3.5-5 seconds to do so. type in the password, and it takes about 20 seconds to actually load into ubuntu. then it speeds up while running MOST of my applications individually. Load more then 1 or 2 though, and theres a noticeable speed decrease. give it a moment or so to adjust and it speeds back up again. once i start running 2 tabs on firefox and the music player, it tends to lag. 1 instance of diablo and 1 tab in firefox is a BIG lag issue, typically lasting around 20 seconds. and as i open more items, obviously, it gets worse with bigger and longer lag spikes.

Initially my cpu ran @ 2.6 Ghz, i overclocked it to 3.21 and that fixed the VAST majority of the issues, but i was still having issues running more then 1 app at the same time. so i thought that the cpu was the issue.

after a little research and tinkering, it started to look like my ram was the issue.i bring these issues to others attentions, and get lost in all the other ideas


so right now i have SEVERAL good hypotheses, but not exactly sure where to start looking. does this help clarify my issue at all?

---

### Post by NightwishFan on 2011-01-18
These lag issues might just be related to the way modern Linux schedules tasks to be honest. I find "real work" is done extremely well and long cpu intensive tasks do not get in my way. Firefox on the other hand is often halting while loading tabs. I can't prove if it is a Firefox problem or a Linux problem. I suspect Firefox. Are there any specific other tasks that lag (but not while you are using Firefox)?

---

### Post by cascade9 on 2011-01-18
> **NightwishFan said:**
> My bottom line opinion is faster is subject to personal opinion. There is no universal way to define "faster" in a machine. Generally "fast enough" from all aspects is what you should look for.
 
 There is not a 'universal' way to measure faster, but you can benchmark. 

> **1clue said:**
> I've tweaked the performance of a whole lot of my computers.  To date, I have never found overclocking to be necessary or even advantageous.

'Ncessary'? No, never. 'Advantageous'? I've found overclocking can be. 

As for the rest of your post (that I snipped) I agree 100%. Ohh, and BTW, see this thread- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10355568#post10355568](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10355568#post10355568)

I've tried suggesting some a non-overclocking way to try to improve performance, but garyhibdon has no intrest in even trying it.

---

### Post by garyhibdon on 2011-01-18
first off, found out something funny. my memory is ddr2 800 2gig. mb recomends 1066 while o/c. oops.

and yes actually. the lag issue are pretty interchangeable no matter the programs.  my games and music player, 3 tabs in firefox, 1 tab in firefox and a game or rhythmbox, etc.

so far there seems to be no true trend for the particular programs lagging it,
atleast not outside of all of them. but firefox does make it a little worse

---

### Post by garyhibdon on 2011-01-18
> 

As for the rest of your post (that I snipped) I agree 100%. Ohh, and BTW, see this thread- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10355568#post10355568](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10355568#post10355568)

I've tried suggesting some a non-overclocking way to try to improve performance, but garyhibdon has no intrest in even trying it.
you are correct sir. ive no interest in chopping my system down to minimal.
its counterproductive. if i dont have anything IN my system, then theres no point in trying to make it faster.

as i said then and ill say again, minimal install wont accomplish anything once my files are re-installed. true, less information to read, but it is still made up for my programs just to RUN the things i'm having issues with.


BTW, if you cant be productive with your input, please keep it to yourself.

I'm asking for answers or ideas, not "smart" retorts, ty

---

### Post by NightwishFan on 2011-01-18
There should not be problems on such a lightly loaded system. I would look into potential graphics performances issues. Try changing your theme to clearlooks and see if performance improves. If so then your problem is GPU related. I find Ubuntu 10.04 is amazingly fast so perhaps try that release if you are not already. (I forget if you are or not, sorry if you already know this, or its not an option.)

---

### Post by garyhibdon on 2011-01-18
when i bought my motherboard i was told it "had a built in vid car" could THIS in fact be the issue? or did i misunderstand what you were shooting for?



EDIT: also, i only had it set to ambiance but i changed it anyway, and also killed the visual effects in the other tab. i guess we'll see

---

### Post by cascade9 on 2011-01-18
> **garyhibdon said:**
> you are correct sir. ive no interest in chopping my system down to minimal.
its counterproductive. if i dont have anything IN my system, then theres no point in trying to make it faster.

as i said then and ill say again, minimal install wont accomplish anything once my files are re-installed. true, less information to read, but it is still made up for my programs just to RUN the things i'm having issues with.

BTW, if you cant be productive with your input, please keep it to yourself.

I'm asking for answers or ideas, not "smart" retorts, ty

So, you've already decided that a minimal install wont help at all, without even trying it? It probably would help. 

Ohhh, so you want 'productive' but you are more than happy to tell people that the HDD they bought is 'junk'? BTW, like I said there WD blacks are the fastest 7200s around- 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10347068#post10347068](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10347068#post10347068)

Your pot is blacker than my kettle. 

Thats without getting into semi-poinltess accusations like 'do you even know the difference between GiB and GB'? :lolflag:

---

### Post by garyhibdon on 2011-01-18
and there you go again. nothing useful to say. are you this spiteful to everyone? or did you just get a "special place" for me?


nightwishfan, that actually helped EXTENSIVELY. 4 firefox tabs, music player and my game all at once. you are my hero. thank you so much.


cascade, ive grown tired of your witless retorts, please find someone else to mess with. 


"just because you CAN be something, doesnt mean you HAVE to be"



EDIT: as an after thought, why dont you explain to me how deleting everything on my computer to make it faster makes sense.  i truely do not understand how erasing the files i want to run would make them run faster

---

### Post by cascade9 on 2011-01-18
> **garyhibdon said:**
> cascade, ive grown tired of your witless retorts, please find someone else to mess with. 

"just because you CAN be something, doesnt mean you HAVE to be"

Gee, thanks. I was hardly making 'witless retorts', just I'm saying what you dont want to hear.  As far as I can tell, I'm the only person on this thread with extensive overclocking experience, so maybe there is something in what I'm saying? 

Did you really expect somebody here to hold your hand through the overclocking process? Try [h]ardOCP, tomshardware, overclock.net, OCAU, or any of the hundreds of other overclocking sites...

*edit- Paqman has posted here, and IIRC they are running a fair overclock, or was. Minor oversight, they havent posted on this thread much.

---

### Post by garyhibdon on 2011-01-18
and you STILL cant listen evidently. did i NOT mention the possibility of software reconfigs? no? oh my mistake. i thought i JUST about a possible graphics issue. you never answered that. and seen as how you deem yourself some sort of overclocking guru, why are you just NOW mentioning ANY ideas or links to where i might be ABLE to ascertain this information.

and what have you clocked thats so great? as i recall, you have a pretty standard build. copying others doesnt make you cool or good. 


now, should you decide to be productive with your comments, you could explain how deleting the files i want to use would make these files run faster. i'd appreciate it. 

and if thats not what you meant, maybe explain a little, because youve mentioned that 4 different times, so i OBVIOUSLY missed the point or misunderstood somewhere along the way.



this thread was NOT designed to engage a pissing contest. I've already admitted that you know more then myself, thusly i ask for assistance. dont care to help, then dont comment. constructive criticism is always welcome, so long as it remains that way


also, how would i find out what type of ram i need? the only ones i can find say pc2 8500. dont want to buy anything unless i know its right.

---

### Post by cascade9 on 2011-01-18
> **garyhibdon said:**
> and you STILL cant listen evidently. did i NOT mention the possibility of software reconfigs? no? oh my mistake. i thought i JUST about a possible graphics issue. you never answered that. and seen as how you deem yourself some sort of overclocking guru, why are you just NOW mentioning ANY ideas or links to where i might be ABLE to ascertain this information.

and what have you clocked thats so great? as i recall, you have a pretty standard build. copying others doesnt make you cool or good. 

I never mentioned that...of couse.  ! assumed that anybody who was going to try to get max performance would never have been using a intel video chip. 

*edit- listing your system specs in detail is a good idea if you are looking for help. 

I never said I was an 'overclocking guru'. I said "As far as I can tell, I'm the only person on this thread with extensive overclocking experience". (which may well be wrong, apologies to Paqman if I am). 

I'm not putting links in because overclocking is dangerous. 1GHz P1?'Shooting for 6GHZ'? If I put a link in here to how to get more MHz from your machine, you are liable to give it far to many volts, and then I'd feel borderline responsible.  

Where have I put in any links to anywhere that you might be able to find out anythign about your chip, and/or overclocking? Nowhere. If you had of done some reasearch, at least one of those sites should be familiar to you. 

I dont talk about overclocking here much. I have put in a few system specs, but they tend to change fairly often. I've never put a detailed list up here, so you are just guessing that I have a 'fairly standard build'. As for 'copying others'- pfft. No, my system is not a clone of anybody elses. 

As for what overclocking I've done, I'm not going to list them all. Suffice it to say I've used every major cooling method known apart from liquid nitrogen (air, water/radiator, water/evaporative and phase change) and I've pushed some CPUs pretty much as far as they will go (well, I could have got an extra 100MHz out of my XP 2500+, but I didnt want to push the core voltage any higher). 

> **garyhibdon said:**
> this thread was NOT designed to engage a pissing contest. I've already admitted that you know more then myself, thusly i ask for assistance. dont care to help, then dont comment. constructive criticism is always welcome, so long as it remains that way

You say that, but you are asking for what "have you clocked thats so great"? Think about it..... 

> **garyhibdon said:**
> now, should you decide to be productive with your comments, you could explain how deleting the files i want to use would make these files run faster. i'd appreciate it. 

and if thats not what you meant, maybe explain a little, because youve mentioned that 4 different times, so i OBVIOUSLY missed the point or misunderstood somewhere along the way.

*sigh* You cant 'run a file' if its deleted. 

Minimal installs have a lot less packages. If you need the package, install it. Sure, if yuo need _all_ the packages that come with standard ubuntu, it wont make any difference.....but most people dont need everything that comes with ubuntu.  

Did I ever say 'delete files you need'? No. Minimal install is not 'delete files you need', its 'start with a minimal amount of pacakges so you can build only what you need'. 

> **garyhibdon said:**
> also, how would i find out what type of ram i need? the only ones i can find say pc2 8500. dont want to buy anything unless i know its right.

Yopu look at the motherbaord manufacturers page, figure out what RAM it takes (DDR2 in this case), at what speeds (667, 800 and 1066 in this case). Then decide if you want to run memory on the 'motherbaord memory compatibilty list' or if you want to just risk getting random RAM and hoping it works.  

2 x 2 GB DDR 1066 is probably your best bet, but DDR2-1066 is overly expensive now. 2 x 2 GB DDR2-800, $60, 2 x 2GB DDR2-1066, $80.

---

### Post by garyhibdon on 2011-01-18
That was sarcasm, and obviously you missed it. not in a pissing match with you. so i'll let it go. and fyi, ive not installed anything i dont need to accomplish what i want on here. 320Gig hard drive and ive only used 5.9 gigs. that includes music files. and im also well aware that my m/b takes ddr2 1066. but all the ram i found at newegg is pc2 8500. THAT was the part i was unsure of



also, i know NOTHING about vid cards. i admit it.never messed with one. have been looking around a bit to find out whats what, and honestly, i just dont have the experience with them to make an educated guess. i thought that the one i had would suffice. at this point i suppose not. any recommendations?



EDIT: the epu model of the p5kpl, if you would recall, has a safety cap, so i couldnt really hurt it anyhow.

---

### Post by cascade9 on 2011-01-18
> **garyhibdon said:**
> That was sarcasm, and obviously you missed it. not in a pissing match with you. so i'll let it go. and fyi, ive not installed anything i dont need to accomplish what i want on here. 320Gig hard drive and ive only used 5.9 gigs. that includes music files. and im also well aware that my m/b takes ddr2 1066. but all the ram i found at newegg is pc2 8500. THAT was the part i was unsure of

Sarcasm doesnt translate well online. 

PC2-8500 = DDR2-1066. BTW, DDR2 and DDR3 come in 'PC 8500'. DDR3 would be PC3-8500. 

*edit- you might not have manually installed anything 'you dont need' but there will be at least a few packages in standard ubuntu you dont need. Its not about space used on the HDD, its about how many packages need to be loaded, how much RAM and how many system calls they will use, etc.. 

> **garyhibdon said:**
> also, i know NOTHING about vid cards. i admit it.never messed with one. have been looking around a bit to find out whats what, and honestly, i just dont have the experience with them to make an educated guess. i thought that the one i had would suffice. at this point i suppose not. any recommendations?

Probably nice, cheap GT220. It will blow intel video into the weeds. A GTS450 or GTX460 would be faster, but probably uneeded since the only game I've seen you mention is D2, and that hardly pushed GPUs 'back in the day' let alone now. 

> **garyhibdon said:**
> EDIT: the epu model of the p5kpl, if you would recall, has a safety cap, so i couldnt really hurt it anyhow.

'Safety cap'? *blinks* What on earth are you talking about? If you mean 'EPU' then its just asus power saving tech. It wont save you from excessive voltage, MHz or heat.

---

### Post by 1clue on 2011-01-18
Holy moley!

Settle down a bit, both of you guys have your danders up and you're not doing anything but spamming the board with your angst.

Gary, post 65 was EXACTLY the sort of questions that will get you a faster machine as cheaply as possible.  68 was not bad either.

I would start with /var/log/messages.  Go through there and make sure there are no errors at all.  Once you think you've cleared out all the problems, then zero the file and reboot, and start over checking the file out again.

**sudo cp /dev/null > /var/log/messages** will do it.

Any error that happens will cause your system to slow down.  Overly verbose logging will also do that but you probably don't have that unless you've been messing around with logging.  Also, a clean log will help you immensely when something breaks and you need to figure out what it is fast.  A lot of people I know tolerate badness in their logs because they can still get work done, but if you wait till then you'd just as well start over with an installer disk.

You and cascade have been obnoxious to each other long enough that you're objecting to each other's ideas without paying attention.  However he's right about one thing, even if I don't see where he's worded it very well:

Removing services which are running on your system but that you don't care about will speed your system up.  A few years back I started using distributions that have a minimal install.  I install that and then add the things I care about explicitly.  Ubuntu Server is actually pretty decent that way.  So is Gentoo, but that's a whole nother can of worms.  =)

Removing "unnecessary" components is entirely subjective.  If you want the flashy screen special effects then they're necessary.  Deciding what is unnecessary will probably take you years to do the job right but maybe not so long to get the big stuff turned off.  It's a really good idea to get started on that because it will teach you a huge amount about Linux and enable you to get the most out of your hardware, no matter what it is.

I would suggest that any benchmarks you might make until the logs are clean are irrelevant except as a baseline for how much you've improved.

---

### Post by 1clue on 2011-01-18
Another thing about too many files that supports cascade a bit.

Fragmentation.

If you're close to full on a filesystem and that filesystem is repeatedly written to, then there is a fairly good chance that you have fragmentation on it.  Fragmentation causes the disk heads to seek rapidly on the platter, which is a mechanical action and much slower than anything software that might be going on.

Whatever filesystem you're using, check out how well it handles fragmentation and whether you need to manually do anything to get rid of it.

Common opinion is that any more than 90% full and you have a fragmentation problem.  I personally think it's closer to 75%.  I'll happily leave something like /usr above 90% because that just never gets written to, but /home needs to keep plenty of space on it.

---

### Post by 1clue on 2011-01-18
Sorry for the triple post.  The more I read, the more I feel I need to say something.

Please stop slinging mud, both of you.  It's fun for awhile, but after the first few handfuls it loses its effect and nobody gets anything done.  I did some of that too, but enough is enough.

Let's tone down the language here and try to see what it is that the other person is trying to say rather than how they say it.  Too many flames and anyone who knows anything at all is going to stop watching your thread.

Gary:

Don't buy anything yet.  Get your system working correctly so it conforms to a reasonable performance standard.  Once it's working properly, we can get some idea of where the bottleneck is and fix that.  Whether that's memory or a hard disk or a video card or something else, we don't know what's causing the problem yet.

---

### Post by garyhibdon on 2011-01-18
kudos to 1clue yet again. ill try these ideas and get back with some info. thanks much again.



before you ask, i did verify that my account was set as admin, but i get this error message:

```
me@me-System-Product-Name:/$ sudo cp /dev/null > /var/log/messages
bash: /var/log/messages: Permission denied
```


I'm starting to feel retarded. this seems a pretty basic and straight forward task and I'm lost. lol

---

### Post by garyhibdon on 2011-01-18
Ok cascade and 1clue, i need to listen more. the ram i have are not up to par for overclocking, and my hdd is 32 bit.

I'm looking dumber by the moment.

*foot inserted to mouth*

---

### Post by 1clue on 2011-01-18
Um, it might be more basic and simple if I gave you the right command.  :oops:

sudo cat /dev/null > /var/log/messages

First, make sure you're done with it first.  Here's what this does:

sudo:  makes you superuser.
cat:   prints the contents of the file.
/dev/null:  A special device file on any un*x which contains nothing.
>:     puts the "standard out" into the file specified next.
/var/log/messages:  Your system log file.

So what you're doing is causing your /var/log/messages file to be zero bytes.

Again, only do this if you have gone through your log and fixed what you think needs to be fixed.  The reason you're doing this is so you can reboot and see exactly what is still broken, when you come back up the only things in there will be related to your most recent shutdown and the boot after it.

Or more correctly, everything that happened after you zeroed the file.

---

### Post by garyhibdon on 2011-01-19
ok, still a negatory on that one. same exact error message


```
me@me-System-Product-Name:~$ sudo cat /dev/null > /var/log/messages
bash: /var/log/messages: Permission denied
me@me-System-Product-Name:~$ 
```

---

### Post by 1clue on 2011-01-19
It asked you for the password right?  And you typed it correctly?

Type **sudo ls -al** and see what happens.

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:~$ sudo ls -al
[sudo] password for me: 
ls: cannot access .gvfs: Permission denied
total 332
drwxr-xr-x 45 me   me    4096 2011-01-18 19:34 .
drwxr-xr-x  3 root root  4096 2011-01-03 14:42 ..
drwx------  3 me   me    4096 2011-01-04 22:07 .adobe
-rw-------  1 me   me    4342 2011-01-19 00:36 .bash_history
-rw-r--r--  1 me   me     220 2011-01-03 14:42 .bash_logout
-rw-r--r--  1 me   me    3353 2011-01-03 14:42 .bashrc
drwx------ 18 me   me    4096 2011-01-18 19:34 .cache
drwx------  3 me   me    4096 2011-01-03 17:00 .compiz
drwxr-xr-x 19 me   me    4096 2011-01-12 01:01 .config
drwx------  3 me   me    4096 2011-01-03 14:45 .dbus
drwxr-xr-x  7 me   me    4096 2011-01-16 20:37 Desktop
-rw-r--r--  1 me   me      41 2011-01-18 19:34 .dmrc
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Documents
-rw-r--r--  1 me   me     205 2011-01-06 03:20 .dopewars
drwxr-xr-x  2 me   me    4096 2011-01-16 14:08 Downloads
-rw-------  1 me   me      16 2011-01-03 14:45 .esd_auth
drwx------  8 me   me    4096 2011-01-04 21:32 .evolution
-rw-r--r--  1 me   me     179 2011-01-03 14:42 examples.desktop
drwxr-xr-x  2 me   me    4096 2011-01-17 00:17 .fontconfig
drwxr-xr-x  3 me   me    4096 2011-01-05 15:03 .fretsonfire
drwx------  4 me   me    4096 2011-01-18 19:34 .gconf
drwx------  2 me   me    4096 2011-01-19 01:23 .gconfd
-rw-r-----  1 me   me       0 2011-01-17 00:09 .gksu.lock
drwx------ 11 me   me    4096 2011-01-17 00:26 .gnome2
drwx------  2 me   me    4096 2011-01-04 19:20 .gnome2_private
drwxr-xr-x  2 me   me    4096 2011-01-17 01:03 .gstreamer-0.10
-rw-r--r--  1 me   me     122 2011-01-18 19:34 .gtk-bookmarks
d?????????  ? ?    ?        ?                ? .gvfs
-rw-------  1 me   me   22196 2011-01-18 19:34 .ICEauthority
drwxr-xr-x  2 me   me    4096 2011-01-06 00:19 .icons
drwx------  3 me   me    4096 2011-01-05 00:54 .kde
drwxr-xr-x  3 me   me    4096 2011-01-03 14:45 .local
drwx------  3 me   me    4096 2011-01-04 22:07 .macromedia
drwx------  3 me   me    4096 2011-01-04 21:32 .mission-control
drwx------  4 me   me    4096 2011-01-04 19:20 .mozilla
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Music
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 .nautilus
drwxr-xr-x  3 me   me    4096 2011-01-04 21:26 .openoffice.org
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Pictures
drwx------  3 me   me    4096 2011-01-04 20:45 .pki
drwxr-xr-x 11 me   me    4096 2011-01-19 01:25 .PlayOnLinux
-rw-r--r--  1 me   me     675 2011-01-03 14:42 .profile
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Public
drwx------  2 me   me    4096 2011-01-18 19:34 .pulse
-rw-------  1 me   me     256 2011-01-03 14:45 .pulse-cookie
drwxr-xr-x  2 me   me    4096 2011-01-09 14:47 .qt
-rw-------  1 me   me   58512 2011-01-18 19:30 .recently-used.xbel
drwxr-xr-x  2 me   me    4096 2011-01-09 21:42 .shotwell
-rw-r--r--  1 me   me       0 2011-01-04 04:13 .sudo_as_admin_successful
drwxr-xr-x  4 me   me    4096 2011-01-06 01:17 .sudoku
drwxr-xr-x  4 me   me    4096 2011-01-06 02:48 .supertux
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Templates
drwxr-xr-x  3 me   me    4096 2011-01-06 17:33 test folder
drwxr-xr-x  2 me   me    4096 2011-01-06 00:19 .themes
drwx------  4 me   me    4096 2011-01-04 21:00 .thumbnails
drwxr-xr-x  2 me   me    4096 2011-01-03 14:45 Videos
-rw-r--r--  1 me   me       2 2011-01-08 04:59 .windows-serial
drwxr-xr-x  4 me   me    4096 2011-01-19 00:32 .wine
drwxr-xr-x  2 me   me    4096 2011-01-05 16:18 .xine
-rw-------  1 me   me   13321 2011-01-19 01:25 .xsession-errors
-rw-------  1 me   me    4076 2011-01-18 19:30 .xsession-errors.old
drwxr-xr-x  2 me   me    4096 2011-01-06 01:24 .zsnes
me@me-System-Product-Name:~$ 
```

thats what happened


EDIT: and no, it did not ask for password.

---

### Post by 1clue on 2011-01-19
You're having trouble becoming the root user.  Do you know another way?  **su -** should work fine, or any other way you can become root and try again.

So how many errors were in /var/log/messages?  Have you fixed all the problems in there already?

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:/$ su -
 Password: 
 su: Authentication failure
 me@me-System-Product-Name:/$
```
 
 
 is it just me or is this forum CRAWLING? 
this is REDICULOUS!!! ive been trying to post this for 10 minutes!!!!

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:/$ su -
Password: 
su: Authentication failure
me@me-System-Product-Name:/$ 
```

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:/$ su -
Password: 
su: Authentication failure
me@me-System-Product-Name:/$ 
```

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:/$ su -
Password: 
su: Authentication failure
me@me-System-Product-Name:/$ 
```


also, is it just me or is this forum CRAWLING along?

---

### Post by garyhibdon on 2011-01-19
```
me@me-System-Product-Name:/$ su -
Password: 
su: Authentication failure
me@me-System-Product-Name:/$ 
```


also, is it just me or is this forum CRAWLING along?

---

### Post by garyhibdon on 2011-01-19
sorry for the multiple replies, i was SERIOUSLY having a lag spike, and wouldnt EVER post anything

---

### Post by garyhibdon on 2011-01-19
these are the sections that i noticed that arent that self explanatory to me. are they of any interest?


```
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.654920] type=1400 audit(1295397238.800:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=915 comm="apparmor_parser"
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.655057] type=1400 audit(1295397238.800:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=916 comm="apparmor_parser"
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.655524] type=1400 audit(1295397238.800:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=916 comm="apparmor_parser"
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.655780] type=1400 audit(1295397238.800:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=916 comm="apparmor_parser"
Jan 19 00:38:41 me-System-Product-Name kernel: [18288.357130] VFS: busy inodes on changed media or resized disk sr0
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.450678] drm: registered panic notifier
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.030380] leds_ss4200: no LED devices found
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.047632] agpgart-intel 0000:00:00.0: Intel G33 Chipset
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.048113] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Jan 18 19:33:58 me-System-Product-Name kernel: [    7.098060] lp: driver loaded but no devices found
Jan  9 18:55:59 me-System-Product-Name kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Jan  9 18:55:59 me-System-Product-Name kernel: [    0.000000] DMI present.
Jan  9 18:55:59 me-System-Product-Name kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371802] EISA: Probing bus 0 at eisa.0
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371804] EISA: Cannot allocate resource for mainboard
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371805] Cannot allocate resource for EISA slot 1
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371806] Cannot allocate resource for EISA slot 2
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371808] Cannot allocate resource for EISA slot 3
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371809] Cannot allocate resource for EISA slot 4
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371810] Cannot allocate resource for EISA slot 5
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371812] Cannot allocate resource for EISA slot 6
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371813] Cannot allocate resource for EISA slot 7
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371814] Cannot allocate resource for EISA slot 8
Jan 16 01:40:28 me-System-Product-Name kernel: [    0.371815] EISA: Detected 0 cards.
```
their not in order, but thats all i saw

---

### Post by robert shearer on 2011-01-19
> **garyhibdon said:**
> sorry for the multiple replies, i was SERIOUSLY having a lag spike, and wouldnt EVER post anything

Everybody is affected.
There are currently server problems.
Post then WAIT... cause it will happen.

[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

If you try reposting 'cause its slow then you just end up with multiple posts and bog things down even more.

Be patient and check this for news on this issue..
[http://ubuntuforums.org/showthread.php?t=1669956](http://ubuntuforums.org/showthread.php?t=1669956)

---

### Post by Paqman on 2011-01-19
> **cascade9 said:**
>  "As far as I can tell, I'm the only person on this thread with extensive overclocking experience". (which may well be wrong, apologies to Paqman if I am). 


Hey, most i've done is pushed by E8500 out to about 110% of factory clock on air, before thinking "what's the point?" and getting an SSD instead. Now that's a *real* upgrade.

---

### Post by 1clue on 2011-01-19
OK, here's where there starts to be a problem I can't help with.

You need root access.  It's been a long time since I installed Ubuntu, and have no 10.x systems at all.  You need to figure out your root password, it's critical or you won't ever be able to do software updates or any of the neat stuff.

I usually do this through the sudo command, and while I know how most Linux does it I don't know how Ubuntu does it out of the box now.  :(


If you have no slots in your box, then there's not a lot of things I would worry about with your log, so zeroing it out is probably irrelevant.

Actually you don't really have to zero it anyway.  If you want to add a marker you can do something like this:

**logger '===----->> garyhibdon was here! <<-----==='**

which will show up in your logs and be easier to find than some random shutdown notification.  It works with your normal login, and it's fast.

---

### Post by garyhibdon on 2011-01-19
i use my root password all the time, thats why it doesnt make sense to me either. ive retyped my password countless times in that command, and it always says that access is denied. and did you see the section i posted that had the areas i wasnt sure about? some of them bother me with the way that they are typed in. .

---

### Post by garyhibdon on 2011-01-19
so when i initially built this computer, i was looking at the velociraptor 150gig hdd.
lets say i was to do a minimal install on that, and used my present hdd to store info, do you think that would fix some of the bottlenecks i'm having presently? Had to ask, because ive been reading about the minimal install for the last few hours, and the concept seems pretty sound. and shut up cascade, i already know.

---

### Post by 1clue on 2011-01-19
Gary,

You must have restrictive permissions on /var/log/messages.  Type this:
**ls -l /var/log/messages** and tell me what you get.

Yes, I saw your logs.  Not much to worry about unless you have cards in those slots.

You will want to check the rest of the files in /var/log and any subdirectories as well.

Don't worry about clearing the logs.  It's what I do because it's just easier, but I'm not sure if I want you to inherit my bad habits.  That logger command I gave you will be easy enough to use and would be technically more correct.

---

### Post by garyhibdon on 2011-01-19
this is what it said. not much here 
```
 me@me-System-Product-Name:~$ ls -l /var/log/messages
-rw-r----- 1 syslog adm 175475 2011-01-19 19:44 /var/log/messages
```

and also, just to double check, one of the logs in what i posted mentioned an issue with memory and having to work around it.

whats the significants of this?

---

### Post by 1clue on 2011-01-19
This is something about your video card, almost certainly video RAM instead of system, but not much in any case.  Not sure what that is:

Jan 18 19:33:58 me-System-Product-Name kernel: [    7.048113] agpgart-intel 0000:00:00.0: detected 7676K stolen memory


This is saying the BIOS has a bug in it, but the kernel can work around it:

 [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.

---

### Post by cascade9 on 2011-01-20
I was goign to just avoid this thread but since you are going to be rude, I'll post again. Or maybe it wasnt rude, maybe its a cry for attention? :lolflag: 

I wouldnt be getting a velociraptor for that system. 

Mind you, I would have actually started by checking htop (and/or system monitor) to see what the actual CPU/RAM use levels were before doing anything else, so maybe I'm crazy :P 

> **1clue said:**
> This is something about your video card, almost certainly video RAM instead of system, but not much in any case.  Not sure what that is:

Jan 18 19:33:58 me-System-Product-Name kernel: [    7.048113] agpgart-intel 0000:00:00.0: detected 7676K stolen memory

There is no 'video RAM' on that motherboard. 'Stolen memory' goes back to the intel 810/815- 

[http://i810fb.sourceforge.net/howto/x39.html](http://i810fb.sourceforge.net/howto/x39.html)

> **Paqman said:**
> Hey, most i've done is pushed by E8500 out to about 110% of factory clock on air, before thinking "what's the point?" and getting an SSD instead. Now that's a *real* upgrade.

Well, I was in part right at least, but I thought you had it at 4GHz?  

SSDs, an amazing upgrade for those people with a lot of I/O. Just 'great' for the rest of us (though you would probably get more improvement to average computers from adding an SSD than anything else).

---

### Post by garyhibdon on 2011-01-20
so, my computer no longer will turn on. it went into standby mode, and when i went to wake it up, nothing is working. when i hit the power button, the fans start to spin for a second and then turn back off. any ideas? i've never had this happen before.
 
i tried letting it sit for an hour or so, i tried unplugging it and letting it sit, ive done all i can think of to get it to reset of sorts, and none of it is working. its pissin the crap out of me because i've not changed anything.
 
 
and cascade, i never said anything rude or disrespectful, so if you took it that way, then you read into it more then was really there. i actually even gave you credit and kind of said thank you. so im just done. 1clue was right about the insults back and forth. i listened to you, checked into it, and gave you credit. dont know what more to really say
 
 
and im not sure what "bug" could be in the bios, its all set back to defaults and has been for several days

---

### Post by cascade9 on 2011-01-20
Is this what you meant?

> **garyhibdon said:**
> so when i initially built this computer, i was looking at the velociraptor 150gig hdd.
lets say i was to do a minimal install on that, and used my present hdd to store info, do you think that would fix some of the bottlenecks i'm having presently? Had to ask, because ive been reading about the minimal install for the last few hours, and the concept seems pretty sound. **and shut up cascade, i already know. **

That is rude, and hardly a 'thank you'. 

Maybe when you thought you were reading ""how to make friends and influence people" by Dale Carnegie you were actually reading "101 ways to start a fight" by...er...an Irish gentleman whose name eludes me
 :lolflag: 

As for your problem, clear your CMOS. If that doesnt work, pull all the RAM, clean out the conenctors, reseat. If that doesnt work, strip it down to just motherboard, CPU, a single RAM stick and power supply (nothing else). If it still wont boot, then you've got something seriously wrong, possibly dead, and you'll probably need to start parts swapping to find it.

---

### Post by garyhibdon on 2011-01-20
i already pulled the battery to reset it, and nothing. tried the ram i have in either slot, same thing. lastly i'll try unplugging everything and see what happens. REALLY wish i had more then 1 ram stick. lol and i really wasnt trying to be rude, that was a failed attempt at humor and sarcasm. sorry about that, no offense was intended. thanks for the ideas though
 
 
WISH ME LUCK!!!

---

### Post by Paqman on 2011-01-20
> **garyhibdon said:**
> so, my computer no longer will turn on. it went into standby mode, and when i went to wake it up, nothing is working. when i hit the power button, the fans start to spin for a second and then turn back off. any ideas? i've never had this happen before.


Do you get a beep code? Are the wee power LEDs on the mobo on? Try opening the case and reseating all the cards and checking all the cables are pushed home. If that doesn't work start disconnecting components one at a time and see if it will boot. Start with all the unimportant stuff like optical drives and work your way up to video cards, various RAM sticks, etc. Take notes as you go.

---

### Post by garyhibdon on 2011-01-20
i already pulled the battery to reset it, and nothing. tried the ram i have in either slot, same thing. lastly i'll try unplugging everything and see what happens. REALLY wish i had more then 1 ram stick. lol and i really wasnt trying to be rude, that was a failed attempt at humor and sarcasm. sorry about that, no offense was intended. thanks for the ideas though
 
 
WISH ME LUCK!!!
 
 
tried unplugging everything, and it fired right up. slowly plugged everything back in one at a time and it still fires up. making sure that the bios is still at default and bench test it a few more times. and THANK YOU cascade. better? lol


LOL so i went into the bios, and was checking to verify everything was still default, and to my surprise, the bios version was 0401. . . .their up to 0503 if im not mistaken. lol any idea how to update inside of linux, because thats as up to date as my cd goes, and i never saw an option to check the net for newer ones

---

### Post by Paqman on 2011-01-20
> **garyhibdon said:**
> 
tried unplugging everything, and it fired right up. slowly plugged everything back in one at a time and it still fires up. 

Something came unplugged/unseated then. It happens.

---

### Post by garyhibdon on 2011-01-20
yes it does, now back to the OTHER problem. lol

---

### Post by cascade9 on 2011-01-20
> **garyhibdon said:**
> tried unplugging everything, and it fired right up. slowly plugged everything back in one at a time and it still fires up. making sure that the bios is still at default and bench test it a few more times. and THANK YOU cascade. better? lol

LMAO

> **garyhibdon said:**
> LOL so i went into the bios, and was checking to verify everything was still default, and to my surprise, the bios version was 0401. . . .their up to 0503 if im not mistaken. lol any idea how to update inside of linux, because thats as up to date as my cd goes, and i never saw an option to check the net for newer ones

501, but near enough. That board has "EZ Flash 2", so getting the new BIOS on should be really simple. 

List of instrucions here- 

[http://vip.asus.com/forum/view.aspx?id=20070215223109668&board_id=1&model=P5B+Deluxe%2FWiFi-AP&SLanguage=en-us&page=1]("http://vip.asus.com/forum/view.aspx?id=20070215223109668&board_id=1&model=P5B+Deluxe%2FWiFi-AP&SLanguage=en-us&page=1")

---

### Post by garyhibdon on 2011-01-20
lol thanks there boss. got it all straight, no more error codes on that. so what made you say no on the velociraptor? i figured 150 gig 1000 rpm hdd @ 64megs would run a little quicker then my 32 meg 320 gig p.o.s.

---

### Post by Paqman on 2011-01-20
> **garyhibdon said:**
> so what made you say no on the velociraptor? i figured 150 gig 1000 rpm hdd @ 64megs would run a little quicker then my 32 meg 320 gig p.o.s.

For me, it's a no brainer:

150GB Velociraptor = £90 for a small performance increase compared to a 7200RPM drive.
40GB Intel X25-V SSD = £60 for a big performance increase
80GB Intel X25-M SSD = £130 for an even bigger increase

Keep your 320GB 7200rpm drive for your data and put your OS on an SSD. Magnetic drives are great for bulk storage, but they're a dead-end if you're looking to up your I/O speed. 

How much value you'll get out of sinking cash into upping I/O really depends on how you use the system.

---

### Post by garyhibdon on 2011-01-20
i meant 10,000 rpm but yeah. you probably knew that. and i'm just not sure im ready to make the plunge to ssd. thats alot of money and i just cant justify it in my head. what kind of speed increase could i actually expect? the other part is im trying to match my entire system and do all the little, cheaper stuff to do what i can without spending an arm and a leg, and if i was going to go ssd, i'd want this. not worth the money yet.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227512&cm_re=ssd_120gb-_-20-227-512-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227512&cm_re=ssd_120gb-_-20-227-512-_-Product)

---

### Post by cascade9 on 2011-01-20
Raptors/Velociraptors have great access times, really good throughput and I/os, but are  outclassed by SSDs. 

The new SATAIII models are far to expensive, they only look good compared to an SSD on size, and you could run a 2nd drive if you want space. The older models are slower, due to smaller platters, slower interfaces, older tech, etc.. 

Even the newer SATAIII 450/600GB models arent that far ahead of the fast 7200s in a lot of places, and older 300GB models are slower (in some ways) than the fast 7200s. An old 150GB model would be slower almost eveywhere. 

BTW they are only 16MB (old models) and 32MB (new models) cache.

---

### Post by garyhibdon on 2011-01-20
oops. lol i was thinking of a 2Tb drive i saw. my bad. . . again

---

### Post by Paqman on 2011-01-20
> **garyhibdon said:**
> thats alot of money and i just cant justify it in my head.

Er, you can get an Intel one for less than a Velociraptor, so I don't really follow your logic.

---

### Post by garyhibdon on 2011-01-20
my logic atm is i've been up for 36 hours and counting. lol i just looked at one of the ones you recommended and i never saw that. the only ones i was looking at were the 2 and 3Tb drives. lol stupid me. sorry paqman and cascade, i sucede both points that you two made. i'll try to look before i speak again and make sure we're on the same page. lol

---

### Post by garyhibdon on 2011-01-20
my logic atm is i've been up for 36 hours and counting. lol i just looked at one of the ones you recommended and i never saw that. the only ones i was looking at were the 2 and 3Tb drives. lol stupid me. sorry paqman and cascade, i sucede both points that you two made. i'll try to look before i speak again and make sure we're on the same page. lol



AHHHHHHH!!!  i didnt even send it twice!!! epic fail on my part. lol

---

### Post by 1clue on 2011-01-20
Oops.

It seems that I posted without reading the extra page or two of posts that happened in the meantime.

---

### Post by garyhibdon on 2011-01-22
so,  will actually listen to any ideas that come about because I've learned my lesson. 
does anyone have anymore ideas to work on the speed here? After checking my logs several times, i have verified everything i can think of and found no further issues. so i think i'm ready to actually LISTEN this time.

And btw, sorry for being a pain in the **** to begin with

---

### Post by 1clue on 2011-01-23
OK Gary,

First thing to do is to start doing what you normally do, and keep tabs on what sort of performance you currently get.  Save this one someplace, most people who try to optimize performance like to have a benchmark from day zero, but often they never think of it until months later.

You'll want to keep tabs on this sort of stuff:
[LIST=1]
[*]Physical memory usage.
[*]Virtual memory usage
[*]Memory used as disk cache (probably irrelevant if you're using virtual memory at all)
[*]CPU usage on all cores.
[*]Disk usage on all disks, partition space.
[*]Disk bandwidth used on all disks individually
[*]Disk bandwidth used on the disk IO interface (sata card, whatever)
[*]Video card CPU load, etc.
[*]Network load.
[*]How choppy is the graphics rendering?
[*]How degraded is the sound?
[*]How long does the foreground task freeze while something goes on in the background?
[*]Are there deadlocks?
[*]I'm sure I missed some things.
[/LIST]

You'll also want to find out what sort of benchmarks pertain to your particular type of use, and perform them on your system whenever you change something.  But keep in mind that while a general benchmark can help you see where you stand with others by that benchmark, the one that really counts is the task you run when you're using your system.  3x that game, for example.

Some of this stuff you can get a GUI applet for, and have it always running.  When you're gaming, have the applet visible so you can see how much CPU, memory etc is being used.  If something pegs to 100% for any significant time, then that's the bottleneck.  Look into improving that thing.

Look for the tools that make sense to you for measuring your system performance.  The best tool is not always the one that dumps the most irrelevant information on the screen, but the one that clearly and concisely shows you what you're interested in knowing in a way that you can tell what's going on at a glance.  I 'grew up' on the command line, so things like top and htop and other command-line tools don't bother me at all.  Even so, I still use things like Gnome panel for my normal system monitoring.

Don't bother upgrading something unless YOU see it being a bottleneck on YOUR system, when you're doing something that you think is unacceptably slow.  What I do is going to be drastically different than what you do.  You could buy exactly my hardware, and chances are we won't have the same bottlenecks.

If your system suddenly degrades, look in the logs.  Now that you've cleaned them up you should be able to spot errors easier.  Get familiar with the entire log, as bizarre as that seems it can teach you a lot about what your system is doing.

You don't have to do all this at once.  It's an ongoing process and a moving target.  I'm still learning a lot, and I'm 45.  Keep in mind that with anything, the amount of effort you put in to understanding and maintaining a process, the better the results you will get out of it.

I would suggest that rather than having all your questions under this thread, separate them and make a relevant title for each topic.  If necessary post links to other threads that might describe your situation accurately.  Use the search feature to see if somebody else already asked that question, but don't interrupt their thread with your own questions unless you feel it's REALLY pertinent.  Sometimes I begin my post with "I was reading <link to a thread> and am having a similar problem but didn't want to confuse that thread.  Here's how it's different on my system...."

Good luck and have fun.

---

### Post by garyhibdon on 2011-01-23
as ive said many times, thank you much for fast and concise answers 1clue. its people like you that keep technology growing and moving without losing sight of where it started. 



and like i said, thank you very much. im going to continue looking into this. ive already been watching some of these the lst week or so to see what happens, so i must have learned something. ;-)

---

### Post by cascade9 on 2011-01-25
Damn it, I though I hit 'post'.....ohh well, I cant be bothered to write out in detail what I wrote last time, but here is the gist of it. 

Gnome system monitor is a bit of a resource pig. Its only really handy for the ability to see CPU use over time (and then you can correlate what caused that RAM spike, CPU use spike, etc).

Onboard video can really screw up results. They use CPU power and main system memory bandwidth, so graphically 'heavy' tasks will create more load than a standalone video card (and because its using those system, anything else that uses them will be slowed down by the onboard video) 

Checking var/logs inst a bad idea. I normally only do it when I think there is a serious problem though. 

Dont go to crazy on any single benchmark. I've seen people 'tune' thier machines from a single benchmark, then find that all they've done is make that benchmark better, but hurt everything else. 

Easy hint- in your BIOS, disable all the junk you dont use or need (eg, firewire, serial ports, parallel ports, unused IDE ports, etc). Set your HDDs, dont leave them on 'atuo-detect' (detecting the HDDs does take time). You might only gain a tiny amount, but liek they say in drag racing "seconds are made up of lots of hundredths of seconds"

---

### Post by 1clue on 2011-01-25
Cascade,

I agree with pretty much everything you said in that last post.

The things you bring up are what you need to keep in mind when you're trying to make sense of the results, and figuring out what to do about it.

At the stage Gary is at, he's just trying to find out what's slowing his system down.  Not details exactly, but big bottlenecks.  Not enough RAM, not enough CPU (for whatever reason) or whatever.

I completely agree about not focusing on one benchmark, unless that benchmark is the system's performance when running your most demanding real-life scenario in which case it's perfectly fine to do that.

IMO, if your system hits swap at all more than once a day you might consider getting more.  I might be an extreme case, but if you know what's going on when you swap, it's like being in an airplane that's about to crash, and you stop to read a book before fastening your seat belt.  You never hit swap when your system isn't working.  When it's working, it means you're waiting for something to finish, and here you have to swap RAM over to disk?

I actually go the opposite direction here.  I use tmpfs anywhere I think it will do any good.  I have 12G RAM, so when it uses the swap partition that really means it's using RAM as a disk drive.  If I run out of RAM then it writes to the disk, but not until then.  It's been several months since I actually swapped anything out, and that was when I bumped it up to 12.

Another thing that gnome system monitor does is tell you how much of your RAM is used as a disk cache.  In my case, usually more than what the system thinks of as active.

I'm not sure if I would go nuts with PAE on a 32-bit system.  That's a cluster ****.  I don't know how well it handles that sort of thing, back when they went from 16-bit to 32-bit they did something similar and it was a noticeable performance hit when you had to page out.  The more you paged out the worse it got.

If you're using onboard video and you're running out of CPU, then consider getting a video card, even if you're just browsing the web.  The performance improvements for even a cheap video card are stunning, and to get a decent one helps a lot even if you don't consider yourself to be video-bound.  Try to gauge how much video performance you need and scale the card to that.

---

