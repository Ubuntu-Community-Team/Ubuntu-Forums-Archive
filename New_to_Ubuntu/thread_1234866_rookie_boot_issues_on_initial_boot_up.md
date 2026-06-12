---
title: "rookie boot issues on initial boot up"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by jwilsonpro on 2009-08-08
I loaded ububtu 9.04 as a dual boot on my macine. When I go to boot up ububtu I get the following message.

[4.176280] IO APIC resources could not be allocated

BusyBox V1.10.2 (ububtu 1:1.10.2-2 ububtu build in shell (ash)

(initramfs) 

OK I think I know just enough about Linux to know that the last thing is the command line.
I have no idea though as to what the first two things are talking about, how to fix them or why this is causuing me issues so sever as not to boot ubuntu.

I wish I had more time to put into learning this but really I need to get this up and running quick and dirty because I need some linux software for a project I'm working on. I do think that I will permently leave MSFT for LINUX at the moment though I need to get this up and running. Please help I'd love to have a mentor I can lean on from time to time I'm also willing to read tech refrence material as long as it's written approchably to civilians.

Thanks Ububtu Comunity !

---

### Post by Liolikas on 2009-08-08
Enable APIC in BIOS.
--
BusyBox means that your Linux boot failed.

---

### Post by jwilsonpro on 2009-08-08
Thanks for the tip.
I looked around on the bios and couldn't find it. Please elaborate.
I pressed F2 and went through all the menus and found nothing. 
Is there someplace else I should look?

Thanks again I appreciate The help.

---

### Post by louieb on 2009-08-08
It would help to give the age, type of PC, amount of memory, CPU type, and how you installed Ubuntu (Live CD or alternate CD). 

Getting the Busy Box just means the kernel loaded but can't find something it needs to boot properly. Could be any number of things. There are boot options you can try. 

For example power management (acpi) if you think that might be the problem there are options like **acpi=off **and **acpi=force  **

The link below has some of the common boot options, how to try them on a temporary one time basis and how to make an option permanent.   

[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

### Post by jwilsonpro on 2009-08-09
sounds like a plan here's the specs

Dell latitude c 600
800 MHz
265 ram

The live CD ran OK it's the hard drive dual boot inside of windows that won't get up and running for me

I tried to update the bios but it was already up to date

---

### Post by LewRockwell on 2009-08-09
> **jwilsonpro said:**
> sounds like a plan here's the specs

Dell latitude c 600
800 MHz
265 ram

The live CD ran OK it's the hard drive dual boot inside of windows that won't get up and running for me

I tried to update the bios but it was already up to date

it is fun to experiment with the older stuff if you've got the time to spare

you might find it more enjoyable with the ram maxed out on that equipment
(I'd expect it won't take more than 512 or 768, but it might max at a gig)

.

---

### Post by jwilsonpro on 2009-08-09
yea well to you it's a vintage latitude c600 to me it's a daily driver. It would be nice to get it to run ubuntu buy looks like it's not going to happen easily. if you think this is old you should see my antique windows 95 machine with 63 megs, 200 MHz and a whopping 3 gigs. I can squeeze more out of old hardware run to it's limits that fussing with new bells and whistles that bog out the new supper powered crap.

Can someone tell me how to put that apic off comand in so I can try that. I got lost reading the directions on the link. I get it in theory but exactly where to type what commands is where I'm fuzzy.

---

### Post by louieb on 2009-08-10
Wondered how you got Ubuntu to install on a PC w 256MB ram. Then saw the** inside window**s.

A WUBI install is a different animal  when it comes to fixing problems. Haven't used it but heres a guide to working with one [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide") 

256MB ram limits you - last version of Ubuntu that ran acceptably in 256MB was Dapper (v6.06) and its at end of life.

Have a P2-400mHz, 384MB memory, to play with. Puppy (highly recommended) and DSL Linux run just fine on it.

---

### Post by jwilsonpro on 2009-08-10
It's easy to get machines to do things they weren't designed to do, you just demand it of them and never let on that your running things on them that 'Require' (ideally from the manufacturer in theory) twice of what they have for spec hardware. Machines like that stuff they take it on as a point of pride and a challenge then always rise up to the occasion. 

What I don't get is why the live CD ran OK w/ no issues but the dual boot I threw in off the idiot click here list won't run. Can't I just dissable this ACIP thing from ubuntu.

You would get a kick of Autocad 13 running on my 95 machine with 200 MHz and 64 megs, you just run a ram purger and it's A OK for running 2D drawings, well enough to earn a living on it at least.

---

### Post by LewRockwell on 2009-08-10
> **jwilsonpro said:**
> yea well to you it's a vintage latitude c600 to me it's a daily driver. It would be nice to get it to run ubuntu buy looks like it's not going to happen easily. if you think this is old you should see my antique windows 95 machine with 63 megs, 200 MHz and a whopping 3 gigs. I can squeeze more out of old hardware run to it's limits that fussing with new bells and whistles that bog out the new supper powered crap.

Can someone tell me how to put that apic off comand in so I can try that. I got lost reading the directions on the link. I get it in theory but exactly where to type what commands is where I'm fuzzy.

yeah, I've got some vintage legacy 286/386/486 stuff that still juices up and runs...mostly so I can assist others in rescuing old stuff from legacy media

folks around here can't hardly give away anything slower than a one Gigahertz machine(wholesale/scrap for your latitude around here is $20 CASH)

no offense, glad you're keeping the old gals in shape!

.

---

### Post by theozzlives on 2009-08-10
> **louieb said:**
> Wondered how you got Ubuntu to install on a PC w 256MB ram. Then saw the** inside window**s.

A WUBI install is a different animal  when it comes to fixing problems. Haven't used it but heres a guide to working with one [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide") 

256MB ram limits you - last version of Ubuntu that ran acceptably in 256MB was Dapper (v6.06) and its at end of life.

Have a P2-400mHz, 384MB memory, to play with. Puppy (highly recommended) and DSL Linux run just fine on it.

I have Karmic i386 running on a 500 MHz 256 MB RAM clone. I use it for testing Alphas and dual boot. I just had to use the alternate CD, and my on-board Cirrus Logic sound don't work as of yet. Didn't have to turn APIC off or anything.

---

### Post by Ji Ruo on 2009-08-10
> **louieb said:**
> Wondered how you got Ubuntu to install on a PC w 256MB ram. 

Ubuntu 9.04 runs quite well on my old laptop with 256MB SDRAM. I used the live CD to install as well (went straight to install on the start menu). Perhaps having a swap file on the hard drive before installing helped? 

It is a bit slower than I would like with firefox and especially open office, but definitely still usable.

---

### Post by pizmooz on 2009-08-10
> **jwilsonpro said:**
> 
What I don't get is why the live CD ran OK w/ no issues but the dual boot I threw in off the idiot click here list won't run. Can't I just dissable this ACIP thing from ubuntu.


Basically the Live CD installer tries anything it can to boot up the system.  Then the installer tries weed out what it doesn't need and installs this to the HD (via kernel params in GRUB and stuff in the initrd).  It looks the installer didn't configure these things for your system correctly, because the hardware is older.  
If you are really curious to get it going (for a learning experience) a good point to start would be to add the 'noapic' kernel parameter.  To do this, catch grub before it boots (hit a key in the first screen you see after the BIOS) , press 'e' on the default item, then add 'noapic' the end of the line.  If you don't want to go to a bunch of trouble, which is quite reasonable, just try a different distro as mentioned above.

---

### Post by louieb on 2009-08-11
> **theozzlives said:**
> I have Karmic i386 running on a 500 MHz 256 MB RAM clone. 

> **Ji Ruo said:**
> It is a bit slower than I would like with firefox and especially open office, but definitely still usable.

lol - I guess I'm just picky and expect more from my everyday computer.  
My 1st Pc was a Radio Shack color computer used a TV for a monitor and a cassette player for storage. Cost $600.

> What I don't get is why the live CD ran OK w/ no issues but the dual boot I threw in off the idiot click here list won't run.

When it works a WUBI install is the easiest way to Linux. When it doesn't Its harder that a normal install to get going.   

Still would like to help you get Linux going at this point you can get better help if do a traditional installation. Heres some reading to get you started. [Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Sidewinder1 on 2009-08-17
**Off topic* *louieb...WOW! I love that pic! my younger brother's first 'puter was a "trash 80"... Takes me back...My first was an AT&T pc6300 (actually, in the office we had an IBM PC with 360 k floopy drives, got to play with that a bit but was totally in the DOS dark)...It's nice to see some nostalga and old farts like me. * *Off topic**
Thanx,
Side

---

### Post by mrbiggbrain on 2009-08-17
Currently i have minimal installs of ubuntu 9.04 running on a few pc's, and a flashdrive. for relevence, my flashdrive version can plug into any PC and boot ubuntu 9.04 with

Fluxbox
wcid network manager
Naim
nano
dillo
links 2

as well as a slew of games (from pacman to chess, solotare, blackjack)

music players, mail clients, ect

all in 1GB flashdrive (about 90mb remaining), and the lowest specs iv had it running well on is

128mb of ram, 255mhz pentium II, 8mb GPU.

---

### Post by theozzlives on 2009-08-17
You can run Ubuntu on a 32 MB system: [https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), although I've never tried it.

---

### Post by egalvan on 2009-08-17
> **jwilsonpro said:**
> 

What I don't get is why the live CD ran OK w/ no issues but the dual boot I threw in off the idiot click here list won't run. Can't I just dissable this ACIP thing from ubuntu.



The LiveCD can run in 256M of RAM, but has "issues" doing an install.

To best install with only 256M, use the Alternate Install CD...

or use the Server Install, then add the Desktop of your choice 
Gnome, KDE, xfce, Crunchbag, etc.

Puppy is also an excellent choice for such limited memory.
The 4.x versions (and under) run well in 256M.

---

### Post by egalvan on 2009-08-17
> **theozzlives said:**
> You can run Ubuntu on a 32 MB system

Just realize that this is for pre-7.10 versions.

8.04 Hardy has issues with less than 64M.

---

