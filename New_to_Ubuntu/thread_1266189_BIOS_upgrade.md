---
title: "BIOS upgrade"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by zer010 on 2009-09-14
How good is Ubuntu at dealing with a BIOS update?  How would I go about updating the BIOS on my 1999 machine?  I've never updated a BIOS before, not even in WIn.  I've read things about flashing it, or something.  I've heard it can be tricky and risky.  Is it any easier, less risky, on a linux sys?  Any help is greatly appreciated!

---

### Post by NoaHall on 2009-09-14
Don't do it. If your BIOS works fine, leave it alone. You'll probably do more damage than good. And you'd have to do from BIOS, not from within a OS. (Or at least that's how I've always done it. Through the OS is riskier)

---

### Post by davidsrsb on 2009-09-14
More details on the PC/motherboard please.
Is the bios updater dos based or a Windows gui application?
Dos is more likely for a 1999 machine
If so Freedos should do the job

---

### Post by zer010 on 2009-09-14
I wish I could provide more info. That's another thread of mine.  More detailed hardware info. In Win, I used to use CPUz and GPUz. I have not found an equivalent in Linux yet.

---

### Post by roger_1960 on 2009-09-14
Hi

See this page:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00007682&lc=en&dlc=en&cc=us&product=93562&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00007682&lc=en&dlc=en&cc=us&product=93562&lang=en)

I strongly suggest that you dont try this using Ubuntu or linux.  The BIOS update will probably be DOS based needing a floppy drive present. The updater program runs from the floppy and rewrites the flash ROM containing the BIOS routines. If it goes wrong, the PC will be useless!  I updated the BIOS on an old laptop, but had to reinstall windows just to do it. ( I have never used freeDOS but perhaps that could work to write the routine to the floppy?)

---

### Post by MoonRocketZero on 2009-09-14
Is there a reason you need to (or want to update it), like new functionality, or do you have some problems you are trying to rectify, or?

Or are you just doing the upgrade to do it because you never have before?

If you are just doing it for "fun" then I'd say don't, as said above you can totally brick a motherboard with a bad flash so unless it will add functionally you require leave well enough alone.

If you are set on upgrading or have a good reason to try it -- if it's a desktop PC why not pop the case open and see if there is any model/system info printed on the Mobo (may be right on the board or possibly on stickers on the board) -  that's usually a pretty easy way to find out (would likely work if it was a laptop also but it'll be a lot more of a pain to pop open most laptop cases);)

---

### Post by Tomas5 on 2009-09-14
I'm wanting to update the BIOS for the reason that I have been told with an update my laptop will be able to run 8gb of memory so I'm looking for the performance side of an update. How should I go about updating it?

---

### Post by roger_1960 on 2009-09-14
Hi again

That seems unlikely.  To run more than about 3Gb, it has to have a 64 bit processor and that is rather unlikely in a 1999 machine. Have you updated the processor? Are you the original poster on this thread? and is the laptop the Compaq presario?

---

### Post by NoaHall on 2009-09-14
No, he means to enable the MOTHERBOARD to support that much. It's two different matters.

---

### Post by roger_1960 on 2009-09-14
Mmm, but he said its a laptop........

---

### Post by NoaHall on 2009-09-14
So?

---

### Post by roger_1960 on 2009-09-14
So - I've never heard of a 1999 laptop which can take 8Gb of ram on its motherboard, but I realise I may be wrong, in which case I live and learn.

---

### Post by NoaHall on 2009-09-14
That's the point of flashing it ;) So it does support it. It's not always a physical limit, more in the coding

---

### Post by zer010 on 2009-09-14
I'm the OP, and I was hoping to gain more functionality if possible.  Also, I was kinda wondering if, as updates for Ubuntu come out, the compatability with my mobo/BIOS might be left behind.  Possible? Would a new BIOS flash help?  Also, my current BIOS's functionality (as far as configuration) is lacking.

I understand that BIOS flashing is extremely RISKY.  If it can really only be done in MS environments, that makes me a little more squeemish about trying it.

---

### Post by Garrovick on 2009-09-14
Updating the BIOS is the best way to brick your computer, out side of throwing off a three story building.

And for 32 bit computers, 3.5 gigs of RAM is all that the machine will see.

---

### Post by Bradtek on 2009-09-14
It would be irresponsible for us to give you advice without knowing actual details like :the model of your laptop, the current bios version

If the sticker with serial number etc has faded / come off
try looking in the bios for clues, turn off the boot screen graphic
and you should see at least the bios version while it's starting as well as other hardware info.

If you can't manage this, take it to someone who can tell you.

in 10 + years of amature and professional tinkering with Desktops and Laptops I have only ever once had a firmware/bios upgrade go wrong, and 
that was recoverable.

---

### Post by expatCM on 2009-09-14
if you run 

sudo lshw

at a terminal you will get lots of information about your hardware.

To save it as a file use 

sudo lshw >hw.txt

Similarly, if you run 

sudo dmidecode >bios.txt

you will get a text file of your BIOS version and settings.

---

### Post by zer010 on 2009-09-15
> **expatCM said:**
> if you run 

sudo lshw

at a terminal you will get lots of information about your hardware.

To save it as a file use 

sudo lshw >hw.txt

Similarly, if you run 

sudo dmidecode >bios.txt

you will get a text file of your BIOS version and settings.

If I run the command >.txt, where will the txt file be saved to?

---

### Post by expatCM on 2009-09-15
take a look at 

/home/username/

---

### Post by expatCM on 2009-09-15
oh and remember ....  if you cannot find a file you can always search for it, especially if you know the full name ....  From the menu

Places / Search for Files

---

### Post by MoonRocketZero on 2009-09-15
> **expatCM said:**
> if you run 

sudo lshw

at a terminal you will get lots of information about your hardware.

To save it as a file use 

sudo lshw >hw.txt

Similarly, if you run 

sudo dmidecode >bios.txt

you will get a text file of your BIOS version and settings.

I'm not the OP but I just tried that out and WOW those are 2 very handy commands to know, thx! for the tip on that.

---

### Post by LewRockwell on 2009-09-15
> **zer010 said:**
> How good is Ubuntu at dealing with a BIOS update?  How would I go about updating the BIOS on my 1999 machine?  I've never updated a BIOS before, not even in WIn.  I've read things about flashing it, or something.  I've heard it can be tricky and risky.  Is it any easier, less risky, on a linux sys?  Any help is greatly appreciated!

Anyone wishing to work with their BIOS version should become familiar with what it is, what it does, and the method(s) for altering/changing/upgrading it

here is one link to get you off of ground-zero:

[http://www.bootdisk.com/](http://www.bootdisk.com/)

.

---

