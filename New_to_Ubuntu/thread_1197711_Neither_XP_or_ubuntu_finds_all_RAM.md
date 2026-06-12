---
title: "Neither XP or ubuntu finds all RAM"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-26
Xp said pc had 737 mb of RAM, despite it having 1gb of RAM as standard. The graphics card is 512mb making more than 1 gb of RAM, so that doesnt seem to be the answer. Also I added 1 gb of RAM and XP never found it. Ubuntu says the same as XP-737mb RAM. Anyone know how I can try and find the missing memory?-Thanks

---

### Post by wpshooter on 2009-06-26
Have you tried going into BIOS to see what the memory size is listed there ?  If the BIOS, list the correct amount, then try exiting and saving upon exit and see how the O/Ss report the RAM then.

---

### Post by K.Y.A on 2009-06-26
Is your graphics integrated or is it a card? Graphics memory does not add to ram, that is separate. I have 4gb of system ram, and 256mb of Vram. That still means I have 4gb ram.

---

### Post by typos1 on 2009-06-26
Not sure, I thought it was seperate, some one suggested it might account for the descrepency. I dont think so though

---

### Post by sneeks on 2009-06-26
what your motherboard?

---

### Post by typos1 on 2009-06-26
Um, its an Acer Aspire T-180 pc, can you tell from that?

---

### Post by Shazaam on 2009-06-26
If your pc has Integrated Graphics (built into the motherboard) your pc uses "Shared memory". This means that the installed main memory is shared with the graphics card. If it has a "discrete (add-on) video card the main memory is not shared as the card has it's own memory.
You can find out most hardware installed in you machine by running this command in terminal...
```
lspci
```

---

### Post by Zzl1xndd on 2009-06-26
According to my research. 

Processor:  2.4GHz Athlon 64 3800+
Memory: 1GB DDR2
Storage: 160GB hard drive
Optical Drives: Double-layer DVD±RW
Monitor: None
Graphics: Integrated nVidia GeForce 6100/nForce 430 MCP
Operating System: Windows Vista Home Basic

So it is a shared memory videocard.

---

### Post by nwadams on 2009-06-26
yes, so because it is an integrated card some of your ram is being used by the graphics card. This is 100% normal.

---

### Post by mkvnmtr on 2009-06-26
You say you added 1 Gb of ram and neither system found it. When that happened to me it was because I had not seated the ram correctly. I had to try to get it right I think three times before it was seen by the two systems on the computer.

---

### Post by philcamlin on 2009-06-26
your mbo cant handle it then :popcorn:

---

### Post by AoSteve on 2009-06-26
One of three reasons that your ram won't show when you added it.  First, you have an integrated video card, so the Bios seperates a certain amount of ram just for the video card and doesn't report it to the operating system.  This is basically the same "generic" idea as a partition in the ram for the video card only.

The ram may not show because of these problems.

1 :  Improper seating.  If the DIMM is not seated into the slot correctly or all the way, it will not work.

2 :  Motherboard doesn't support that size of DIMM.  When you put a 2GB stick into a mother board that only supports 1GB DIMM's, then the motherboard will do one of two things.  (Show the 1gb on the DIMM and not read the rest which will cause an enourmous amount of memory errors, ask me how I know LOL) or simply not acknowledge the ram at all.

3 :  The ram is not supported by the voltage and the memory module has declared the dimm as dead.  For example, my Kingston hyperx will work at 1.8v in my brothers intel motherboard.   However, my two sticks of crucial 2.2v ram (even though it's the same type), will not even be recognized by the motherboard as it will not run RAM at over 1.8v or at anything above 800Mhz.

So it's one of those reasons..  Seating is usually the most common reason though.

I'd try reseating the ram and see how that works out.  Even my 2000 made MSI motherboard supports 1GB dimms of PC2100 :)

---

### Post by A_M_S on 2009-06-26
> yes, so because it is an integrated card some of your ram is being used by the graphics card. This is 100% normal

The vendors don't lie about the RAM size but also don't say all the truth.

Its easy to be mistaken by the vendors specs. :(

---

### Post by typos1 on 2009-06-27
I got the RAM from Crucial funnily enough, I typed in my pc and it gave me a choice of the ones that fitted. I had trouble seating it and tried several times, but it defo looked like it was supossed to fit. I got 2x512 and ther was 2 in there already.

---

### Post by Terry of Astoria on 2009-06-27
Try one stick of RAM at a time and do the memtest86 boot option from grub for each one to see if any are bad. Then try combinations of two sticks at a time, and see how the machine responds.

---

### Post by typos1 on 2009-06-27
Ok, I did a mem test and everything was ok. Said had 737 mb still. I ll try re-seating them...

---

### Post by MasterProg on 2009-06-27
Is your graphics card integrated into your motherboard? Such cards usually don't have their own memory, so they use some of your RAM. As it was already said, such behavior is perfectly normal. Do you have some other video card? Try to install it and see if all your memory becomes available.

---

### Post by kerry_s on 2009-06-27
> **typos1 said:**
> Ok, I did a mem test and everything was ok. Said had 737 mb still. I ll try re-seating them...

check your bios, see how much memory your giving the vid card, it should be selectable, i'm guessing it's set to 256mb

737-1024=287 
minus 256 for vid
287-256=31
so i'm guessing the system is reserving the rest.

---

### Post by typos1 on 2009-06-27
How do you get into bios?

I thought I had seperate graphics card, how do I tell?

737 =256 = 993 shouldnt it add up t0 1024?

---

### Post by LewRockwell on 2009-06-27
> **typos1 said:**
> Um, its an Acer Aspire T-180 pc, can you tell from that?

does it look like this?

[http://www.pcmag.com/article2/0,2817,2189791,00.asp](http://www.pcmag.com/article2/0,2817,2189791,00.asp)

.

---

### Post by kerry_s on 2009-06-27
> **typos1 said:**
> How do you get into bios?

I thought I had seperate graphics card, how do I tell?

737 =256 = 993 shouldnt it add up t0 1024?

reboot and start tapping the delete key, it might be f2 or f12, i think you can also press the esc key to see what key to press to get into the bios.

> I thought I had seperate graphics card, how do I tell?

you put ram in right, did you see a card?

---

### Post by LewRockwell on 2009-06-27
this guy seems to have experienced the same issue

[http://forums.techguy.org/hardware/588322-probs-acer-aspire-t180-amdx2.html](http://forums.techguy.org/hardware/588322-probs-acer-aspire-t180-amdx2.html)

.

---

### Post by typos1 on 2009-06-27
> **kerry_s said:**
> 


you put ram in right, did you see a card?

Was over a year ago, cant remember, I check when I make sure the RAM is seated correctly. Remember having loads of probs tryin to seat it. 

The real problem is why it doesnt show the extra gb of RAM I installed

---

### Post by LewRockwell on 2009-06-27
> **typos1 said:**
> How do you get into bios?

after you've pressed the start button you'll begin depressing the F2 button approximately two times per second(note that this is actually rather slow and it's important not to depress it too rapidly or the machine will just register it as a bad keyboard key)

once you're in the BIOS set-up area you can check it all out and get familiar with all the functions and settings
(nothing will be changed unless/until you do a "save and exit"...SO IF YOU'RE NOT SURE WHETHER YOU CHANGED SOMETHING BY ACCIDENT WHILE POKING AROUND...JUST MAKE SURE TO "EXIT WITHOUT SAVING")

it's pretty simple actually

.

---

### Post by LewRockwell on 2009-06-27
> **typos1 said:**
> Was over a year ago, cant remember, I check when I make sure the RAM is seated correctly. Remember having loads of probs tryin to seat it. 

The real problem is why it doesnt show the extra gb of RAM I installed

your machine's maximum ram is 4 Gigabytes as per:
[http://reviews.cnet.com/desktops/acer-aspire-t180-es322b/1707-3118_7-32496346.html](http://reviews.cnet.com/desktops/acer-aspire-t180-es322b/1707-3118_7-32496346.html)

you should remove all your ram and then place them back in one at a time to see which ones are recognized and which aren't.

it is possible that they will all register when inserted individually and in pairs as long as they are in common/alike.

if you've got four sticks of 512MB ram(two separate sets, most likely) then the sets are not compatible with each other

you'll need to do some further research and investigation to figure out the exact nature of the deficiency and a suitable solution.

.

---

### Post by typos1 on 2009-07-08
Well they all look the same and I brought them from Crucial and selected then from their site by putting in the make model and processor of my system, so seems unlikely that theyre not compatible

---

