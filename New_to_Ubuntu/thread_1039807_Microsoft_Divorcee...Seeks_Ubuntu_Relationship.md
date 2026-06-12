---
title: "Microsoft Divorcee...Seeks Ubuntu Relationship"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-01-14
Howdy Folks,

I am up to my neck in alligators still trying to drain the freakin' swamp. I'm an ole fart sick of Microsoft who need TLC to get onboard the Linux train. If I can figure this out hopefuly others may follow in the mass exodus.
I am attempting new Ubuntu install (7.10 CD) on new computer.
Hardware: P5N73-AM LGA775 Motherboard  Intel E8500 cpu  NVIDIA GeForcec 7050 chipset  4 gig RAM
MoBo has built in LAN connection  250 GB harddrive  cdrom blah blah

Where I need direction is:

1. Best Linux book for newbie
2. Information on correct setup/procedure for wired ethernet connection. I have all the server/gateway addressing values but need to know where to stick what. Need to know how to activate ethernet port,etc.
3. Download of nVidia drivers to correct Safe Mode graphics bootup.
4. Sound programming for speakers.

5. Want to split 250 gig drive during partition in case "other" OS load becomes necessary.

So basically I'm at ground zero and haven't had the chance to screw anything up yet. Maybe I can do all this in an orderly fashion and have some of my gray hair remaining at the end. :^)

Oh yeah, I am somewhat familiar with Terminal mode as I played with Hyperaccess back in the eighties.

So pleeze direct me to the correct forum or I may be there now. I'm not sure.

Looking forward to a Linux infested world,

Ed   -in the Ozarks

---

### Post by handydan918 on 2009-01-14
> **ozark_hillbilly said:**
> Howdy Folks,

I am up to my neck in alligators still trying to drain the freakin' swamp. I'm an ole fart sick of Microsoft who need TLC to get onboard the Linux train. If I can figure this out hopefuly others may follow in the mass exodus.
I am attempting new Ubuntu install (7.10 CD) on new computer.
Hardware: P5N73-AM LGA775 Motherboard  Intel E8500 cpu  NVIDIA GeForcec 7050 chipset  4 gig RAM
MoBo has built in LAN connection  250 GB harddrive  cdrom blah blah

Where I need direction is:

1. Best Linux book for newbie
[/CODE]There are lots of books, but I tend to think online documentation is best. I'll let others post their preferences on this.```

2. Information on correct setup/procedure for wired ethernet connection. I have all the server/gateway addressing values but need to know where to stick what. Need to know how to activate ethernet port,etc.

```I think the thing to do here is to hook it up and try it out. Linux usually doesn't require much help with networking, outside of wireless and the proprietary drivers it comes with...```

3. Download of nVidia drivers to correct Safe Mode graphics bootup.
```This depends on the video card...Lots of folks do well with envyng. (terminal> sudo apt-get install envyng```

4. Sound programming for speakers.

5. Want to split 250 gig drive during partition in case "other" OS load becomes necessary.


```No problem, if you understand partitioning a little The Ubu live cd will give you the opportunity to slice and dice at install time.

[CODE]So basically I'm at ground zero and haven't had the chance to screw anything up yet. Maybe I can do all this in an orderly fashion and have some of my gray hair remaining at the end. :^)

Oh yeah, I am somewhat familiar with Terminal mode as I played with Hyperaccess back in the eighties.

So pleeze direct me to the correct forum or I may be there now. I'm not sure.

Looking forward to a Linux infested world,

Ed   -in the Ozarks

Welcome. You will do well. ( One old fart to another...)

---

### Post by earthpigg on 2009-01-14
> Ubuntu install (7.10 CD)

ubuntu has releases every 6 months.... 7.10 came out in the **_10_**th month of 200_**7**_. clever, huh? ;)

8.04 (4th month of 2008) is a Long Term Release version that will be supported for 3 years.

8.10 is the most recent standard release, that will be supported for 18 months.

i suggest picking one of those two... you can download the ISO and burn it yourself, or [ship it ]("https://shipit.ubuntu.com/")will mail you one for free.

1. the internet, and this forum right here ;) im sure someone has an actual suggestion, but that is all i needed (i have no technical background, moved over to ubuntu about a year ago)

2. test it on a live CD. it may pick it up automatically without anything done on your end. if not, click around and see if you can figure it out a bit. if you cant, make a thread on the forum.

3. [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) (i google searched "nvidia drivers ubuntu")

4. see if it works on its own... if not, make a thread.

5. its easier to install windows first and then ubuntu, but not essential... if you install ubuntu first and then windows, expect to need to make a thread asking "my ubuntu dissappeared from the boot menu, how do i get it back?!!?". its a 5 minute fix to get it back.

:)

edit: im not an old fart. i feel left out. :(

---

### Post by handydan918 on 2009-01-14
> edit: im not an old fart. i feel left out. 

Don't worry. You will be. Just give it time.

):P

---

### Post by albinootje on 2009-01-14
First of all, try both Ubuntu 8.04.1 and 8.10, the 64 bit version.
8.04.1 is the Long Term Support release, should be more stable, but 8.10 has some more recent software.
These two are also a good choice to solve your network- and graphics problems.

Second of all, I can imagine that Ubuntu (or Linux) books are nice to have around, but they have one disadvantage compared to the Internet, and that is that they get old soonish.
Of course it depends on the specific topics, but just FYI.
The publisher O'Reilly comes to mind, for example :
[http://oreilly.com/catalog/9781593271183/](http://oreilly.com/catalog/9781593271183/)

And third. 
As a Linux beginner it's a good idea to start with a dual-boot, or have some other machine(s) with Internet around.
Some things might not work in Linux for some time (think about certain win-modems and win-printers).
Even if you want your full hard disk to have Ubuntu, it can be handy in the beginning to run MS-Windows in a virtual machine, like VirtualBox.

And last one :

**********************
Welcome to Ubuntu ! :)
**********************

---

### Post by ozark_hillbilly on 2009-01-14
> **handydan918 said:**
> Welcome. You will do well. ( One old fart to another...)

Dan,

IS a seperate graphics card necessary to set up Ubuntu? I thought the motherboard GeForce firmware would\could handle basic graphics. I'm not a gamer or soemeone who needs powerful graphics capability.
Also if I go ahead and load 7.10 now is upgrading later a hair pulling process. If I can get a stable OS environment I will be loathe to mess it up "if it's not already broke."

Ed

---

### Post by Artemis3 on 2009-01-14
> **ozark_hillbilly said:**
> 
I am attempting new Ubuntu install (7.10 CD) on new computer.
Hardware: P5N73-AM LGA775 Motherboard  Intel E8500 cpu  NVIDIA GeForcec 7050 chipset  4 gig RAM
MoBo has built in LAN connection  250 GB harddrive  cdrom blah blah

Where I need direction is:

1. Best Linux book for newbie
2. Information on correct setup/procedure for wired ethernet connection. I have all the server/gateway addressing values but need to know where to stick what. Need to know how to activate ethernet port,etc.
3. Download of nVidia drivers to correct Safe Mode graphics bootup.
4. Sound programming for speakers.

5. Want to split 250 gig drive during partition in case "other" OS load becomes necessary.

Please download a newer version, 7.10 is too old. This will ease your nvidia issues. For the partition, when installing there is a moment where you can choose amount of harddisk (in %) to use. After install you can use network manager (network icon on top right) to configure your network.

Installing a second OS is not really newbie friendly, (installing later that other os will make your ubuntu unbootable). It is easier if you install that other OS first then install Ubuntu and choose the % of harddisk to use in the installer.

I don't understand what do you mean with sound programming of speakers. The best book is asking in this forum ^_^

---

### Post by albinootje on 2009-01-14
> **ozark_hillbilly said:**
>  IS a seperate graphics card necessary to set up Ubuntu? I thought the motherboard GeForce firmware would\could handle basic graphics. I'm not a gamer or soemeone who needs powerful graphics capability.

A Nvidia videocard is an *excellent* choice when using Linux, perhaps the best you can have right now!

---

### Post by caro on 2009-01-14
Definitely start with the Live CD to test things out.  That's the easy way to test your hardware.  On mine, the networking (wireless at that) worked out of the box.  

I don't have a book, but the forums are great.  Also check out [http://www.linuxcommand.org]("http://www.linuxcommand.org") to understand the basic on how the file systems and basic commands work.

---

### Post by blackened on 2009-01-14
> **ozark_hillbilly said:**
> ...So basically I'm at ground zero and haven't had the chance to screw anything up yet...

Give it time :)

> So pleeze direct me to the correct forum or I may be there now. I'm not sure.

Looking forward to a Linux infested world,

Ed   -in the Ozarks

You found it already. And it looks like we're not far from each other geographically. Welcome.

---

### Post by Artemis3 on 2009-01-14
> **ozark_hillbilly said:**
> Dan,

IS a seperate graphics card necessary to set up Ubuntu? I thought the motherboard GeForce firmware would\could handle basic graphics. I'm not a gamer or soemeone who needs powerful graphics capability.
Also if I go ahead and load 7.10 now is upgrading later a hair pulling process. If I can get a stable OS environment I will be loathe to mess it up "if it's not already broke."

Might not be hair pulling (but it might go wrong), you will end downloading almost 1gb of data. I urge you to download the latest cd image (8.10), burn to cd, and install from that instead.

---

### Post by handydan918 on 2009-01-14
> **Artemis3 said:**
> Might not be hair pulling (but it might go wrong), you will end downloading almost 1gb of data. I urge you to download the latest cd image (8.10), burn to cd, and install from that instead.

I would agree, with the exception that I would HIGHLY recommend using 8.04, since it is the LTS version(long term support) 
You will continue to have security updates available for 8.04 for the next 30 months or so....and you can still pull the pin and drop the grenade anytime you want to.

---

### Post by albinootje on 2009-01-15
> **handydan918 said:**
> I would agree, with the exception that I would HIGHLY recommend using 8.04, since it is the LTS version(long term support) 

I agree.

And even when the OP would want more recent software with 8.04, there's several repositories with backports around.

---

### Post by ozark_hillbilly on 2009-01-15
I downloaded 8.10and burned a new CD. Was unable to do hash checks from MD5sum or others. They would not run on this old pentium system running w/ Win 98. 
Loaded CD into new computer and errors were generated from BusyBox v1.1.3:
on bootup:

(initramfs) [254.609.279]  ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

also got some stuff about
        irq14: nobody cared (try booting with "irqpoll" option)

I'm not sure how to get a screenshot of the BusyBox error listing to show on this forum. 
The Fun has Begun,

Ed

---

### Post by ozark_hillbilly on 2009-01-15
Well I went ahead and requested CD version 8.04 via mail channels since my download copy generated errors.

It took several hours to download the 8.10 at 3-400 k. Not sure I want to do that again. I guess I can install 7.04 and upgrade when new CD arrives. I also think it would be wise to partition HD and put some version of MS windows on it but I presently only have copies of 2000 and 98. I don't want to do it but I think I will run into problems with online games my wife loves to play and I think they involve Shockwave.

Memory test run w/ Ubuntu CD had a good result. My 4 gig of RAM seems solid. 

When running Live CD will I have to enter network parameters each  session? Or is it stored on hard drive?

And finally, do I need to order a graphics card to get around having to boot up in safe graphics mode? 

15 in Northern Arkansas,

Ed

---

### Post by handydan918 on 2009-01-15
> **ozark_hillbilly said:**
> 

When running Live CD will I have to enter network parameters each  session? Or is it stored on hard drive?
Hmm, not sure what network parameters you are referring to, but nothing will be persistent until Ubu is installed to the hard drive...> 

And finally, do I need to order a graphics card to get around having to boot up in safe graphics mode? 
Absolutely not. Nvidia is a great card, albeit with proprietary drivers which can be annoying for a noob to install. We can get you thru it.> 
15 in Northern Arkansas,

Ed

Brrr.

85 in Ventura county, California.

















:D

---

### Post by steveneddy on 2009-01-15
What's the minimum age limit to be classified as "old fart"?

---

### Post by handydan918 on 2009-01-15
> **steveneddy said:**
> What's the minimum age limit to be classified as "old fart"?
It isn't so much an age limit as a state of mind. Kind of a zen thing, really. 
If you remember the sixties, you weren't stoned enough, for example. Not so much rules as guidelines.

I suspect that everyone who wants to apply the title to themselves is welcome to the club.

"If after the age of fifty, you wake up in the morning and nothing hurts, that is strong evidence that you died during the night..."

---

### Post by ozark_hillbilly on 2009-01-15
Not sure of the exact age to qualify as ole fart but these conditions will give you a clue:

notice hair growing out of the ears and nose

loads of mail from AARP

eyebrows block your vision at times

---

### Post by handydan918 on 2009-01-15
Bwahahaha!!!!!!!!

nice!

---

### Post by LinnetLegs on 2009-01-16
> **steveneddy said:**
> What's the minimum age limit to be classified as "old fart"?


Age is unimportant. Take a look at my avatar. When you look like that - that is when you are an old fart!!:P



ps - it isn't really me. :o

---

### Post by Keen101 on 2009-01-16
Apress books are really good. Also Wiley.

my favorite (Ubuntu) Linux books are:

_**Begining Ubuntu Linux: from novice to professional**_

[http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590596277](http://www.amazon.com/Beginning-Ubuntu-Linux-Novice-Professional/dp/1590596277)

and

[B][U]Ubuntu Linux Toolbox
[/U][/B]

[http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933](http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933)

---

### Post by albinootje on 2009-01-16
> **ozark_hillbilly said:**
>  
also got some stuff about
        irq14: nobody cared (try booting with "irqpoll" option)


Try booting with that option, see here for instructions :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

