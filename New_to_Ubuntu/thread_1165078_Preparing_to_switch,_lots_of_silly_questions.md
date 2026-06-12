---
title: "Preparing to switch, lots of silly questions"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by linuxfanboy on 2009-05-20
OK you got me. I'm in the process of setting up my computer as dual boot. In the past few weeks Ive read quite a bit about linux, about switching from windows and listened to few podcasts. I cant wait to try a bunch of distros

There are a few questions that I couldnt find an answer for in online guides, prolly cos they seem obvious to people who've been using linux and theyre bit silly. Also I have a few concerns re hardware compatibility cos Im using old machine.

ram question...

My desktop is 5-6 years old technology. Still looks like linux distros dont need much. Thinking of going with ubuntu 9.04 first. My ram is only 256 mb, but Im well over the other requirements.

Will the live cd run at 256mb? Ubuntu site says it needs 384mb, but does that mean it wont run at all below 384mb it or it will just run bad?

Also the 384mb that ubuntu needs to run compiz effects, what does that mean? Does it mean it will eat up 384mb so if you wanna run other programs and games you'll need 384mb + what the game needs? Or is it just an estimate of how much it needs to run properly with games/programs included in there...

How much does ubuntu 9.04 use without running any programs, when it starts up?

I'll prolly end up getting more RAM if I can get linux distros to work on my hardware.

graphic card question...

I have one of the dreaded ati cards unfortunately and its as old as the system, 5-6 years. Having listened to few podcasts, thing that stuck me was when one of the linux outlaws guys burned his ati card by installing drivers from the ati site itself lol.

How can I avoid that? What are the chances of that happening? Is there risk if I just use ubuntu's cd? That cd comes with ready drivers in it...are those more stable then the crap ati writes?

The fact the card is old, is that plus cos drivers for it have been around a while or minus cos well....its old and weak?

Because the machine is this old, if I lose any important part like the cpu or the graphic card Im better off buying new computer then buying parts for the old. Unfortunately I'm not in a position to afford a new pc at this stage, hence my paranoia about this.

fan question

Ive got this persistent problem with the fan, dont know if its cos the machine is old or smth else. Whenever I start it up, I hear this loud sound or about 10-20 secs. Like the fan is working franatically or smth. It seems to happen when I turn the computer off for like hour or smth. If I just turn it off and then on again in few mins It usually doesnt happen.

I monitor the fan and it seems to run pretty stable after those first 20 secs.

During heavy gaming (or buggy games i dont know which) times when the cpu maxes out at 100 or close to it, I see the fan has increased its speed somewhat to counter the heat.

I use a program that monitors its speed but I havent configured it change up/down the RPMs. What changes the RPMs? Is it Windows or smth pre-configured on on the motherboard? If its the windows that controls this, does linux have smth similar to control the fan? Do I have to install drivers to get this function to work on linux?

Basically will it be ok to try out few distros with this fan problem or maybe it could escalate the problem and burn up elements in the computer? If smth goes wrong with linux and it doesnt work properly how long will I have before the system burns up lol

That should be all. I'll write more if I can think of smth. Thanks for the help in advance. :D

---

### Post by halitech on 2009-05-20
> **linuxfanboy said:**
> OK you got me. I'm in the process of setting up my computer as dual boot. In the past few weeks Ive read quite a bit about linux, about switching from windows and listened to few podcasts. I cant wait to try a bunch of distros

welcome aboard :)

> There are a few questions that I couldnt find an answer for in online guides, prolly cos they seem obvious to people who've been using linux and theyre bit silly. Also I have a few concerns re hardware compatibility cos Im using old machine.

ram question...

My desktop is 5-6 years old technology. Still looks like linux distros dont need much. Thinking of going with ubuntu 9.04 first. My ram is only 256 mb, but Im well over the other requirements.

Will the live cd run at 256mb? Ubuntu site says it needs 384mb, but does that mean it wont run at all below 384mb it or it will just run bad?

Also the 384mb that ubuntu needs to run compiz effects, what does that mean? Does it mean it will eat up 384mb so if you wanna run other programs and games you'll need 384mb + what the game needs? Or is it just an estimate of how much it needs to run properly with games/programs included in there...

the live cd probably won't run and you will need the alt install cd to get things installed. 384 is the bare minimum I would try running Ubuntu with.  Compiz relies as much on your video card as it does the ram, maybe even more then the ram.

> How much does ubuntu 9.04 use without running any programs, when it starts up?

I'll prolly end up getting more RAM if I can get linux distros to work on my hardware.

there are lighter variants out there that don't need as much ram

> graphic card question...

I have one of the dreaded ati cards unfortunately and its as old as the system, 5-6 years. Having listened to few podcasts, thing that stuck me was when one of the linux outlaws guys burned his ati card by installing drivers from the ati site itself lol.

How can I avoid that? What are the chances of that happening? Is there risk if I just use ubuntu's cd? That cd comes with ready drivers in it...are those more stable then the crap ati writes?

The fact the card is old, is that plus cos drivers for it have been around a while or minus cos well....its old and weak?

there are built in drivers that should get you running, may not be able to run compiz without propritary drivers though

> Because the machine is this old, if I lose any important part like the cpu or the graphic card Im better off buying new computer then buying parts for the old. Unfortunately I'm not in a position to afford a new pc at this stage, hence my paranoia about this.

just cause you're paranoid doesn't mean 'they' aren't out to get you ;)

> fan question

Ive got this persistent problem with the fan, dont know if its cos the machine is old or smth else. Whenever I start it up, I hear this loud sound or about 10-20 secs. Like the fan is working franatically or smth. It seems to happen when I turn the computer off for like hour or smth. If I just turn it off and then on again in few mins It usually doesnt happen.

I monitor the fan and it seems to run pretty stable after those first 20 secs.

During heavy gaming (or buggy games i dont know which) times when the cpu maxes out at 100 or close to it, I see the fan has increased its speed somewhat to counter the heat.

I use a program that monitors its speed but I havent configured it change up/down the RPMs. What changes the RPMs? Is it Windows or smth pre-configured on on the motherboard? If its the windows that controls this, does linux have smth similar to control the fan? Do I have to install drivers to get this function to work on linux?

fan control is usually done by software

> Basically will it be ok to try out few distros with this fan problem or maybe it could escalate the problem and burn up elements in the computer? If smth goes wrong with linux and it doesnt work properly how long will I have before the system burns up lol

you should be able to try them out but just don't work them hard (windows games won't play) the only thing you might damage is the cpu but you can check your BIOS and see if there is a heat shutdown option to prevent over heating

> That should be all. I'll write more if I can think of smth. Thanks for the help in advance. :D

welcome and hope to see you running Linux :)

---

### Post by Sir Jasper on 2009-05-20
Hi,

Fans wear out over time. Also, if you take the cover off you can inspect the dust and clean carefully as may be necessary.

My regards

---

### Post by J.K on 2009-05-20
> **linuxfanboy said:**
> 
How much does ubuntu 9.04 use without running any programs, when it starts up?
For me, on a fresh, default installation, 150-160mb.

I probably can't answer your other questions right now (beginner myself). The first installation I tried, though, was on my desktop which may be similar to yours. It's about 4+ years old and P4 2.8 with 512mb memory. However, I put xubuntu on there first - am probably going to switch over to ubuntu as I've seen it's a little easier to use, personally, after trying it on another computer.

According to xubuntu.org:

> You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.As for [ubuntu]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

> **Bare Minimum requirements**

 It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the *Alternate install CD* to attempt such an installation. 

[LIST]
[*]300 MHz x86 processor
[*]64 MB of system memory (RAM)
[*]At least 4 GB of disk space (for full installation and swap space)
[*]VGA graphics card capable of 640x480 resolution
[*]CD-ROM drive or network card
[/LIST]
 
**Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor
[*]384 MB of system memory (RAM)
[*]8 GB of disk space
[*]Graphics card capable of 1024x768 resolution
[*]*Sound card*
[*]*A network or Internet connection*
[/LIST]

**Note:** All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 
 
**Recommended for visual effects**

 *Visual effects* provide various special graphical effects for your desktop to make it look and feel more fun and easier to use. If your computer is not powerful enough to run visual effects, you can turn them off and will still have a usable Ubuntu desktop. 
Visual effects are turned on by default if you have a graphics card which is supported. For information on supported graphics cards, see [DesktopEffects]("https://help.ubuntu.com/community/DesktopEffects"). 

[LIST]
[*]1.2 GHz x86 processor
[*]384 MB of system memory (RAM)
[*]Supported graphics card (see [DesktopEffects]("https://help.ubuntu.com/community/DesktopEffects"))
[/LIST]


J.K

---

### Post by mapes12 on 2009-05-20
Hi

RAM - 384MB is usually what's required to run a Live CD installation. My advice would be to use the [alternate installation CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") (text based) which does not require so much system resource.

Graphics card - There are new drivers in 9.04 and you may find that it works OK. If you need nonfree drivers this may help you out: [http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

Fan - not sure about that one.

---

### Post by Mark Phelps on 2009-05-20
Don't know specifically about fan "control", but reporting of fan speeds is done using the lm-sensors package. There is also a package known as gkrellm that can do fan monitoring.  But the results vary greatly.  I have a desktop for which I get full reporting, but on two laptops, there is virtually no reporting. Depends critically on the monitoring chip on the motherboard.

I would ordinarily advise you to boot from the LiveCD, install these packages and see how well they monitor your hardware, but with so little RAM, you're probably not going to be able to do that.

My experience running Ubuntu on a 256MB machine was abysmal -- so slow as to be all but useless, and I installed Xubuntu to minimize the graphics demand on the desktop.

With such little memory, would advise an alternative like Damn Small Linux or Puppy Linux. These and other distros are available from the distrowatch.com website.

---

### Post by linuxfanboy on 2009-05-20
> **halitech said:**
> welcome aboard :)



the live cd probably won't run and you will need the alt install cd to get things installed. 384 is the bare minimum I would try running Ubuntu with.  Compiz relies as much on your video card as it does the ram, maybe even more then the ram.



there are lighter variants out there that don't need as much ram



there are built in drivers that should get you running, may not be able to run compiz without propritary drivers though



just cause you're paranoid doesn't mean 'they' aren't out to get you ;)



fan control is usually done by software



you should be able to try them out but just don't work them hard (windows games won't play) the only thing you might damage is the cpu but you can check your BIOS and see if there is a heat shutdown option to prevent over heating



welcome and hope to see you running Linux :)

There was this chart I saw on ubuntu.com  about graphic  cards and my card was supported for 2 and 3rd not sure about tv out but dont really need that atm...Cant find it now... Does that mean with extra ram I can make 904 work?

Looks like trying 904 is prolly bad idea. I might try ubuntu 804 or 704 instead, to see how my hardware matches up with ubuntu....if i dont get  major conflicts I'll get some more ram so I can use 904. Does that make sense or are they too different to matter?

I cant find an option in my bios to shutdown the computer if tempetures go over certain level which is a bummer. I could use smth like that just in case.

Are programs for monitoring/controlling fans easy to find on linux?

Thanks everyone for your replies, good stuff here.

---

### Post by lovinglinux on 2009-05-20
I have a low-end laptop with 256Mb of RAM and I was able to install Ubuntu 8.10 Intrepid using the LiveCD. As far as I understand, the problem with the RAM is that the Live CD doesn't use the hard drive to run, so it needs to load the OS into the RAM. The Alternate CD allows you to install with less memory because it doesn't load the graphical stuff during the installation process.

Once the Ubuntu is installed, it will run fairly well with just 256 Mb of RAM, but it will use more swap memory, which makes it slower. I have Compiz installed and running, but I don't remember trying the full effect option (I'm on my desktop now). This machine is basically used by my mother for Internet, flash games and playing videos. It's her first computer, so I setup the system in a way that she basically do everything from Firefox. So, she only use one application almost all the time, except when playing videos, since she likes smplayer. 

I wouldn't expect to run 3D games, if this is your intention.

I would recommend installing Hardy Heron 8.04 instead of Jaunty, which I think is less RAM hungry and it's LTS (Long Term Support). It will be supported until 2011, when you will be able to upgrade to a newer LTS.

Would be much better if you could buy more RAM tho.

---

### Post by halitech on 2009-05-20
> **linuxfanboy said:**
> There was this chart I saw on ubuntu.com  about graphic  cards and my card was supported for 2 and 3rd not sure about tv out but dont really need that atm...Cant find it now... Does that mean with extra ram I can make 904 work?

Looks like trying 904 is prolly bad idea. I might try ubuntu 804 or 704 instead, to see how my hardware matches up with ubuntu....if i dont get  major conflicts I'll get some more ram so I can use 904. Does that make sense or are they too different to matter?

I cant find an option in my bios to shutdown the computer if tempetures go over certain level which is a bummer. I could use smth like that just in case.

Are programs for monitoring/controlling fans easy to find on linux?

Thanks everyone for your replies, good stuff here.

If you can bump up to at least 512 then Ubuntu 9.04 should run fine (depending on your CPU speed). I wouldn't go with 7.04 as it is no longer supported so you won't get any security updates. Maybe try 8.10 or 8.04 (long term support so better option) and then you can upgrade once you get more ram.

no option to shut down? what board and processor do you have?

---

### Post by anchorschmidt on 2009-05-20
Welcome to UBUNTU!! :)

You won't be able to run Ubuntu live cd in 256 mbs of RAM. I've tried it and it just doesn't work.

For me Jaunty takes around 300 megabytes of ram when it starts up. For your case, I recommend using Xubuntu, which is a lighter variant of Ubuntu. Go to xubuntu.com for more info.

---

### Post by lovinglinux on 2009-05-20
> **anchorschmidt said:**
> You won't be able to run Ubuntu live cd in 256 mbs of RAM. I've tried it and it just doesn't work.

Well, I've tried a minute ago and it works. The system monitor was displaying 212.4 Mb of RAM. I guess the rest went to the integrated video card.

I was also able to open Firefox, but didn't bother to test other stuff.

BTW, it was the Jaunty Live CD.

---

### Post by linuxfanboy on 2009-05-23
> **lovinglinux said:**
> Well, I've tried a minute ago and it works. The system monitor was displaying 212.4 Mb of RAM. I guess the rest went to the integrated video card.

I was also able to open Firefox, but didn't bother to test other stuff.

BTW, it was the Jaunty Live CD.

Tried it too, works for me also. Did the tests and everything looked ok, I'm good to go. Guess that means I shouldnt have hardware issues.

It was slow smtimes like opening openoffice...many times it didnt open it and just froze...but its a llive cd and with low ram it cant be perfect.

Will install it once I figure out this issue with the windows recovery partion....will open thread in general help, doesnt belong here imo.

Thanks everyone for the help. :D

---

