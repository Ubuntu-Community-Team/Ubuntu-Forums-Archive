---
title: "reverse engineering"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by wheel_walker on 2011-03-07
Is it  possible to reverse engineer source code from a binary if we know what language a program was written in, which implementation was used, and what OS and hardware it was compiled on?

---

### Post by turtle153 on 2011-03-07
It is technically possible, but very hard. The code would use sensible variable names, comments and structure, but when it is compiled theres are lost to save space and increase efficiency.

---

### Post by bwang on 2011-03-07
Depending on the jurisdiction in which you live and the license on the program you are reverse-engineering, it may also be illegal.

---

### Post by wheel_walker on 2011-03-07
I live in Brazil and the program and platform are twenty years old.

---

### Post by gordintoronto on 2011-03-07
It's a lot easier if the program is small. Many years ago I generated source code for the Commodore 64 "OS" ROM, and modified it for my purposes at the time.

These days, it seems like a "hello world" program is bigger than the Commodore 64 ROM.

---

### Post by wojox on 2011-03-07
> **wheel_walker said:**
> I live in Brazil and the program and platform are twenty years old.

What are you decompiling, Pong?

---

### Post by wep940 on 2011-03-07
If it's a true compiled language, where the result is really machine code, you can decompile mainly only to the degree of seeing assembler source.  To route that up to a specific language, such as "C" or even Cobol (heaven forbid!) is a lot more difficult.  As already mentioned, any names and comments that make the code readable would be lost.  I know from personal experience disassembling machine code several years ago that it's a lot harder to see the "why" code is doing something, only that it is.  Add to that the optimizations that many compilers add, and you would get some fairly difficult to read source.

---

### Post by Jerry N on 2011-03-07
> **wep940 said:**
> If it's a true compiled language, where the result is really machine code, you can decompile mainly only to the degree of seeing assembler source.  To route that up to a specific language, such as "C" or even Cobol (heaven forbid!) is a lot more difficult.  As already mentioned, any names and comments that make the code readable would be lost.  I know from personal experience disassembling machine code several years ago that it's a lot harder to see the "why" code is doing something, only that it is.  Add to that the optimizations that many compilers add, and you would get some fairly difficult to read source.

I thought disassembling machine code was a lot of fun 30-35 years ago but programs were several orders of magnitude smaller then and most had been written in assembler in the first place.  I thought I was pretty clever when I replaced some unnecessary code inside Wordstar with a driver for my KSR-33 Teletype printer. Things just aren't like they used to be - THANK GOODNESS!!!! (By the way, I wasn't a kid when I was doing that stuff, in fact I had 3 kids before I every got into digital computers)

Jerry

---

### Post by wep940 on 2011-03-08
> **Jerry N said:**
> I thought disassembling machine code was a lot of fun 30-35 years ago but programs were several orders of magnitude smaller then and most had been written in assembler in the first place. I thought I was pretty clever when I replaced some unnecessary code inside Wordstar with a driver for my KSR-33 Teletype printer. Things just aren't like they used to be - THANK GOODNESS!!!! (By the way, I wasn't a kid when I was doing that stuff, in fact I had 3 kids before I every got into digital computers)
 
Jerry
 
Yeah, it actually was fun that many years ago, but times change and things have gotten much more complex. Heck, back in about 1981 or 1982 I bought one of those cheap Sinclair computers and got the 16K expansion for memory. If you ever took a look at the firmware for those things, they were really simple. They didn't give you a blinking cursor, couldn't move around the screen, etc. I hand assembled a word processor with word wrap on/off, justification, printing support, cut/paste support, blinking cursor that could navigate the entire screen, insert/overwrite, etc., converted it to hex, created a rem statement in basic, then poked the hole thing in by hand, and finally adding the termination for the rem statement so that it would be recognized. Obviously it couldn't display the rem statement, but it did load which allowed the word processor to run. Didn't use an assembler because when I first wrote it I didn't have the memory expansion. Obviously, with machine code on a simple machine like that
the resulting program was very small. The trick was growing the size of the rem statement as the document grew. Then I added save and load functions to it that basically just called the rom load and save functions. Since the document was contained within the rem statement it was essentially inside the program. So saving the program actually saved the document - loading did the opposite. Also did a lot of bit work when I worked as a systems programmer and sys admin on large scale boxes. At the time, all that stuff was fun to me - as I've gotten older, I've gotten lazy and don't really care anymore. ;)
 
EDIT:  should probably add that I started with mainframes in 1977 - not nearly as old as some on here, but I sure am not a kid anymore!  :(

---

### Post by wheel_walker on 2011-03-08
> **wojox said:**
> What are you decompiling, Pong?

How old are you, kid?

[http://en.wikipedia.org/wiki/Final_Fantasy_%28video_game%29](http://en.wikipedia.org/wiki/Final_Fantasy_%28video_game%29)

---

### Post by wep940 on 2011-03-08
I guess some of us 55+ 'ers have seen some things that actually help you understand your computer better.  But at the same time, all these "kids" are growing up just using the things like it's second nature.  Anymore, it's probably best to really understand how to use applications than it is the internals, unless you plan to be a systems engineer.

---

### Post by lisati on 2011-03-08
As others have pointed out, for a variety of reasons the task of reverse engineering has its challenges, including possible legal and copyright considerations.

I remember disassembling portions of the ROM on a z80-based computer I had in the late 1980s, and discovering that a significant portion was remarkably similar to that used by the TRS-80. This information helped me unlock some features that were present in ROM but had been disabled when the ROM was customized to suit the hardware.

---

### Post by wep940 on 2011-03-09
Those were the fun days, weren't they? I really enjoyed all of those things, but admittedly things were simpler in those days. Dumping ROM's to see all the functions, particularly, as you found, functions that are not mentioned for the PC, made things interesting and fun. I wish it were the same today, but things have changed so much (although, if I remember correctly, a lot of the underlying interrupts in the BIOS are still left from MS-DOS days, and even those were based on a lot of the CP/M interrupts). ;)

---

