---
title: "Karmic: real-bad sectors on HD Advice sought"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-01-17
Hi all,

So I did read a bunch of posts about Karmic installs and the bad sector thing.

However,   the machine I installed Karmic onto is known to have issues bad enough to make Vista totally un-bootable. How bad that really is I don't know...

The machine: Toshiba A205 --> Core Duo so 64 bit, I installed 9.10 AMD64 which
was tricky because the install kept failing or crashing.

It was revealed that one of the memory card slots is faulty and only recognizes RAM card of 512MB, the second 1GB card failed to be recognized by BIOS and when I ran a memory check with both 1 GB cards, I got errors. Where as when same test was run with 2 512MB cads, there were no errors. I didn't try a test with 1.5 GB just on a whim I tried 1.512 GB of RAM and it worked.

I had to use the slowest speed burn, when making the live CD just like the instructions say...and it helps to check the md5 hash so as to rule out the possibility of a bad download, which did occur once during my install.

Since the Hard Drive was suspect, I wiped it a CopyWipe LiveCD.
Then the install worked, previous attempts had failed.

So with Karmic finally installed and working well, the disk analysizer says I have 64 bad sectors. 

This machine is going to my gf's mother, and I want  it to be as stable as possible without spending any money.  

I have read that some makers of hard drives have their own software that shunts the bad sectors better than a generic utility. 

What do you all think ?
Did ubuntu already 'fix' them during the install ?
Is there an Ubuntu Karmic app that will do the 'fixing' moderately well ?

thank you very much,
wbg

---

### Post by nothingspecial on 2010-01-17
You mean like this,

[ATTACH]143950[/ATTACH]

Test it with something else, I have had this since karmic was in beta.

Although I back up, I`ve had no problems.

Like I said, test it with something else.

---

### Post by wannabegeek on 2010-01-17
what other apps are there ? I've been looking around but haven't
seen anything yet, perhaps using bad search string...

thanks

wbg

---

### Post by egalvan on 2010-01-17
> **wannabegeek said:**
> what other apps are there ?

thanks

wbg

The drive manufacture should have testing software on it's website.
Find a bootable version.

And initial bad-sector re-mapping is done by the drive hardware, not the OS.
When the drive is bad enough to need OS-based re-mapping, it's time to toss it...
it's got far too many bad sectors to be reliable at that point.
(Take the magnets out first, they are fun to play with)

---

### Post by wannabegeek on 2010-01-17
@egalvan

I thought you name was gonna be eiganvalue for a second...a dumb math joke...

anyways...Karmic says 67 bad sectors...assuming that # is accurate,
do you think that many is unstable ?

thanks a ton,
wbg

---

### Post by wannabegeek on 2010-01-17
I tried to find a utility to reassign the sectors ...
the manufacturer is listed as Toshiba from the palimpset (?) window..
I searched toshiba's site and didn't find anything

I'm not sure what a good search string for this is. I've never done this
before.

If anybody has some good suggestions or knows where to look,
please sound off.

TIA

---

### Post by warfacegod on 2010-01-17
Palmipset, the Disk Utility you are looking at, has been know to throw false positives. I suggest booting into the LiveCD you used to install ubuntu with and check the Hard drive with Gparted. Right click the Partition and select Check. If Gparted also says that the hard drive has bad sectors then you would be wise to replace it.

---

### Post by wannabegeek on 2010-01-17
sup  war, you've been busy here :)


running gparted now...

thanks again, this experience with 9.10 has been really good so far.

wbg

---

### Post by egalvan on 2010-01-17
OK, the Toshiba website was less than useful...
I suggest you call them

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/navShell.jsp?cf=su_contact](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/navShell.jsp?cf=su_contact)

and ask if they have any utility to check the hard drive.
They will probably want your machine model and serial numbers,
so have them handy.
( DON"T tell them you are trying to install Linux, they will probably have a cow...
 "Linux Verboten, Nunca Jamas, Quel Horror", and say that they cannot help you.... :)
Tell them that your drive is acting up, and you cannot re-install Windows... )


Back in the Pleistocene era of computers, I used Spinrite to check and "restore" hard drives.
I haven't used anything newer than version 1.2,
so have no option on the newest stuff.
I believe the newest version that Gibson and Co is selling for $80.
[www.grc.com](www.grc.com)  ( Gibson Research Corporation )


Another thought...
If it is a SATA drive (highly likely, given it's Core Duo 64bit)
you may find that it's cheaper, in time spent, to just buy a new 40-80 GB drive.
 These can be found fairly cheap, as everybody wants the TeraByte Monsters.
Your local Mom&Pop Computer Repair may even have a few in stock, that they kept from customer upgrades...


Then again, it's a learning experience to diagnose hardware/software problems... :D


further math jokes...
 if I was in the petro-chemical industry, would my name be Euler?

Not Serious , but very Ernest

---

### Post by egalvan on 2010-01-17
BTW, you may want to consider PartedMagic for all your drive needs.

[http://partedmagic.com/](http://partedmagic.com/)

it's a small but full distro, with the latest gparted, and other drive tools,
smaller than Ubuntu, and loads faster.
it's what I use, and I support them $$

---

### Post by warfacegod on 2010-01-17
> **wannabegeek said:**
> sup  war, you've been busy here :)


running gparted now...

thanks again, this experience with 9.10 has been really good so far.

wbg

Hows the physics going?

Glad you like 9.10 and glad to help. egalvan is right, by the way, if you call Toshiba don't tell them you installed Linux. In fact, if they ask, just say "Linux? What is Linux? We don't need no stinking Linux here!"

Don't feel bad, it'll be like Peter denying Jesus but J didn't mind, he was cool about it. Ubuntu won't mind either. (But it won't forget)

---

### Post by wannabegeek on 2010-01-17
so gparted   gave me all green checks !!

great, this project is done...

now I have to finish my own machine...

awesome help war and egalvan

getting geekier all the time,
wbg

---

### Post by warfacegod on 2010-01-17
The only requirement for being a geek is wanting to be a geek. If you need help with the other machine just ask.

---

### Post by egalvan on 2010-01-17
the fact that you seem to be enjoying this, in spite of problems,
is a sure sign of "geek".

It's the Hacker Syndrome coming out.

Congratulations.

and again
Welcome to *Nix World!

---

### Post by wannabegeek on 2010-01-18
you folks make laugh....

I've always wanted to be a geek...my girl friend is a certified geek...
she bought me my first good scientific calculator, Casio...

It's been great learning my way around Ubuntu, 9.10 rocks...
the Toshiba is working well too, 9.10 AMD64 is a real step up....I want 
a Core Duo badly now...

@warface...physics is moving along, I will be taking a quantum mechanics course which is mostly computational, versus 'modern physics' which was 
introductory...and I may have a job lined up as research project/intern 
for a 25MHz coastal radar array for measuring tidal currents. 

thanks again, 
see you all around the forum,
wbg

---

### Post by egalvan on 2010-01-19
Whoa, a Casio?

Back in *my* day, no geek would be seen, or use,
anything other than an HP Scientific calculator.

A slip-stick hanging from your belt, with the HP in the other holster...

kinda like the cowboys of old with two pistols...

Quantum mechanics were all theory...

We drank tea or cola. anything else was a waste of brain cells,
and thinking time...

"course, I was also an engineer.

Really showing my age.

Laters, y'all!!

---

### Post by warfacegod on 2010-01-19
> **egalvan said:**
> Whoa, a Casio?

Back in *my* day, no geek would be seen, or use,
anything other than an HP Scientific calculator.

A slip-stick hanging from your belt, with the HP in the other holster...

kinda like the cowboys of old with two pistols...

Quantum mechanics were all theory...

We drank tea or cola. anything else was a waste of brain cells,
and thinking time...

"course, I was also an engineer.

Really showing my age.

Laters, y'all!!

What about a Texas Instruments S.C.? And an abacus.

Quantum mechanics is still mostly theory. And don't get me started on String and M theory!

---

### Post by wannabegeek on 2010-01-19
this will get moved to the cafe soon...

@egalvan
HP calcs are the best....RPN for true geeks...see I'm not there just yet

Casio calcs are the bomb for everyday numbers with out  too many operations...they cost $12 and are small and run on solar cell. 

TI's stink IMHO

slide rules...how did you folks ever use those ? I have two and they are not easy to use....one of my professors, wrote in her book that when she 
starting out as a PHD doing research, integrals were done by having grad students carefully plot the function on paper, cut it out, weigh it then spend the day using conversion factors to get the units required. 

That's torture...perhaps egalvan has some experience with this ? and tubes ?   hehe   I actually need to start learning tube amp circuits for a possible job...

---

### Post by warfacegod on 2010-01-19
Did you try the gsmart utility suggested in your other post? I installed it last night and it looks good to me. Lots of useful info. Don't know what most of a damn bit of it means but what I did get was spot on.

---

### Post by egalvan on 2010-01-20
Slipsticks (slide rules), yes I used them during my first year of engineering...
at that time (circa 1971) a serious math & engineering syllabus had at least one, and sometimes two, semesters of "slide rule theory and use".
You learned the theory as well as the practical use of them in the different disciplines/studies.
ALL students were expected to learn at least the basics, which was a one month course.
Everyone else got six months, or a year!
And ALL math students and engineering students had one, or two, rules.

And I remember the emphasis that was put on the decimal point...
Log scales, log-log scales, e-scales, oh my!

I used my Dad's rule, which he had used in College, and post-graduate studies.
High quality rules could last several lifetimes!

By my second year of studies, I had acquired an HP-35C, which was up-graded to the HP-40C about a year later.
The numbers stood for how many operations the machine was capable of.
$400 in 1972 dollars, when a simple 4-banger cost some than $25-$50.
EXTREMELY  well made... all metal was gold-plated, other parts made of heavy-duty engineering plastic, rechargeable batteries, red LED display ( I think 1/4")...
My HP-35 was sold to another student, and my HP-40 worked until my cat urinated on it sometime in 1984.


Calculating integrals by weighing the area under the curve...
I thought everybody did that???

The school had a computer. Yes, just one.
An IBM 1130 series.
8k word memory (true core type, look it up in your Funk&Wagnalls)
4k for the system, 4k for data.
500k word rigid disk on-line storage.
punch card reader.
Line printer.
Selectric console.
FORTRAN, COBOL, RPG.

Yes, just one for the entire school; administration, computer science, math, engineering, fine arts, etc.
3,500 students
350 teachers and professors.
Just one, to rule them all.

As for vacuum tubes, well yes, we used them.
And we learned the theory, and we built circuits with them.
Mainly radio transmitters.... lots of fun.
Tubes were cheaper than transistors, and the transformers were usually  hand-wound ...
Low-cost stuff.

As for an abacus, yes I taught myself to use one. :)

---

### Post by lotharmat on 2010-01-20
> **warfacegod said:**
> Palmipset, the Disk Utility you are looking at, has been know to throw false positives. I suggest booting into the LiveCD you used to install ubuntu with and check the Hard drive with Gparted. Right click the Partition and select Check. If Gparted also says that the hard drive has bad sectors then you would be wise to replace it.

In my experience the false positives thrown by Palimpsest are usually shown by sky-high counts of reallocated sectors. 

I had a Samsung Spinpoint that was reporting 89 of these - Keeping an eye on it I noticed it was increasing so I just RMA'd it with the reason that more and more sectors were becoming bad and thus being reallocated. This is an early indication of disk failure - could be days could be months.

What ever you do; have a good backup regime!

---

### Post by warfacegod on 2010-01-20
> **lotharmat said:**
> In my experience the false positives thrown by Palimpsest are usually shown by sky-high counts of reallocated sectors. 

I had a Samsung Spinpoint that was reporting 89 of these - Keeping an eye on it I noticed it was increasing so I just RMA'd it with the reason that more and more sectors were becoming bad and thus being reallocated. This is an early indication of disk failure - could be days could be months.

What ever you do; have a good backup regime!

Backups are always wise. Here's a good one:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

Palimpset told me my internal had 27 bad sectors, gsmartcontrol said it was fine. I got the basically the same results with another brand new internal yesterday.

---

### Post by wannabegeek on 2010-01-20
gsmart util...will check it out, the machine with said concern
is going back to its owner tonight...

I am going to start using an actual backup protocol like Ghost for windoze...I will dig into the posted thread..

thanks for your continued effort....

@egalvan

I was born in 1975, so i just missed out on the 'good ol days' of computing...I remember my neighbor taking a computer class around 1982 and he showed me all these punch cards...my mom took a computer class in the 80's and learned BASIC .

my family's first PC was an IBM XT with an amber monitor...that was the BEST version of Word Perfect ever and perhaps the best word processor I have used to this day. Super quick, all menus and hot keys driven.

wbg

---

### Post by warfacegod on 2010-01-20
> **wannabegeek said:**
> gsmart util...will check it out, the machine with said concern
is going back to its owner tonight...

I am going to start using an actual backup protocol like Ghost for windoze...I will dig into the posted thread..

thanks for your continued effort....

@egalvan

I was born in 1975, so i just missed out on the 'good ol days' of computing...I remember my neighbor taking a computer class around 1982 and he showed me all these punch cards...my mom took a computer class in the 80's and learned BASIC .

my family's first PC was an IBM XT with an amber monitor...that was the BEST version of Word Perfect ever and perhaps the best word processor I have used to this day. Super quick, all menus and hot keys driven.

wbg

I can't remember if I posted this or not in your threads so I will just in case. Using Norton Ghost in Linux can frag your drive. Tthere's a better synopsis in the thread I posted above. I've read about it in other places but that one sums it up nicely.

*Word Perfect 5.0 for life!*

---

