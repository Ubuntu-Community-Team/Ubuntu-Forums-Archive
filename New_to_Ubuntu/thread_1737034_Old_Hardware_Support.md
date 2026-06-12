---
title: "Old Hardware Support???"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by StormcrowofRohan on 2011-04-22
I have had Ubuntu for about two weeks.  During these two weeks I have done nothing but try to adapt MY pc to THEIR os.  Is it so much to ask that you have a little bit more compatibility?  Sure, all of my hardware is old, but how hard was it for me to run everything wide open on Windows?  It wasn't hard at all.  They supported my hardware with drivers, etc.  

I have installed 4 native Linux games on this system, and there has yet to be one that I've gotten past the launcher.  Every single one has said that my system capabilities were not enough, or that I needed to adjust settings which weren't even available.

Now, before I just completely wipe my system and reinstall Windows...can you tell me there is hope and that there is actually software that will run my old hardware correctly?

I'm not buying new hardware, to run it mediocre...

Yes, I'm a gamer.  But, I like Linux and would like to establish my niche here. As much as Windows was convenient.  I hate how it looks, how it behaves, how it slowly drains the life out of my computer and my sanity.  I would rather just attain functionality with Ubuntu, because frankly I'd rather work for a nice product than be handed it by Windows.

I hope I didn't sound too bitter, just bear with me.  I'm new to this and I've been struggling with it since the beginning. :P

Here are my specs:

Ubuntu 10.10 Lucid Maverick(?) lol
AMD Athlon(tm) 64 Processor 4000+, ATI Radeon x1600 Sapphire, 2 GB RAM, and I'm not sure what other hardware you need listed...

If you can suggest any sort of software that will allow me to run them properly.  I will be eternally grateful.

---

### Post by lykwydchykyn on 2011-04-22
I'm not personally an expert on game performance, but I can tell you that it pretty much comes down to the video chipset and the video drivers.  RAM, cpu, etc. is typically not an issue if your computer isn't faded beige and coated with 2 inches of dust.

When you want high performance from a video card on Linux, it can get tricky.  

ATI/AMD chipsets are tricky.  IMLE the proprietary drivers work better for some things, but not others.  Have you tried installing the proprietary drivers (fglrx)?

---

### Post by spillin_dylan on 2011-04-23
I can't say I personally run any of your hardware you have listed, but I know that what you have should be more than sufficient to run a Linux distro....  

Currently I am running Linux on a Pentium III 800MHz, with 512 MB of RAM and 18GB of HD, and it runs very well!  Maybe a little slow, but it sure beats the Windows 98 the system came with!

---

### Post by mrob184 on 2011-04-23
Might be a problem with your install.
My rig is not as strong as yours and I'm running full settings in video and enjoying all the built in compiz features.
My rig.
socket A 2000 Athlon
old Machspeed socket A motherboard with VIA KM400 chipset
old ATI 9250 128mb vid AGP video card

I di not install any propietary drivers that I'm aware of as I just let Ubuntu do its thing during install.
Hang in there...someone with alot of experiance will be along.

---

### Post by LowSky on 2011-04-23
The problem is your video card. Sorry but Ubuntu and Linux in General do not support ATI video card released before the HD series. Its been this way for about 2 years. The rest of your PC's specs are fine.
As a gamer you are stuck with Windows. Sorry.

Many in the community will not say this but I will. Run the OS that runs the software you want to use. Ubuntu is not Windows in any way. With WINE you can run some Windows made programs but in doing so they usually run slower. My own experience I have Starcrat 2 installed on Ubuntu and can only play in low graphics mode. In Windows 7 it runs on full graphic settings. I have a Nvidia GTX 460 if your wondering.

I get you are upset with Windows and need a change. Unfortunately what you want and what is possible are not the same thing. You will need to make sacrifices. So you can either shell out $40+ on a newer graphics card, or reinstall Windows. Your choice.

---

### Post by khelben1979 on 2011-04-23
> **LowSky said:**
> The problem is your video card. Sorry but Ubuntu and Linux in General do not support ATI video card released before the HD series. Its been this way for about 2 years. The rest of your PC's specs are fine.
As a gamer you are stuck with Windows. Sorry.

I disagree. there's no reason to use Windows because of older pc hardware, he can choose an older version of Ubuntu which uses an older version of the X server where the AMD Catalyst 9.3 is supported. it's officially supported.

Another alternative is to go for the latest version of Ubuntu and make sure to only use the open source RADEON driver. And the reason for this would be if the latest software is more important than graphics performance.

For higher graphics performance together with the latest version of Ubuntu, then a hardware upgrade is the only way to go. The Radeon X1600 is very old by todays standards so you really can't expect too much from it.

---

### Post by StormcrowofRohan on 2011-04-23
Thank you for all the replies.  I have tried installing the proprietary driver for my card, but when I run it in terminal it goes through the process so fast that I don't see whether it was successful or a failure.

Even after this none of the games seem to launch correctly.  I think I may just go find myself a newer graphics card, any suggestions on a cheaper Nvidia that would be compatible for a few years.  I just want to be able to use Ubuntu and a few of the dev games, because I'd like to learn a bit of coding and how the system functions.  It's so much more stimulating than Windows.

---

### Post by jramshu on 2011-04-23
I ran 10.10 Desktop on the following with no problems:
AMD Athlon(tm) XP 1800+
1550Mhz
NVCrush11 [GeForce2 MX Integrated Graphics]

No problems, didn't try games though. It's now running Ubuntu Server 10.10.

---

### Post by khelben1979 on 2011-04-24
If you intend to get a better video card: [Newegg.com]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Pagesize=100").

It doesn't matter too much which model you choose, because nVidia supports old as new video cards with their drivers. What matters is probably price and how it sounds, if it's quiet or loud with the fan.

Geforce GT 430 doesn't sound too bad from what I can see. Going down too low in price you risk getting something you don't want, not even if you decide to avoid all games...

---

### Post by mastablasta on 2011-04-24
> **LowSky said:**
> The problem is your video card. Sorry but Ubuntu and Linux in General do not support ATI video card released before the HD series. Its been this way for about 2 years. The rest of your PC's specs are fine.
As a gamer you are stuck with Windows. Sorry.


that is totally not true!!! you have no idea what you are talking about. i have a 9600XT radeon that runs fantastically on opensource drivers.

To the OP you card driver is the issue why things are so slow. If we can fix that you should be running at blazing fast speeds. 
Now then a poster here already established that ATi dropped Linux support for your card and decided not to make any new drivers (you can thank them later). This is not Ubuntus fault. 

BUt what now? well thewre are some people out there with soem free time oon their hands and they decided to create/revere engineer the drivers so that people can run these cards in Linux. These are so called opensource drivers.

What you can try to do is to upgrade them by installing Edgers PPA.read the instructions here on how to install them and what to do if it doesn't work: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


here is some more information 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

you will see that you should be able to get 3D support on your card. 

but lets also be fair here to notice that Card is old and nothing special, also WinXP kernel is from 2001 (ubuntu's is from 2010). an upgrade will solve it and should be cheap unless this is a notebook.

---

### Post by grahammechanical on 2011-04-24
Have you ever purchased a PC that did not have a Microsoft operating system pre-installed? If people purchased PCs without a pre-installed OS, then everyone would need to adapt their PC to someone else's OS. Usually it is the retailer that has to do the adapting. The retailer does this by only using hardware that is known to work with the Microsoft OS. 

This is why Microsoft refused to allow its Media Center OS to be sold over the counter. Too many people would be demanding refunds because it did not work with their PCs.

By the way, Microsoft did not support your hardware. The makers of the hardware provided the drivers otherwise they could not put the Windows ready or Windows approved logo on the machine.

I have discs with Windows drivers on them. I do not have a Windows operating system. The drivers came when I brought the motherboard, graphic card and monitor. If more hardware makers supplied Linux drivers or released information about their hardware to the Linux developers then fewer of us would need to adapt our PC to their OS, as you put it.

Regards.

---

### Post by StormcrowofRohan on 2011-04-24
No, this is a desktop.

Can you suggest an open source driver for my ATI Radeon x1600 Sapphire?  I'm not savvy on this subject, so any advice would be appreciated.  I see the list here: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only) but I have no earthly idea what to go with. haha 

I think it would be interesting to at least try them until I can upgrade my card.  The worst that can happen is I have to reinstall ubuntu, which won't be a problem.  I've been running it about 3 weeks now and really don't have much to lose here. lol

---

### Post by TenPlus1 on 2011-04-24
Run Terminal from the Applications -> Accessories menu, and at the prompt type this:

sudo add-apt-repository ppa:xorg-edgers/drivers-only

...it will ask for your password, enter it and you will have added a new repository with the drivers you need for your computer.

You can run the Update Manager and ask it to CHECK for updates for it to find your driver :)

---

### Post by khelben1979 on 2011-04-24
Ubuntu 11.04 is expected to get released in 4 days from now. You will get faster performance from the open source video drivers using this version of Ubuntu. I recommend you try it out! :)

---

