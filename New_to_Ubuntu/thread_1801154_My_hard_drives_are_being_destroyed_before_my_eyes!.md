---
title: "My hard drives are being destroyed before my eyes! One-after-another"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-10
Trying to get these old computers working. Replaced the failed hard drive that was in one of them with what I know to be a good 20 GB drive. I keep running into situations with the software I run to diagnose and get system info and now with a distro I'm trying to install - a situation where I can not get the thing to shut down safely. I end up having no choice (that I know of anyhow) but to hit the power button to shut it down (hard boot it). Next thing I know I'm getting funny noised out of the drive. For the love of God and all that's good! I can't afford this. There must be some way to make it safely shut down when you get a screen there is nothing you can do with - isn't there???

Please help! Wow! I'll have nothing left! At this rate I might as well take all my drives, line them up on the sidewalk and take a hammer to them!!!

:confused:
-----------------

Edit:

I should have mentioned, so far I've tried:

esc, end, ctrl+alt+F1

```
shutdown now
```

```
reboot now
```

```
exit
```

```
stop
```

and a few others.

But it isn't a terminal window I'm looking at. For crying out loud what I wouldn't give for a terminal window right now!

---

### Post by Isaacgallegos on 2011-07-10
If it's just a UI lock up I like to escape to the terminal. 

CTRL+ALT+F1
or
CTRL+ALT+F2
or
CTRL+ALT+F3
or
CTRL+ALT+F4
or
CTRL+ALT+F5
or
CTRL+ALT+F6

Desktop:
CTRL+ALT+F7

Generally this will always be available, even if my desktop locks up. 

Once in the terminal I can:
sudo reboot

or 

sudo killall [application name goes here]
like 
sudo killall inkscape 
or
sudo killall5 which kills your entire session and kicks you out to the login screen.

edit: lol you added your edit as I was writing. Yeah, you got it.

---

### Post by ClientAlive on 2011-07-10
> **Isaacgallegos said:**
> If it's just a UI lock up I like to escape to the terminal. 

CTRL+ALT+F1
or
CTRL+ALT+F2
or
CTRL+ALT+F3
or
CTRL+ALT+F4
or
CTRL+ALT+F5
or
CTRL+ALT+F6

Desktop:
CTRL+ALT+F7

Generally this will always be available, even if my desktop locks up. 

Once in the terminal I can:
sudo reboot

or 

sudo killall [application name goes here]
like 
sudo killall inkscape 
or
sudo killall5 which kills your entire session and kicks you out to the login screen.

edit: lol you added your edit as I was writing. Yeah, you got it.


I'm trying to do a fresh install of Bodhi Linux on a bare, wiped drive. There were only 3 options in the main menu when it loaded and none of them made it obvious they led to "installing" (talking about live or whatever). One option said "boot from hard drive" or something very similar to that. I wasn't sure but I suspected it would do this and try to reboot and boot from that blank drive. Of course, the screen I'm looking at now says:

> 
Booting from local disk . . .
Missing operating system_


Just exactly like that. Of course there's no operating system. How could there be! I dd'ed the disk! I know there isn't!

The thing [Bodhi Linux] isn't even loaded I can't get into a terminal window that doesn't exist yet and nothing I do gets me out of this. I'm just sitting here looking at that screen listening to the machine run. I've hard booted 3 times tonight already and the las time I start getting funny noises out of my disk (hard drive). Anything happening, I mean anything at all, to that drive - is something that simply can-not-happen.

There has to be something I can do! Isn't there? She's not gonna take much more of that. It might be too late already.

---

### Post by ClientAlive on 2011-07-10
I guess there is no answer for this? I have to push the $%&! button again?

Wow!

---

### Post by wildmanne39 on 2011-07-10
> **ClientAlive said:**
> I guess there is no answer for this? I have to push the $%&! button again?

Wow!Hi, have a look at this guide.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by ClientAlive on 2011-07-10
> **wildmanne39 said:**
> Hi, have a look at this guide.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)


Hi,

Thanks. That definitely looks like something to have enabled in one's kernel. In my sitch (with no o/s installed) I don't know if it would have helped me. Maybe I missed it but I don't recall seeing anything in that article about a situation where you don't actually have Linux installed yet.

I would think that the only way to handle something like that is to somehow get back into the bios. I'm not sure if bios has the abilty to "re" boot though. Maybe all it is, is to set the boot order when you're already in the process of booting up. It would be nice if there were some live tool or something you can put on a usb stick. You put the usb in the computer and that gets loaded into memory first and gives you the ability to do all the sysrq things regardless of whether anything is installed yet or not. Then you boot from your cd or whatever to do the install. If anything goes wrong that thing on the usb is loaded up and ready to go - has been since before even attempting an install.

So I had to hard boot the thing two more times. Bodhi Linux never would work for me - just sat there at the splash screen forever. Finally I put Xubuntu minimal in the cd drive and it's installing now. I hope my drive is ok and that the install completes.

Sorry for all the exclamation marks. I was really freaking out. These stupid little old computer parts are all I have and I was hoping to resell a couple of these things cheap. I wouldn't be able to do that though if components start getting killed off and I end up without enough for a functional system.

Ahhh well. You live and learn I guess. Just real frustrating when there isn't a darn thing you can do about it.

---

### Post by wildmanne39 on 2011-07-10
Hi, I could be wrong but I would think if there is no operating system to startup then turning it off with the power button should not cause it to fry a drive, but I am tired I will sleep on it.

---

### Post by ClientAlive on 2011-07-10
> **wildmanne39 said:**
> Hi, I could be wrong but I would think if there is no operating system to startup then turning it off with the power button should not cause it to fry a drive, but I am tired I will sleep on it.


Well that makes sense. I just can't figure out what those sounds are that come from the drive. It didn't do it the first time I fired that thing up after installing the drive. And the sounds it was making are basically identical to the sounds the other bad drives were making before I took them out. Just had me real worried.

](*,)

---

### Post by CatKiller on 2011-07-10
> **ClientAlive said:**
> Well that makes sense. I just can't figure out what those sounds are that come from the drive. It didn't do it the first time I fired that thing up after installing the drive. And the sounds it was making are basically identical to the sounds the other bad drives were making before I took them out. Just had me real worried.

Noises from a hard drive are bad. Especially clicking noises. The hard drive manufacturer probably has a diagnostic tool that you can run on the drive. Hard drive errors are going to lead to all sorts of weirdness.

A bad drive controller can chew its way through hard drives, as can a faulty power supply.

EDIT: So can bad cabling. If the shield is broken on a ribbon cable it can cause the signals to short, which also causes problems.

---

### Post by colin.p on 2011-07-10
I agree. I have had to on occasion, hit the restart button, or even the shut down button, in windows and sometimes in linux, been doing it for 16 years. I have never ever had a problem from doing it. Of course, it isn't something to do all the time, but sometimes, you have no choice.
If you are going through that many drives from doing a hard shut down, then I would think that either the power supply or the mother board is suspect.

---

### Post by LowSky on 2011-07-10
Are you sure it isn't a hardware issue that is really causing the problem? Maybe a voltage regulation problem.

---

### Post by JRV on 2011-07-10
The correct syntax for the shutdown command is:
```
sudo shutdown -h now
```

You can also try to re-start X with <CTRL>-<ALT>-<Backspace> after you enable it.

To enable it System=>Preferences=>Keyboard=>Layouts=>Options=>Key sequence to kill the X server.

---

### Post by bodhi.zazen on 2011-07-10
> **ClientAlive said:**
> In my sitch (with no o/s installed) I don't know if it would have helped me.

It is hard to know based on what you have posted. Were you running a live CD ? If so, then those keys should have worked.

Diagnosing lockups can be very difficult and in general they are most often related to the kernel, video drivers, and rarely wireless drivers.

Fedora maintains a nice set of pages (hint @ Ubuntu wiki) on how to report such bugs, see this page:

[https://fedoraproject.org/wiki/BugsAndFeatureRequests](https://fedoraproject.org/wiki/BugsAndFeatureRequests)

From there are links to pages on the kernel and X (graphical interface).

Some of the information on those pages is Fedora specific, but much of the information is not.

Also be aware , this is a classical read:

[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

I highly suggest that page to everyone.

As you can see, in a nut shell, when describing a problem, a "simple" description such as "it locked up" is of little to no value.

How did you produce the problem ? What were you doing exactly a the time ? What OS ? What kernel ? etc, etc ...

With all that in mind, in general, it seems you have two problems:



1. You could not shut down. This could have been most anything from you did not run the command as root to your system was not responding to your keyboard, to a kernel problem, to a problem with X to a hardware problem.


2. Your hard drive is making noise. Although sub optimal, hitting the power button is unlikely to have caused the problem with your hard drive (but it could mind you). If you did not have a hardware problem before, you do now, and there really is no way to repair a failing hard drive short of replacing it. You can run diagnostics on it, which will confirm what you already know, it is failing, but as there is no way to repair bad sectors, such diagnostics are of limited utility.

A mentor of mine when I was first starting with computers told me, in regards to data backup and hard drives, it is not a matter of if your hard drive will fail, but when and what your plan is in place to restore your data.

No time like the present to review your back up strategy.

---

### Post by no2498 on 2011-07-10
boot from the cd only turn every thing else off
you can install this way

---

### Post by CatKiller on 2011-07-10
My read on the situation breaks it down to two issues too.

The OP has been in situations where he's had to power-cycle the machine. Where he's had an environment running, he's been given instruction on how to more gracefully shut down the system. The one situation that he's actually detailed - he booted with no OS - power-cycling won't have caused any damage because the disc was neither being read nor written to. The heads should have been safely away from the platters.

He also has some as-yet undetermined hardware problem that has affected a currently-unknown number of hard drives. It's possible that the drives just went bad - they have a finite lifespan and are likely to be the first component to go in any system, and these apparently are of a certain age. In which case there's not a lot that can be done, as you say. It's also possible that, as the OP contends, the drives are otherwise fine and there's an external cause leading to drive failure. By identifying and fixing this other hardware cause, the drives might be salvaged. The damaged sectors can be re-mapped and if the heads haven't been damaged by the issue the drives might last another year or two. If there is an external cause, putting a new drive in there will just kill the new drive.

I hate hard drive problems...

---

### Post by ClientAlive on 2011-07-10
Hi guys,

Thanks for showing up for me. It got to be real late where I am and I just couldn't hold my eyes open any longer. I see everyone's post here but I'm not sure that quoting ea post and trying to respond that way is the best way I can respond right now. So I'll make this post and read through the thread in another tab as I go - and do my best to explain.

In general what I see is people saying is that it's more complicated and probably requires more than I realize to work with old hardware like this and get a healthy machine in the end.

It may be a little off topic but I feel I should briefly explain my situation, my working environment, and why it is I assumed that power cycling the machine was the cause.

My situation?

I acquired these machines (now a total of 4) and monitors and other periferals (keyboards, mice, etc) with the intention of reselling them to earn a little extra cash. Also with the intention that any hardware that's compatible with my machine I could use for upgrades. The machines are all so old that they really aren't worth that much even if they are working perfectly. On average these machines are about 10 years old. All of them use old sdram memory (100 MHz) - if that gives you some idea.

My working environment?

I have a couple philips screwdrivers, a flat screwdriver, and an old pair of metal scissors. I also have a few software tools I've been using for various things (recovering data off of drives, running diagnostics, getting system information, etc). Some of those software tools are as follows:

Ultimate Bood CD
Clonezilla
Ubuntu 10.04 LTS (which, of course, can be run live)
Parted Magic
Knoppix
and a couple others that I haven't had the need to make use of so far.

So I get these 4 machines in 2 rounds. Last week I get 3 machines and recover the data off all drives for the guy who gave them do me. He also wants one machine back so there goes one, off to the side, with what I think is a faulty power supply (I have no replacement for it nor do I have the equipment to properly diagnose the problem - but that power supply is my suspicion). So now there's two left from that first round.

Of those two left, one of them had a faulty drive which (1) made all kinds of god aweful "clicking noises" and (2) the diagnostic (one of the tools on Ultimate Boot CD) came back saying it's failing and get your data off it right away. So here, with no experience before starting this last week, here at this point I gain the experience of hearing a faulty drive for the first time. Now, after that, I know what one sounds like and that those sounds are not good. (This was my first experience with that - never heard it before in my life).

Now, yesterday, I get 2 more machines. Both look very nice and well cared for. One fires right up, has Windows XP on it and appears very healthy. I set it to the side to come back to later for data recovery, wiping the disk and reinstalling and preparing for sale. The other (and this is the one in connection with this thread) - I fire it up and I hear these same sounds. I run system information tools on it and the drive does not show up/ not recognized. I run a diagnostic and it comes back as failed. Now I've experienced two machines, two faulty drives, and they both made the same noises. Now this is two drives; but, so far, they are the drives that were in the machines when I got them - they were that way already.

So I take a 20 GB drive out of my goodies box and I swap it for the faulty drive in the second machine (the one I said was in connection with this thread). I fire it up. Everything sounds fine. I boot from CD (in this case "Ultimate Boot CD") so I can get some sys info and other info and I intend to proceed to install some minimal Linux after that. Well, this so called Ultimate Boot CD is, apparently, famous for leaving you with programs that don't tell you anything about how to exit the program and even the main menu does not seem to have an option to just shut down the machine. So I try every command I can think of, every key on the keyboard that I can think of, that might make it shut down the machine. No dice! H\So here, at this point, I find myself in the situation of having to power cycle the machine or just sit there staring at it watching it show me some UBCD menu screen (or in some cases the last screen of the program I had run).

So why did I think that power cycling the machine would fry the drive?

I have a friend who I consider a veritable computer genius. This guy really knows his stuff - big time! I once asked him what happens when you just shut down the machine (power cycle it). And his response was this: He told me you don't want to do that. That it can damage a lot of things but that one of the things that can happen is (and I quote), "it can rip your hard drive a new one."

With that response in mind and having had the experience of hearing a bad drive - after power cycling that machine (the one in connection with this thread) a few times, it began to make those same noises.

The drive that I put in it to replace the bad one it came with had had diagnostics run on it before (when it was plugged into the mobo of my own destktop which is a healthy machine). The diagnostics had come back healthy. The drive never made any funny noises before. Now, after putting it in the other machine and power cycling a few times - funny sounds.

The last thing I did last night was to run an Ubuntu 10.04 minimal install with xfce desktop install (to make for an Xubuntu install). It seems to have been successful. At the end I was able to reboot the machine, take out the CD, got my log in screen, logged in successfully, and got to the desktop environment. I was just too tired to stay awake any longer and fish around in there tweaking things and dialing things in. The drive still makes noises when you boot the computer up though and I can't sell someone junk. Maybe someone else would do that and feel fine with it but I can't and I won't. (So lets take the $ I would have had, I might have had, from the sale of that machine in one hand and our lighters in the other, and lets have ourselves a little burning party - Nice!). I only have so many drives and whatever is causing them to get eaten up I don't have the proper tools or expertise do diagnose it.

So I see what people are saying in their posts. I'm sorry I can't offer a better response than this. I just don't have the vocabulary or expertise to really respond in kind (but I'm working on that).

So, in the final tally, here's what I've gotten out of this so far (not that these things were explicitly said but this is what I got):

* When you work with old hardware you have a lot more to worry about and it takes a lot more work to ensure a healthy machine in the end.
* If you have a machine that starts out with a bad drive, don't just replace the drive with a good one - it'll probably get eaten up too from whatever caused the first one to fail. Diagnose the source of the problem first, fix it, then replace the drive with a good one.
* Don't assume you can get good results with a couple screwdrivers, a pair of scissors and a few pieces of software - it's going to take more than that.
* Don't assume you aren't going to have all kinds of failures and headaches when you first start doing something like this. If you go about learning it in this way (hands on and relatively on your own) your probably going to learn your lessons the hard way.



So, lastly, I should mention that I did notice all the very specific and technical information that was given to me in this thread. I also see the links to information. Based on the tools available to me I can visit the links and learn (my mind is a tool and I do have that still, even after last night  :D ). As far as some of the other things? I'm not sure but I'm assuming there will be some (if they are based on making use of some new knowledge or on software I can acquire for free) that I can do or try; and some that may require actual, physical tools - the ones that cost money - (like a multi tester or some other tools) that I may need to wait to get my hands on.

Thanks for everything you've shared guys - I will check out everything that was shared with me. Thanks Bodhi. Sorry for buggin you last night.

---

### Post by ClientAlive on 2011-07-10
> **LowSky said:**
> Are you sure it isn't a hardware issue that is really causing the problem? Maybe a voltage regulation problem.


I saw your signature - how very apropos.

---

### Post by JRV on 2011-07-24
I am just curious.  What type of motherboard do you have?  
I used to use VIA Mini-ITX boards and I had three drive controller failures.
(I have switched to Intel Atom Mini-ITX boards.)

---

### Post by ClientAlive on 2011-07-24
> **JRV said:**
> I am just curious.  What type of motherboard do you have?  
I used to use VIA Mini-ITX boards and I had three drive controller failures.
(I have switched to Intel Atom Mini-ITX boards.)



Product Specs: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

It's an old Amberine board.

---

