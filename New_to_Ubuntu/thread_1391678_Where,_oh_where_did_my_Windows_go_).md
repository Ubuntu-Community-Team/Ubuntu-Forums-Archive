---
title: "Where, oh where did my Windows go? :)"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by gnometorule on 2010-01-27
To culminate 2 weeks of sheer bliss with Ubuntu, I just tried to log over into Windows: and it's gone. :) I still can log into the pretty looking, but now entirely empty screen that formerly occupied the Windows XP part of my laptop. In other words, I can choose OS; get into Ubuntu; when choosing Windows instead, I log into windows, then end up with an empty screen.

I installed this under WUPI (not that I meant to, mind you, see below); if anyone has a reasonable idea how to remedy this fast, that'd neat. I doubt it. Ubuntu is just reaaaaaaallly messed up.

--------------------------
[B]Summary of 2 beautiful weeks back in the dark ages of computing
[/B][I]
The story of a not-so-brave knight with lots of time on his hands fighting windmills[/I]
-------------------------

[I]Prologue:
[/I]
I originally installed Ubuntu just to read a book (Hacking: The Art of Exploitation). The book comes with the no longer supported 7.10. As that system didn't recognize my ethernet/wireless, and, despite some support by a 2 year Ubuntu using friend, and a background of some sort with comps, I failed to remedy this. Along the way, some beautiful, foreboding experiences.

*The challenge*

- before even knowing the deeper ins of Ubuntu (had last used Unix in 2002), the recommended path (per Intel instructions for kerner drivers) includes kernel module modifications, kernel recompilations and such (as you all know). That sounded just svelte for someone who, at that point, was proud to again remember mkdir and cd. So that, surprisingly, didn't work out
- let's try ndiswrapper. Going to intel, i download the drivers. Oups, neither is in a format that ndiswrapper needs.
- Let's try sourceforge. Following the links from the official sourceforge ndiswrapper pages for my wireless card to get windows drivers, I find myself (a) at one blind link, and (b) one of a private person sharing his travel experiences and such. Cool.
- I finally am smart enough to just pick the drivers off my windows drivers folder. Great!
- on to installing ndiswrapper. But wait, i can't. I get build errors. Tsssh.

[I]The resolution...or so it seemed
[/I]
I decide to just install 9.10 for dual boot. 
- Let's get the iso burn and this installed!
- Oups, despite integrity checks of the burn etc, the installation jumps off with an error message
- I find Wupi. Mind you, not that i said great, let's not use the boot disk. I didn't really have an option.
- Wupi works fine...well, until something Wupi related just destroyed my entire Windows XP

*The renewed challenge*

- Takes me a good day to just get yahoo running under Thunderbird. Satisfying when it does
- I try this and that, which usually doesn't work right out of the box. And I decide to be happy to make this just a dumb box doing what I really need instead of wasting a day on each challenge
- I need: Coding platform; internet
- Let's get a nice IDE
- Let's install QT. Damn, it installs, but doesn't work
- Well, what about Eclipse? I install the SDK and plugin (vis synaptic); I follow the instructions for the cdt from their web page; but oups, build error. Doesn't work either.
[I][B]
Summary of 2 weeks time:[/B][/I]

- Lost my windows
- Got the Linux command line
- Got basic internet. Mind you, much less i can do currently in internet than I could in Windows

Seriously, people really caring about Ubuntu. U. doesn't need to argue over whether or not (gasp) GIMP will be on the 10.4 CD rom. If you care about Ubuntu, get it to

- work with reasonable effort
- don't have blind links or pages describing version from 2004 tersely
- and don't destroy other OS you might have on the comp


I realize this is all done by people who want to create and support a community. But the focus on 'what wallpaper' as opposed to 'let's get a version that works almost out of the box, sort of working with 1 day worth of effort, and where you can not only access, but actually install reasonably recent BASIC software.' You're not competing with Windows; you're working with a small group of new and old-school geeks, who, like me, WANT to like this. But they need what I just wrote; not a loooong debate about whether the wallpaper is too brown.

---

### Post by mastablasta on 2010-01-27
So what you say is you tried out the live CD to load the system and everything worked there and when you tried to install it everything got messed up? And you installed it on a separate partition to double boot with WinXP?
 
BTW it is laptops that have more issues with Linux. Desktops usually just work... At least from what i tried with LiveCD.

---

### Post by gnometorule on 2010-01-27
No. After I eventually got Ubuntu via Wupi, i was able to dual boot. I spent 10 something days exclusively on the Ubuntu side, trying in vain mostly to get software to run. When logging back to windows for the first time tonight, it was a blank screen.

---

### Post by Bartender on 2010-01-27
#1:  Just tell us what the problem is.  You lose a lot of people with all the extraneous talking.
#2:  Wubi (not Woopie) isn't all it's cracked up to be.  IMO, wubi may be easier to install, but you end up with more "moving parts".  A true dual-boot may require more research, but the result has fewer moving parts and is more reliable.
#3:  Your frustration is understandable, and it may be therapeutic to vent, but venting does not increase your chances of getting good help.  Write your first post, get all your frustration out, then hit the delete button instead of the Send button.  Start over.
#4:  You backed up your Windows data, right?  You have Windows recovery discs, or a genuine Windows CD, or the entire Windows install imaged to another disk?  Did you adhere to ANY of the disaster recovery methods that have been outlined on these forums about a billion times?
#5:  For the most part, people who carry on about the Ubuntu themes have functional systems.  What does that have to do with your situation?  Focus.
#6:  It's unfortunate that some of the hardware in your rig isn't supported out of the box.  That's one of the reasons for the LiveCD's.  But the best route is to google your exact model.  Unless it's a very rare computer there will be a trail of people posting about problems.

---

