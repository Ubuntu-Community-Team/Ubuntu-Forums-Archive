---
title: "advantages of virtualbox windows over dual boot?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-07-09
I had fulltilt poker working in wine just fine but the latest update cured that completely. I also tried it on two  old windows machines that had been running fulltilt fine and the update messed it up completely on them as well.  I am wondering now if I should try a dual boot with windows xp  and Ubuntu or just go with the virtualbox. I read on the forum that it takes  a lot of ram to run it in virtual box. This machine originally had xp, it has around 700 mb of ram, it ran it fine with the exception of a little lag when I was working in poser.

I have Poser working in wine now, its not perfect but certainly usable, but I'd really like to get fulltilt working for hubby as he enjoys it a lot. So would it be better just to set up a dual boot than go with virtual box?

thanks - all advice is always appreciated.

myst

---

### Post by aysiu on 2009-07-09
700 MB of RAM is too little. You will definitely have to take a performance hit. To run Windows and Linux together (one virtually), I'd recommend a bare minimum of 1 GB of RAM.

---

### Post by DGortze380 on 2009-07-09
> **aysiu said:**
> 700 MB of RAM is too little. You will definitely have to take a performance hit. To run Windows and Linux together (one virtually), I'd recommend a bare minimum of 1 GB of RAM.

I disagree, while 700mb is certainly low it could be made to work with 256mb for Ubuntu and the rest for XP. Of course, this is assuming you only run XP when needed, use only XP when it's running.

Not ideal, but workable IMO.

Now for your original question, The advantage is that you can run both OS's at the same time. The advantage over WINE is that you get a fully functional Windows install. The disadvantages are extra RAM usage, and no 3D Graphics.

This line is what concerns me

> 
I also tried it on two old windows machines that had been running fulltilt fine and the update messed it up completely on them as well.


A Windows Virtual Machine will not fix this ... if it doesn't work on a plain old Windows install, it won't work on a Windows Virtual Machine.

---

### Post by mystmaiden on 2009-07-09
Degortze wrote: A Windows Virtual Machine will not fix this ... if it doesn't work on a plain old Windows install, it won't work on a Windows Virtual Machine.

You may well be right, I just assumed the last update was the cut off for fulltilt to work with windows 98 and was hoping xp would be more compatible.

Does no 3d mean that virtual box couldn't play a movie? I'd wondered if this would solve my can't-use-netflix-play-now feature dilema too.

---

### Post by binbash on 2009-07-09
You can trim Windows XP to 50mb ram with nlite.Then you can run it fine with 700mb ram, otherwise just forget it

---

### Post by mystmaiden on 2009-07-09
binbash wrote: You can trim Windows XP to 50mb ram with nlite.Then you can run it fine with 700mb ram, otherwise just forget it.

Is that because it would be running in virtualbox? Cause I ran it fine for years on its own with less ram even. 

I'd wondered about nlite  too, since one of my biggest objections to all things windows is all the extraneous flotsam they force on you. 

What is needed as far as hard disk space for a dual boot? I have 56 gigs, I think then a terrabyte external. Ubuntu would be my primary os, only a couple of things I'd ever need windows for.

As far as that goes I might be able to slap another stick of ram in there, the biggest problem with that being sony and their itty bitty boxes. The thing is physically crammed full now. 

myst

---

### Post by mystmaiden on 2009-07-10
I got virtualbox running and fulltilt poker does work on it and so does netflix watch instantly. Unfortunately there is no sound. In the control panel it shows no sound devices whatsoever, everything is greyed out so I couldn't change that. No idea how to fix that. Ideas anyone?

So far in this experiment - I'm not liking virtual box at all because of the tiny screen. I tried changing the settings but then the command line is not accessible. I haven't experimented with nlite yet, so it is taking up a lot of hard disk space. IE explorer ran just a bit faster than firefox does for me on ubuntu. I may try to set up a dual boot tomorrow. I had really wanted to stick with Just ubuntu but - hubby works hard to support my computing habit and all the toys I buy to play with in Poser, the least I can do is see he can play the one game he likes. :)

anyone else done a comparison? Your thoughts?

myst

---

### Post by Peter09 on 2009-07-10
To get your screen correct you need to install the guest utilities. They should be part of your virtual box installation setup.

---

### Post by binbash on 2009-07-10
> **mystmaiden said:**
> binbash wrote: You can trim Windows XP to 50mb ram with nlite.Then you can run it fine with 700mb ram, otherwise just forget it.

Is that because it would be running in virtualbox? Cause I ran it fine for years on its own with less ram even. 

I'd wondered about nlite  too, since one of my biggest objections to all things windows is all the extraneous flotsam they force on you. 

What is needed as far as hard disk space for a dual boot? I have 56 gigs, I think then a terrabyte external. Ubuntu would be my primary os, only a couple of things I'd ever need windows for.

As far as that goes I might be able to slap another stick of ram in there, the biggest problem with that being sony and their itty bitty boxes. The thing is physically crammed full now. 

myst

Yes and No.

Why would i install paint(or any other software) or other drivers that i do not have, other languages etc etc ?

---

### Post by DGortze380 on 2009-07-10
> **mystmaiden said:**
> I got virtualbox running and fulltilt poker does work on it and so does netflix watch instantly. Unfortunately there is no sound. In the control panel it shows no sound devices whatsoever, everything is greyed out so I couldn't change that. No idea how to fix that. Ideas anyone?

myst

Two easy fixes. In the setting window for your VM, choose CORE AUDIO and ICH AC97. Sound will work next time you boot the VM.

As for the screen size, google how to install Guest Addition for a Windows Guest on Ubuntu. You'll be able to run full screen with mouse integration.

---

### Post by mystmaiden on 2009-07-10
Thanks much, Degortze! 

well, I've hit a definite snag on the sound, there isn't an option for core audio, and I keep getting an error that either i have no sound on my computer or it is being used by another program. This May be because of the way my speakers are set up. I have an old altec speakers with a subwoofer, they don't make drivers for them anymore but they sound soo good I've hated to get rid of them. I just plug them in and control them with the knob on the speaker itself and its stereo war with the neighbor. (kidding, I wouldn't torture my neighbors - much)

---

### Post by mystmaiden on 2009-07-12
Since my attempt at a dual boot was such a complete wreck I am back to trying to get past my frustrations with virtual box. I'm running Ubuntu 8.04 and apparently there are some issues with installing the guest additions. I can click on the devices/install guest additions all day long and nothing happens.  The guest os is Windows xp and I'm using Virtualbox 3.0

I found one tutorial on line but it sounds as if he has the guest additions on a cd but I've done several google searches but I can not find the link to download the iso  . If anyone can walk me through this or point me to the right place, I'd be really happy.

myst

---

