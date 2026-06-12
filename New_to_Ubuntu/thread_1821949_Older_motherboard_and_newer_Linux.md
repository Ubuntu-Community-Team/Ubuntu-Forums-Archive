---
title: "Older motherboard and newer Linux?"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by ajpulley on 2011-08-09
For my direct question, skip to next paragraph.  I'm new to Linux if it isn't obvious.  I've been using Macs most of my life, for work and for personal, of which I'm very familiar with.  However, I'm not so familiar with Windows or Ubuntu.  Last year, I had to get Windows 7 for my company, and installed a copy via Parallels 6.  I also took an interest in Linux, and decided on Ubuntu.  I installed the long-term build of version 10, then upgraded to 11.04, also installed as a virtual machine.  I've played around with alot of it, trying to familiarize myself with the operating system and associated software... at least with what I can through the GUI aspect of it.  I have a basic understanding of hardware, how it all works together, and terminology.  What I am not good at is understanding drivers, firmware, and command line interface as I simply don't need it with my Macs.  However, I do search for and read up on what I need to.  I'm fairly intelligent, and research as much as I can.  But, sometimes, I need some help getting started in the right direction.  Now...

I decided to build a tower out of old PC components I was given, and would like to install a newer release directly on this computer.  For me, this is the next step in learning Linux and Ubuntu with respect to hardware.  According to 11.04's system requirements, I need a minimum of specifications, for which I have (processor speed, RAM, etc.).  My question is, will I need external drivers, or does Ubuntu include and install what I need?  Will Ubuntu even work on all computers, or are certain motherboards and processors not "built" to work on anything but Windows?  Specifically, I'm working with an *ASUS KV8 SE Deluxe* motherboard with an *AMD64 Athelon 3200*.  I just don't have enough experience with Windows or Linux to know how to start from scratch.

I know some of you may be easily irritated with some of the questions new folks post.  But, we've all started somewhere.  If it brings any comfort, know that I have spent a couple evenings searching on here and about the web trying to find information that would satisfy my question.

---

### Post by elgordodude on 2011-08-09
Congratulations on building your own machine and installing linux. It is an excellent way to learn computers, and thank you for asking if someone could say if they thought it would work before you threw it all together and then hit the "oh crap" button.

To answer your question I'm typing this on a AMD Athlon 64 3200+ on an Asus motherboard. Running Ubuntu 10.10.

A year and a half or so ago, it took some work to get the wireless drivers to work correctly, but in the latest release they work out of the box. I have to do a little bit of work to install the proprietary nvidia drivers for my 8800gt (I need the cuda from time to time...) The only real problem I've had is with an hp printer, but even that got sorted out after awhile. So, yes, ubuntu (at least 10.10, I had trouble upgrading to natty) should work great.

Best of luck, and welcome to the forums.

---

### Post by ajpulley on 2011-08-09
Thank you, I really appreciate your experience.  I meant to show one of many articles I've read about building a Linux computer.  Here is one:

[http://www.kitchentablecomputers.com/linux3.php](http://www.kitchentablecomputers.com/linux3.php)

I also read up on booting from a CD, and adjusting the BIOS that most motherboards have.  It seems to be fairly simple, at least based on reading but not yet doing:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

I'll experiment with hardware until I find what works for me.  For example, the MB has an analog and digital monitor interface card that it came with.  I don't remember the specs- itmay change, or I might leave it.  I have yet to find a wireless PCI adapter which I want to install.  My keyboard uses the older PS/2 interface, as will my mouse, for now.  But, I intend on ending up with a RAID 1 configuration, a card reader, and external firewire ports before I'm done.

My intent is to eventually move away from Macintosh, and rely more on Linux.

I hope this will help someone else who is trying to do the same thing I am in the future.

---

### Post by elgordodude on 2011-08-09
No worries, you just happened to have my processor and a similar (I think) mobo, I've got an A8N-VM. Anyway if you're building out, a couple of things, yes, ubuntu is the best place to start with linux, its popularity and the depth of the user forum make it a very responsive and easy to use distro. Don't know if I'd start with 11.04, there seem to be a fair number of problems associated with the switch to unity, 10.04 may be a better place to start, especially with an older system.

As far as your build goes, I'd definitely get an ESD strap, they're a neccessity if you want to build many or play around a lot with one machine. Do you need RAID? Adding RAID adds a new level of complexity, especially if it's on a boot disk. Firewire is getting a little passe, consider gigabit ethernet, USB 3, and esata cards, they cost about the same, and will probably give you more flexibility, depending of course on whatever else you're connecting to :)

A round of applause for moving from mac to linux, if nothing else you will save A LOT of money.

I should ask, how does your memory look? I hope you have at least a gig, preferably 2. Other than that, put it together, and see whats happening.

---

### Post by ajpulley on 2011-08-10
I suppose my MB is similar; yours is newer, faster, and has many upgrades.  For curiosity's sake...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131490](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131490)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131570](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131570)

---

### Post by the.phantom on 2011-08-10
i am not a expert !

but have a few computers and on my "Main" system i am using that processor and have no troubles at all !

i have taken a few computers that had a operating system on it and were totally contaminated with virus/worms ,trogens that people just got a replacement. and have played "mix and match" with them and had great success so far


if i wonder if a video card will work i just google "nvidia xyz and ubuntu " and start reading and works great so far !

i got a barebones kit a while ago and did that on all parts before i spent the $ and for $200 got a quad core amd 64 processor ( not the latest but works great) and by googeling all the parts i knew i had a great chance of success and did !

a friend wanted a fast new system and i googled all the items and now he has to get a 5 point safty belt for his office chair !

i have a amd X2 7750 that i made up and have ubuntu and mint on it and it is my loaner!  people have trouble i try and fix problems and let them play with linux while i work on their box !

so far have 2 converts ;-DDDD

first one could not believe the speed on the "cheap system" 
second one keeps saying " is it legal with all the free software"

---

### Post by ajpulley on 2011-08-10
Thank you for your input!

I assembled everything in a temporary, table-top layout, reconfigured  the BIOS, and attempted to boot from the x386.iso.  The first couple of  attempts were unsuccessful.  Once, was simply due to the fact that I  bumped the DVD drive, and a line of code was missed, putting the boot  into error.  The other time seemed like it took a very, very long time,  over 20 minutes in fact, just to get to the purple screen with "ubuntu"  and five progress dots underneath.  

The next step is to determine if there is an .iso specifically for the  AMD, and try to find information that would give me an idea of what is  acceptable boot time from a disk, and what isn't.  I also want to see if  I can update the BIOS in my MB.

---

### Post by amjjawad on 2011-08-11
It's 9:15am here and it's time for me to ZzZz (Yes, I'm a batman ;) )

A very quick post for you.

Ubuntu in most cases will work Out-of-The Box. If you will need any driver, it shouldn't be a problem at all.

[http://en.wikipedia.org/wiki/Athlon_64](http://en.wikipedia.org/wiki/Athlon_64)

For Ubuntu Search use: [www.googlubuntu.com](www.googlubuntu.com)

Google.com will help you a lot.

Good luck and sorry for my poor input :)

---

### Post by Paqman on 2011-08-11
> **ajpulley said:**
> 
The next step is to determine if there is an .iso specifically for the  AMD

Nope. Ubuntu comes in desktop and server, 32-bit and 64-bit. AMD uses the same architecture as Intel, so just use the regular desktop ISO in 32- or 64-bit as required.

> 
and try to find information that would give me an idea of what is  acceptable boot time from a disk, and what isn't.

Shouldn't be any longer than a few minutes. 20 is waaaay too long. You can try booting from a USB stick if your mobo allows it. I suspect what's going on is that there's some hardware problem that's causing it to hang.

> 
I also want to see if  I can update the BIOS in my MB.

You could, but the general advice for BIOS is "if it ain't broke, don't fix it!". Like any firmware update BIOS updates run a small but real risk of bricking your hardware, so be careful.

The methods of updating it available to you vary widely depending on the manufacturer.

---

### Post by ajpulley on 2011-08-11
> **amjjawad said:**
> 

[http://en.wikipedia.org/wiki/Athlon_64](http://en.wikipedia.org/wiki/Athlon_64)

For Ubuntu Search use: [www.googlubuntu.com]("http://www.googlubuntu.com")

Google.com will help you a lot.



Thank you, I've been using Google and Wikipedia for years.  Almost always, if my key words are correct, I'll get enough hits.  You see, when you're lost in the woods, it does no good to follow the river downstream back towards town when you don't know where the stream is to begin with.  

In other words, I have to have a fairly good idea what to start searching for to find an answer that will help.  If I have no idea where to start, it makes it difficult to search for the unknown.

---

### Post by ajpulley on 2011-08-11
Paqman, thank you for the verification.  Because of it, I borrowed an old Dell, and the 32-bit install disk came to life very quickly.  I misspoke earlier.  I went through the set-up menu of the MB, but it is telling me there is no BIOS installed.  I'm currently self-educating myself in this respect to find a solution.  Either way, something is causing the install process, or the boot-from-optical process to hang just after the purple screen with the keyboard-equals-stickfigure-in-circle thing on the bottom of the screen.  I'm not sure what to start troubleshooting as far as hardware is concerned, so if I can't figure it out, I'll get a new(er) MB and processor. It would be nice to have some of the more recent options that my MB and processor do not have.  

Again, thank you everyone for your help.  Eventually, I'll learn more about the booting/loading process of how a computer works, which will help me understand better what I am doing, and why.

---

### Post by amjjawad on 2011-08-12
> **ajpulley said:**
> Thank you, I've been using Google and Wikipedia for years.  Almost always, if my key words are correct, I'll get enough hits.  You see, when you're lost in the woods, it does no good to follow the river downstream back towards town when you don't know where the stream is to begin with.  

**In other words, I have to have a fairly good idea what to start searching for to find an answer that will help.  If I have no idea where to start, it makes it difficult to search for the unknown**.

For me, that is the fun part of the challenging part :)

I'm just like most of the people in this world, like the easy solutions but sometimes, I feel that so boring and easy. Therefore, I always look for some challenges when it comes to Computers and Real Life too.

This is a great place to seek for help. You see many will jump in and do their best to help. A word from here and a link from there will do the needful :)

I'm one of those who are in love with OLD machines and I always look for old machine and do some tests. It's so much fun.

Good luck and I'm sure you'll achieve what you want :)

P.S.
Sorry for the previous short reply but I was going to bed and had zero energy :)

---

### Post by ajpulley on 2011-08-12
I have a GeForce 6600; is it a fairly decent AGP card?  I read NVIDIA's driver download page, and it gave the following:

"Note that many Linux distributions provide their own packages of the  NVIDIA Linux Graphics Driver in the distribution's native package  management format. This may interact better with the rest of your  distribution's framework, and you may want to use this rather than  NVIDIA's official package.'

Is the only way to know which is better is to try installing?  Or, how can I determine if it is needed?  Under Admin., I looked up installed drivers and the utility indicated no proprietary were installed.

And, any suggestions, or dissuasions, towards a 802.11g wireless PCI card?

---

### Post by elgordodude on 2011-08-12
You're stretching my memory a little in the era of FM1 sockets and GTX 5xx GPUs, but as I recall the 6600 was a great AGP card. That said, AGP is currently about as popular as Nintendo 64, so if you're trying to play CoD Black Ops, I foresee problems, if you're surfing the internet, checking your email and watching the occasional movie, you should be golden. If you're halfway in between it sounds like a grey question where results will depend on your memory and power supply.

As far as a wireless card goes, I had great results with a Zonet zew1642s it's MIMO, technically n-class but works great on my g network and worked out of the box with ubuntu 10.10 Should be about $10 US on the internet.

edit* Apparently you edited within a minute of my post, drivers may well get sticky with such an old card, but something will definitely work. I prefer the current nvidia drivers on my cards, but they're certainly not necessary, it depends on what when why and how you use your machines.

---

### Post by ajpulley on 2011-08-12
Thank you.  No, I don't play games.  To be honest, I wouldn't know the difference between Nintendo products.  So, I'll assume the one you mentioned is antiquated, or bad in some degree.  My use for this once stable will be mainly office-type work.  The reason I asked is it meets the requirements for Unity, according to one of Ubuntu's websites.  In fact, it is mentioned specifically in an example, and I just happen to have one that works.  The driver is a recent one; the latest version was posted this month.

I will search for the Zonet zew1642s.  I would like the n-specification, but I don't need it.  Most of the n-cards I see need a PCI-Express slot, which I don't have.  Just finding something I know will work will be helpful since I'll have to buy this card.

---

