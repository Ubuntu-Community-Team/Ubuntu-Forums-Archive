---
title: "Emulating  CP/M operating system - CP/M-86 ?"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-08
Hi, 

I have been using  CP/M  during many years. I would like to know if LINUX can emulates these machines, ie. operating system? 

Have you too used some of these machines in the past? 

Thank you

---

### Post by Jerry N on 2011-09-08
I have used CP/M but not CP/M-86. I haven't heard of a linux emulation of CP/M-86 but that doesn't mean it doesn't exist.  I can't imagine that there would be much interest in emulating CP/M or any of the other old stuff like TRS-DOS, MultiDos, or DOSPLUS.  Most people in these forums weren't even born when these were in use!  

Jerry

---

### Post by haqking on 2011-09-08
> **Jerry N said:**
> I have used CP/M but not CP/M-86. I haven't heard of a linux emulation of CP/M-86 but that doesn't mean it doesn't exist.  I can't imagine that there would be much interest in emulating CP/M or any of the other old stuff like TRS-DOS, MultiDos, or DOSPLUS.  Most people in these forums weren't even born when these were in use!  

Jerry

simh is in the software centre. not sure if it does cp/m though.

see here As of April 2008, Peter Shorn's version of **SIMH** supports the  8080, Z80, and 8086; supports a number of OS's of the CP/M era including  IMDOS, MDOS, and NorthStar DOS; and a number of hardware platforms of  the era. Check [Peter Schorn's Altair SIMH site]("http://www.schorn.ch/cpm/intro.html") for the latest verision of SIMH and for links back to the  [SIMH Web site]("http://simh.trailing-edge.com/"). SIMH supports many mainframe and minicomputers of the 1970's and earlier

---

### Post by anewguy on 2011-09-08
Man, I haven't been around CP/M for a lot of years - surprised to see someone else who still remembers!  The good old days - writing your own software BIOS code to adapt the OS to your specific hardware, etc..  Actually was fun, but I've pretty much forgotten it.  Funny how Ms/Dos used the same interrupts, etc., eh?

There is a utility to read CP/M based files in synaptic package manager.

If you'd like to emulate CP/M, you might might want to see this link:

[http://www.andrewault.net/2010/02/01/emulating-a-z80-and-cpm-on-ubuntu-linux/]("http://www.andrewault.net/2010/02/01/emulating-a-z80-and-cpm-on-ubuntu-linux/")

A link included there to download the emulator is to a page that has CP/M 86 emulators as well, so you may want to check it at:

[http://www.gaby.de/edownl.htm]("http://www.gaby.de/edownl.htm")

Remember this is after you have some sort of dos emulator installed - they recommend dosemu from the repos.

I'm not sure how old it is and if it still applies, but it might be worth a shot!

Dave ;)

EDIT:  I tried the instructions - when I went to run dosemu I got an error about memory mapping and to be honest I'm just not that interested in going back to try CP/M to worry about fixing it.  So, I can't give you an opinion of how CP/M itself actually looks in the emulator.

---

### Post by honeybear on 2011-09-08
Indeed CP/M CP/M was before DOS. 
Zx/80 is so not pretty much the CP/M ... of old first computers


Who still has some floppy disks of the old good CP/M?   
- Not that bad, but I had so other apps ... [http://www.gaby.de/edownl.htm](http://www.gaby.de/edownl.htm) 


Did you code in Assembler or this kind of Basic 1984/1986?

Please guys, make screenshots, for making cool website of those apps here by gaby.de

---

### Post by Zill on 2011-09-08
> **honeybear said:**
> ...
Have you too used some of these machines in the past?...
Yep!  DEC PDP-11, Osborne 1 and Amstrad PCW8512.

Would I go back to a CP/M O/S?  **NO!**  ;-)

---

### Post by anewguy on 2011-09-08
I even remember when CP/M was NEW - a real + over what little we had before!

Brings back memories of populating boards from scratch, building your own parallel, serial, etc., cables, debugging soldering joints, (remember the old Digital Research boards?), etc. etc., etc..

Anyway, I couldn't leave well enough alone.....

I installed dosbox and it works fine.


Dave ;)

---

### Post by anewguy on 2011-09-08
I could be remembering very wrong here, but I seem to remember Microsoft first approached Digital Research to write MS/DOS, and I think that's why the old CP/M interrupts carried forward.

Love those old processors and the fun you could have!

Dave ;)

BTW - For those not old enough to know - don't confuse Digital Research with DEC (Digital Equipment Corporation) - 2 different animals!  All of the old DEC stuff is valid, just distinguishing between DR and DEC is all. ;)

---

### Post by haqking on 2011-09-08
> **anewguy said:**
> I could be remembering very wrong here, but I seem to remember Microsoft first approached Digital Research to write MS/DOS, and I think that's why the old CP/M interrupts carried forward.

Love those old processors and the fun you could have!

Dave ;)

BTW - For those not old enough to know - don't confuse Digital Research with DEC (Digital Equipment Corporation) - 2 different animals!  All of the old DEC stuff is valid, just distinguishing between DR and DEC is all. ;)


yeah DR-Dos which is indeed why they did. I was gonna say jack killian for some reason but i mean gary kildall...LOL (not the midnight caller)
wasnt DR originally called something like Intergalactic or something cool like that ?

---

### Post by anewguy on 2011-09-08
> **haqking said:**
> yeah DR-Dos which is indeed why they did. I was gonna say jack killian for some reason but i mean gary kildall...LOL (not the midnight caller)
wasnt DR originally called something like Intergalactic or something cool like that ?

You know, I really don't remember - again I think it's those recreational activities of the late 60's/early 70's kicking in! ;)  Actually it's been so long ago I'm a little surprised I remember what I do - done an awful lot of technical work since then and it really got pushed into the cob webs!  ;)

Gee, maybe I don't feel so old now!  ;)

OLD GEEZERS UNITE!!!!

---

### Post by haqking on 2011-09-08
> **anewguy said:**
> You know, I really don't remember - again I think it's those recreational activities of the late 60's/early 70's kicking in! ;)  Actually it's been so long ago I'm a little surprised I remember what I do - done an awful lot of technical work since then and it really got pushed into the cob webs!  ;)

Gee, maybe I don't feel so old now!  ;)

OLD GEEZERS UNITE!!!!


ha well im still a spritely 38, but i remember reading a lot about it when i started with computers back in the early 80's

---

### Post by anewguy on 2011-09-08
> **honeybear said:**
> Indeed CP/M CP/M was before DOS. 
Zx/80 is so not pretty much the CP/M ... of old first computers


Who still has some floppy disks of the old good CP/M?   
- Not that bad, but I had so other apps ... [http://www.gaby.de/edownl.htm](http://www.gaby.de/edownl.htm) 


Did you code in Assembler or this kind of Basic 1984/1986?

Please guys, make screenshots, for making cool website of those apps here by gaby.de[http://ubuntuforums.org/showthread.php?t=1838585](http://ubuntuforums.org/showthread.php?t=1838585)

Mostly assembler in those days for me - some even just straight machine code (hand assemble, load into memory, save it, man does that bring back memories!).  Don't ask me now how to do much though - I think I could still remember a branch and link on BC (or was it BD or some other combo of register pairs!) though! ;)

Dave ;)

---

### Post by Zill on 2011-09-08
> **anewguy said:**
> ...BTW - For those not old enough to know - don't confuse Digital Research with DEC (Digital Equipment Corporation) - 2 different animals!  All of the old DEC stuff is valid, just distinguishing between DR and DEC is all. ;)
...And just to throw some more confusion out there [Data General]("http://en.wikipedia.org/wiki/Data_General_Nova") produced the Nova minicomputers which were vaguely related to the DEC PDP series. ;-)

---

### Post by anewguy on 2011-09-08
Isn't it amazing how back in those days the words "digital" and "data" could really ignite some curiosity? I remember back in the very early 70's it was like "ooooooooooo......".  Of course, we still have to remember RCA, Sperry, Univac, Singer (yep, there were Singer computers!), GE, even Honeywell computers went by the wayside back in the 90's (Bull is still active overseas, but I don't think they have a presence in the U.S., and I think everything now is more server oriented - even things like their old OS's, GCOSx's, are pretty much just emulators on server hardware now) etc.!

Dave ;)

Anyway.......to honeybear -> did you try any of the emulators yet?

---

### Post by anewguy on 2011-09-08
> **haqking said:**
> ha well im still a spritely 38, but i remember reading a lot about it when i started with computers back in the early 80's

Jeez - I missed the 38 reference - rub it in you young pup!!  ;) ;) ;)

Actually, glad you still remember it even at your age.  A lot of the people who might be on the forum are too young to have even know about things like that.  They missed the good old days of knowing your hardware first, how to interface to it second - both hardware and write-your-own drivers, and paying attention to every nibble in memory - hey, if you can grab 3 or 4 bits for more flags, why not?  ;)

What a trip down the old "memory lane" this has been, and yes, Jerry Garcia was right! ;)

---

### Post by haqking on 2011-09-08
> **anewguy said:**
> Jeez - I missed the 38 reference - rub it in you young pup!!  ;) ;) ;)

Actually, glad you still remember it even at your age.  A lot of the people who might be on the forum are too young to have even know about things like that.  They missed the good old days of knowing your hardware first, how to interface to it second - both hardware and write-your-own drivers, and paying attention to every nibble in memory - hey, if you can grab 3 or 4 bits for more flags, why not?  ;)

What a trip down the old "memory lane" this has been, and yes, Jerry Garcia was right! ;)


LOL

took me a minute to realise the jerry garcia reference..;-)

it was cos i was watching midnight caller yesterday.

ahh CP/M and midnight caller all in one thread, so retro...LOL

---

### Post by Jerry N on 2011-09-08
> **honeybear said:**
> Did you code in Assembler or this kind of Basic 1984/1986?

I hand coded machine language for the Intel 4040, the 6502, and the TI 9900.  My first real assembler was for the Z80 (TRS-80 Model I) and I did a lot of assembler work on the 8086/8088.  I also ran Pascal, Lisp (_L_ots of _I_rritating _S_illy _P_arentheses), BASIC and Fortran on my various Radio Shack computers.  The only time I ran CP/M was on a TRS-80 Model 4p that I traded something for.  I also had the CP/M version of Borland Pascal 3.0 on that one. Now that I think back (way back!) I think I also had a CP/M assembler from Microsoft.

Jerry

---

### Post by MG&amp;TL on 2011-09-08
This is fascinating stuff-I don't have a clue what you're on about, but I'm filing it in my head for later googling...:)

Born in '96, so I just remember windows 95, y'see, so this stuff is just, wow. Build a computer from radioshack!?

---

### Post by Jerry N on 2011-09-08
> **anewguy said:**
> Jeez - I missed the 38 reference - rub it in you young pup!!  ;) ;) ;)

Actually, glad you still remember it even at your age.  A lot of the people who might be on the forum are too young to have even know about things like that.  They missed the good old days of knowing your hardware first, how to interface to it second - both hardware and write-your-own drivers, and paying attention to every nibble in memory - hey, if you can grab 3 or 4 bits for more flags, why not?  ;)

What a trip down the old "memory lane" this has been, and yes, Jerry Garcia was right! ;)

How about the fun of building an interface to a solenoid driven Selectric typewriter and then creating and embedding the driver code for the Selectric inside the Superscripsit program?  Of course I had previously embedded the driver for an ASR-33 Teletype in Superscripsit.  For the kids, Superscripsit was an early word processor program.  For those that don't know what a typewriter is, just ignore all this blather! 

Someone is 38? Jeez my youngest kid is older than that!  I may have shoes that old!  

Jerry

---

### Post by Jerry N on 2011-09-08
> **MG&TL said:**
> This is fascinating stuff-I don't have a clue what you're on about, but I'm filing it in my head for later googling...:)

Born in '96, so I just remember windows 95, y'see, so this stuff is just, wow. Build a computer from radioshack!?

Born in 96?  I have a working HP Laserjet that was 5 years old when you were born!  My 5th grandkid was born in 96.

Jerry

---

### Post by MG&amp;TL on 2011-09-08
I love typewriters...I used to have a small collection...teachers got this misty look when I said I'd typed it on a typewriter...

---

### Post by haqking on 2011-09-08
> **Jerry N said:**
> How about the fun of building an interface to a solenoid driven Selectric typewriter and then creating and embedding the driver code for the Selectric inside the Superscripsit program?  Of course I had previously embedded the driver for an ASR-33 Teletype in Superscripsit.  For the kids, Superscripsit was an early word processor program.  For those that don't know what a typewriter is, just ignore all this blather! 

Someone is 38? Jeez my youngest kid is older than that!  I may have shoes that old!  

Jerry


ha ha yeah im 38, but i started computers when i was 10 in 83, i remember CP/M cos i read alot about it when i started out, i was real geek when i was younger ;-)

---

### Post by MG&amp;TL on 2011-09-08
I know. My grandparent's cat was older than I, until about a year ago, when it died.

I have a RAM stick that's older than me.

It's scary.

---

### Post by haqking on 2011-09-08
> **MG&TL said:**
> I know. My grandparent's cat was older than I, until about a year ago, when it died.

I have a RAM stick that's older than me.

It's scary.


i have a body thats older than me ;-)

---

### Post by MG&amp;TL on 2011-09-08
I suppose that's true,if you think about it biologically.

But then, everything gets replaced continuosly, so actually we're in a freakishly young body. :confused:

---

### Post by anewguy on 2011-09-08
I have shirts that are probably older than both of you!!  ;);)

Seriously though, I wonder how the OP is doing on the question?

Dave ;)

---

### Post by lkraemer on 2011-09-08
Ah, CP/M, It was GREAT!

[http://ubuntuforums.org/showthread.php?t=1815406&highlight=TRS80](http://ubuntuforums.org/showthread.php?t=1815406&highlight=TRS80)

[http://ubuntuforums.org/showthread.php?t=1569510&highlight=TRS80](http://ubuntuforums.org/showthread.php?t=1569510&highlight=TRS80)

[http://ubuntuforums.org/showthread.php?t=1801324](http://ubuntuforums.org/showthread.php?t=1801324)

[http://www.retrotechnology.com/dri/index.html](http://www.retrotechnology.com/dri/index.html)

[http://www.trs-80.com/](http://www.trs-80.com/)

[http://www.retroarchive.org/](http://www.retroarchive.org/)


lk

---

### Post by Zill on 2011-09-09
> **haqking said:**
> ... i was real geek when i was younger ;-)
Doh!  So you mean it is actually *possible* to grow out of being a geek? ;-)

---

### Post by haqking on 2011-09-09
> **Zill said:**
> Doh!  So you mean it is actually *possible* to grow out of being a geek? ;-)


no but as your grow up it is easier to hide ;-)

---

### Post by honeybear on 2011-09-09
> **MG&TL said:**
> I love typewriters...I used to have a small collection...teachers got this misty look when I said I'd typed it on a typewriter...

what is it typewriters? 

Was zx-80 really cp-m sort of?

---

### Post by anewguy on 2011-09-10
If you mean the Sinclair ZX80, the answer would be a big no.  

Dave ;)

---

### Post by honeybear on 2011-09-10
> **haqking said:**
> i have a body thats older than me ;-)

too much done and seen... body ages faster :( well or maybe not :) 

CP/M was cool


but man, I had dbtools ;) So cool 
[http://www.retroarchive.org/cpm/dbase/dbase.htm](http://www.retroarchive.org/cpm/dbase/dbase.htm)



I had a sort of game or program. A cursor that was moving randomly onto the black screen. What could it be?


I started my program in basic like with 
> COL=65534
LIG=...


POKE or something like that to print text on a given part of the screen... 

cannot remember ...

---

