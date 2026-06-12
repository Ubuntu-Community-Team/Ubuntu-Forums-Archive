---
title: "Ubuntu 8.10 v 8.04"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-21
im new to ubuntu and have just downloaded 8.10 with plans to install dual boot with xp on my desktop in a week or so.  in the mean time, ive been trying to learn about ubuntu, etc.  

ive come across various posts where people say noobs should install 8.04 over 8.10 due to stability or better driver/hardware compatibility and the like.  

so now ive started downloading 8.04....

and then i read some complaining that when they run update manager on 8.04, they dont see the latest software updates and thus cant rely on the repositories and needing to go look for updates directly from software sources.

any recommendations on which one should i install?

---

### Post by novafluxx on 2009-02-21
It really depends on what your using the system for. What will you be doing on the system?

8.10 is a stable release, 8.04.2 is the latest update to 8.04.

If you're just trying to learn Linux for the first time, I'd recommend using 8.10 as its the latest and has the most up-to-date software in its repositories.

Nearly everything you will need/use/want is in the repos for 8.04.2 and 8.10!

8.04.2 won't have the latest and greatest, because its a stable long term support release. No major updates or changes will occur, besides the incrimental 8.04.x updates, and of course you'll always see the latest security updates

---

### Post by 4Orbs on 2009-02-21
If you install 8.04 you'll learn how things work correctly out of the box. Just follow the tutorials on the forum to get it set up peachy-keen.

If you install 8.10 you'll be forced to learn alternate ways of getting your graphics driver working (maybe), and it's a good lesson. I prefer 8.10 to 8.04 even though I currently have to use the nVidia beta driver for my card. My mobile broadband was working immediately, also. But 8.04 is good and solid. Either one will probably make you smile.

I'm betting that once you spend the next two months on 8.10, you will be eager to move up to 9.04 when it releases.

---

### Post by Temposs on 2009-02-21
hi nachos,

So, how the updates work in Ubuntu is that each version has a list of programs that it uses, and the Ubuntu administrators(Canonical Inc.) package up and send out updates just like Microsoft does for Windows. The difference here is that you can install thousands of programs of all kinds on Ubuntu and they will also be updated. That doesn't happen in Windows.

But, each version keeps a certain basic code base, and it won't upgrade programs that require a newer version of code base than it is set up to handle. So, Ubuntu 8.04 uses the Linux kernel 2.6.24, and won't move away from that for its whole existence. Canonical will, however, send out security updates for that version of the kernel if there's a major flaw/vulnerability, so you're covered there. And the other core parts of the system are likewise tested against this version of the kernel and made to be ever more stable through little updates that don't introduce any new features. This has benefits of stability and not confusing users constantly with adding new features and removing old features. 8.04 is what it is, more or less. 

And for a lot of people, those versions work perfectly well, and 8.04 is more stable generally and will be supported for a looong time(until April 2011). 8.10 is less stable and is only supported until April 2010.

Getting 8.10 will get you more recent versions of the kernel and all the other software. Although here too, some versions of certain programs that 8.10 uses are not the most up to date now. They're trying to stabilize 8.10 now, and not introduce new things that could mess things up.

If you really wanted the version of Ubuntu that comes with the hottest stuff off the presses, you go get the latest Alpha version of Ubuntu 9.04. But, that's probably more unstable than you'd want.

So, it's really up to you. One isn't objectively better than the other.

---

### Post by nachos99 on 2009-02-21
thanks for the suggestions.

to answer nova's question of what i'll be doing on the system, i use my computer for both work and personal use, so ill be running the basic office apps, a real estate software for work which im PRAYING will run on wine or something/anything, dreamweaver which ill also have to figure out how to run on ubuntu, along with the basic emailing, internet, watching video, music and simple video editing. as far as software issues, besides the real estate program, im optimistic that i will find solutions/substitutes.  i dont play games on PC these days (maybe ill make an exception for starcraft 2), so im unconcerned about that as far as running them on ubuntu, directX issues, etc.

the biggest concern for now (since i dont know any better) is being able to run multiple monitors using my dated Nvidia Quadro NVS w/128MB on a dated dimension 4600 with pentium 4. i use and need 3 monitors for work.  and i would really like to be able to do all my work on linux (eventually.. soon... i mean now).

so after reading about people apparently really struggling to get 3 or more screens to run on ubuntu (seems people are managing dual monitors however), i started to think i may have a better shot getting that to work on 8.04 than 8.10.

i understand the suggestion for going with the newer version, since it will force me to learn linux faster due to a probable increased need to troubleshoot.  on the other hand, since i am a total noob and am not familiar with the line codes etc (though willing to learn), im a bit concerned about too much of a bumpy transition which may get in the way of work since i plan to install it on my primary system - my desktop. i guess i can always just boot in XP and work using that. i just want to be free from windows ASAP!  maybe it takes time. 

well, this post is getting a little too long...  i guess im leaning towards 8.04 due to my apprehension about setting up 3 monitors.

thanks again for the suggestions and more ideas/answers/suggestions are always welcome.

---

### Post by Mercury_Alpha on 2009-02-21
> **nachos99 said:**
> 
to answer nova's question of what i'll be doing on the system, i use my computer for both work and personal use, so ill be running the basic office apps, a real estate software for work which im PRAYING will run on wine or something/anything, dreamweaver which ill also have to figure out how to run on ubuntu,

I would ordinarily recommend installing Windows in a virtual machine within Ubuntu. But your specs sound a little low for that. It doesn't hurt to try, I guess, but there is the possibility of taking all that time to install Windows, only to find that you can't give the VM enough resources to run decently.

I recommend ditching the "OSE" version of VirtualBox that comes built in and grabbing the Sun xVM version instead. It seems to run with fewer hangups.

It's actually really easy to do. Just grab the [installer package]("http://www.virtualbox.org/wiki/Linux_Downloads") of choice from here, and you can get the documentation from there as well.

Edit: In the long run, it sounds like the determining factor is your amount of RAM. If you have 2GB, then you can grant the VM 1GB pretty easily, and 64MB of video RAM. I run XP in a VM with 512MB pretty smoothly, but I'm not doing anything heavy.

---

### Post by nachos99 on 2009-02-21
thanks for the tips, Mercury Alpha.  

will definitely look into the sun version.

the XP app that i need for work is definitely not heavy duty, so it sounds like it might work.

---

### Post by novafluxx on 2009-02-21
In that case nacho, I'd go with 8.04 for right now :-)

Good luck to you, in any case!

Let us know how it goes and if you need any help

---

### Post by Bendihossan on 2009-02-21
I've had a lot of problems with 8.10 and have since reverted back to 8.04. NetworkManager applet disconnecting on several known secure and fast networks (wired and wireless) requiring a restarting the applet. Also with 8.10 network roaming is enabled and therefore the nm--applet attempts to connect to ANY wireless network without asking which is illegal in the UK (to join a wireless network without the owners explicit permission) and can be a damn nuisance on laptops! Not the same problems with with 8.04 though :)

Hardy Heron is win!

---

