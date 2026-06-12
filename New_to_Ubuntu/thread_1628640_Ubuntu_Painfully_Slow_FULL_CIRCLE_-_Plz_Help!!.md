---
title: "Ubuntu Painfully Slow FULL CIRCLE - Plz Help!!"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Syndacate on 2010-11-22
Hey,

I'm experiencing some problems with Ubuntu, I initially tried Kubuntu just to see if KDE 4.5 sucked as much as the last time I tried it...and I thought it did...but then I loaded up Ubuntu, and I'm in the same boat.  Tried the same thing with 10.10 with Trinity (KDE3.X), same thing.

Kubuntu both KDE 3.X & 4.X, and Ubuntu 10.10 x64 all are having the same exact problem.

**EVERYTHING** is slow to the point of unusability.  Menus have a good solid 1s wait time before any action happens, updates take FOREVER for each one because they're just installing soooooooo slow (downloaded damn near instantly), boot up is horrific, using any program is horrific, pretty much ANYTHING is RIDICULOUSLY slow, completely passed the point of usability.

It's almost as if there's a process using ALL my CPU power 100% of the time - but according to 'top' - there isn't.  Also, this is happening on FRESH installed versions - nothing even installed, everything, complete and utter delay, I have no idea why, haven't turned up anything on google, haven't turned up anything here.

It's not like my system specs are slouching to the point of unusability either...unless ubuntu REALLY went up in resource usage over the last distro release, specs:
- Core I7 Nahalem 920 2.66Ghz OC'ed 3.36Ghz
- 12GB DDR3 Corsair clocked to 1.6Ghz
- 12 1TB WD 7200RPM Caviar blacks
- EVGA Classified BL-141-E760 mobo
- EVGA GTX 260 (with factory OC) gfx card

I can't figure out what's going on but 10.04 works 100% flawlessly, this is like there's 500 uers logged on and they're all brute forcing..

Distro:
- 10.10 Desktop Ed.
- x64
- Nothing but base software (no non-included software) + OEM updates installed

I don't think it's my computer b/c it runs Win7 just fine, as well as Ubuntu 10.04, it's something only with Maverick where things are going REALLY bad (slow response, very slow response).

Any help is greatly appreciated, I have no idea what could be causing this...

---

### Post by karlwbloedorn on 2010-11-22
If you go to a TTY terminal (shift alt f2 should give you one), and login, then run a few commands like:

"ls /etc/"
"cat /proc/cpuinfo"
"apt-cache search ubuntu"

Do they run slow?

---

### Post by yankysunny on 2010-11-22
> **Syndacate said:**
> Hey,

I'm experiencing some problems with Ubuntu, I initially tried Kubuntu just to see if KDE 4.5 sucked as much as the last time I tried it...and I thought it did...but then I loaded up Ubuntu, and I'm in the same boat.  Tried the same thing with 10.10 with Trinity (KDE3.X), same thing.

Kubuntu both KDE 3.X & 4.X, and Ubuntu 10.10 x64 all are having the same exact problem.

**EVERYTHING is slow to the point of unusability.  Menus have a good solid 1s wait time before any action happens, updates take FOREVER for each one because they're just installing soooooooo slow (downloaded damn near instantly), boot up is horrific, using any program is horrific, pretty much ANYTHING is RIDICULOUSLY slow, completely passed the point of usability.**

It's almost as if there's a process using ALL my CPU power 100% of the time - but according to 'top' - there isn't.  Also, this is happening on FRESH installed versions - nothing even installed, everything, complete and utter delay, I have no idea why, haven't turned up anything on google, haven't turned up anything here.

It's not like my system specs are slouching to the point of unusability either...unless ubuntu REALLY went up in resource usage over the last distro release, specs:
- Core I7 Nahalem 920 2.66Ghz OC'ed 3.36Ghz
- 12GB DDR3 Corsair clocked to 1.6Ghz
- 12 1TB WD 7200RPM Caviar blacks
- EVGA Classified BL-141-E760 mobo
- EVGA GTX 260 (with factory OC) gfx card

I can't figure out what's going on but 10.04 works 100% flawlessly, this is like there's 500 uers logged on and they're all brute forcing..

Distro:
- 10.10 Desktop Ed.
- x64
- Nothing but base software (no non-included software) + OEM updates installed

I don't think it's my computer b/c it runs Win7 just fine, as well as Ubuntu 10.04, it's something only with Maverick where things are going REALLY bad (slow response, very slow response).

Any help is greatly appreciated, I have no idea what could be causing this...

I do agree.. The whole GUI thing is getting slow day by day
Bu when I tried more apps on server , then its fine. I think GUI is to blame

---

### Post by Syndacate on 2010-11-22
No, all of those run quite fast.

Actually, quite weirdly, on this last re-boot, everything appeared to be running at normal speed, switched to a terminal (ctrl + alt + # btw), typed stuff, no problem, went back to the GUI, no problem.

I figured "Maybe I'm losing it" - clicked mouse properties, no problem, clicked somethign else, no problem, then clicked firefox...and all went bad.

The animation of clicking the FF icon took 5s to go away, and the program took 20 seconds to open up.  Once it opened the internet was OK, which is weird b/c here, on campus, it's blazingly fast.  

Then I started clicking on other apps in the window, first one I clicked on, computer janitor, took a good solid 7s to open, menus are laggy to open, etc. etc., changing the view (name vs size) takes 10s, even though it doesn't have anything to list, etc.  Back to square one.

I **DON'T** think this is a problem with FF, though, as this is the first time I've run FF on this install, I simply think FF triggered the issue this time..not sure why, though.

Now I go back to the TTY terminal (which takes forever to switch to, btw)...and the programs still are quick, but there's extra line breaks for some reason, like after I hit "enter" I get prompted 2x or 3x.

What's even weirder, pressing num lock gives about a 3s delay before the light coming on.  I'm not sure how Linux handles echo'ing interrupts but I'm assuming it's like any OS and has to echo the command back to turn the light on, indicating servere lag in the USB driver or interrupt handler thread in the kernel.

I'm going to try a different keyboard, as weird as that sounds..

PS:
'ls' and 'cat' are very light programs that are optimized to hell, and the cache query is just a bunch of downloads and output interrupts, nothing severely resource intensive there, though just because I can't see the difference, doesn't mean there isn't one.

---

### Post by Syndacate on 2010-11-22
> **yankysunny said:**
> I do agree.. The whole GUI thing is getting slow day by day
Bu when I tried more apps on server , then its fine. I think GUI is to blame

No, this is beyond that, man.  This is more than just the standard canonical super-bloating.  It's to the point where it takes 2 or 3s for keyboard interrupts to get back to the keyboard.

Right now it's so slow that the cursor isn't even flashing in the prompt (well it appears and re-appears once every 30s or so, so it's pseud-flashing), and caps lock interrupt doesn't even get returned to the keyboard nor do any any of the key presses go through.  Nor does the mouse move...1 minute later the mouse is moving again..typed a few letters in the "run application" dialog...though I hit "cancel" and it froze up again.

This is way beyond "slower by the day" - today is the FIRST day for this install :(

EDIT:
Now the behavior is getting weirder, all of a sudden the GUI comes alive, everything is regularly responsive, open a terminal and run 'top', system tanks, everything dies.  Still says 0.0% CPU usage though when it finally did load, though...and as I (or anybody else) figured, replacing the keyboard didn't do anything :-P.

---

### Post by yankysunny on 2010-11-22
check out for some background processes? may be they r making u crazy

---

### Post by karlwbloedorn on 2010-11-22
Well, its harder to diagnose the problem now that the issue is intermittent. However, I immediately jump to the conclusion that something with graphics is causing this problem.

Which video driver are you using? I noticed you have an Nvidia card (most common choices are the nvidia proprietary driver and the open source nouveau driver (did I really spell that right without looking it up?). 

You can also try changing the amount of visual effects used in the desktop to see if that alleviates the issue. Right click the desktop and click Change Desktop Background. Then go to the "Visual Effects" tab, select the "None" option.

Does the lag ONLY occur when using the graphical?

---

### Post by Syndacate on 2010-11-22
According to top the processes are in check, I do believe it displays background processes as well.  Either way, is there any processes that are known to create massive (12GB worth) memory leaks within 30s of bootup which come packaged with ubuntu?

---

### Post by karlwbloedorn on 2010-11-22
The reason I think its a graphics problem is when KDE decided to get all plasma'like and change up the way things work; certain graphics cards decided that they didn't want to do anything fast. The main issue that occurred was lack of responsiveness.

I don't know of any massive memory leaking problems that come with ubuntu, but I know one program that can really mess up a system:

#include stuff needed
int main(){
    while(malloc(512)){
       fork();
    }
}

---

### Post by Syndacate on 2010-11-22
> **karlwbloedorn said:**
> Well, its harder to diagnose the problem now that the issue is intermittent. However, I immediately jump to the conclusion that something with graphics is causing this problem.

It's not really intermittent, more-like it's dipping in and out, showing itself in the GUI or showing itself in keyboard response, or mouse response, etc.  There's no long term usage where it's absent, longest it went was like 30s after a fresh boot, that was all.  After this boot it was immediately fried.

I thought that graphics could be causing the problem, too, but I've never had issues with nvidia's drivers.

I don't think you can think of this issue as intermittent, is all I'm saying.  It's really not, just shifting the way it shows itself.

> **karlwbloedorn said:**
> Which video driver are you using? I noticed you have an Nvidia card (most common choices are the nvidia proprietary driver and the open source nouveau driver (did I really spell that right without looking it up?). 

Using Nvidia's proprietary drivers packaged with Ubuntu (whatever "current version" is), never even heard of an issue with them before, it's not ATI under Linux :-P

> **karlwbloedorn said:**
> You can also try changing the amount of visual effects used in the desktop to see if that alleviates the issue. Right click the desktop and click Change Desktop Background. Then go to the "Visual Effects" tab, select the "None" option.

Even though that's never been a problem in the past for my gfx card (and shouldn't, with a GTX 285, it runs GTA IV and crisis at pretty decent gfx), I turned it off.  Nothing changed after a reboot, same constant lag, everywhere.

> **karlwbloedorn said:**
> Does the lag ONLY occur when using the graphical?

It's really hard to tell, as the issues are typically seen in feedback received from the GUI (ie. a button not unclicking)...I would blame GTK but QT in KDE is doing it too (unlikely, regardless of how stable it is), it could be X...but I've never seen an issue like this with X...

---

### Post by Syndacate on 2010-11-22
> **karlwbloedorn said:**
> The reason I think its a graphics problem is when KDE decided to get all plasma'like and change up the way things work; certain graphics cards decided that they didn't want to do anything fast. The main issue that occurred was lack of responsiveness.

I don't know of any massive memory leaking problems that come with ubuntu, but I know one program that can really mess up a system:

#include stuff needed
int main(){
    while(malloc(512)){
       fork();
    }
}

Yeah, I know how to fork bomb in C...though I didn't write a fork bomb in C.

Also, this is currently happening on my Ubuntu install, and also happend on KDE 3.X where plasma was absent..

PS:  It makes more since to do a while(1) - it'll fork faster, who cares how much memory is used on the heap if the CPU can't touch any of it?

---

### Post by karlwbloedorn on 2010-11-22
> **Syndacate said:**
> Yeah, I know how to fork bomb in C...though I didn't write a fork bomb in C.

Also, this is currently happening on my Ubuntu install, and also happend on KDE 3.X where plasma was absent..

PS:  It makes more since to do a while(1) - it'll fork faster, who cares how much memory is used on the heap if the CPU can't touch any of it?
It lags more if you do the malloc because its running out of memory at the same time. :)

In response to your updates, I would try disabling the nvidia driver temporarily and using vesa or nouveau and see if the same problem occurs.

---

### Post by Syndacate on 2010-11-23
> **karlwbloedorn said:**
> It lags more if you do the malloc because its running out of memory at the same time. :)

Takes a hell of a lot more time if you allocate memory each time to fork, malloc is an expensive command (relatively speaking) which doesn't do anything about the goal...if a fork bomb is used as a DOS attack on the CPU than nobody really cares about memory usage, and vice versa if it's attacking RAM.  Recursive spawning using fork will go probably 2-3x as quickly due to it being an exponential time usage, while the CPU is bogged to hell.  The only thing side-attacking RAM will do is make the processor have more PF's...which aren't nearly as detrimental as the amount of children processes which could have forked in that time.

I'd be really surprised if a fork bomb using malloc took down a system as quickly as one which used a constant.  Completely off topic, though, I didn't write a fork bomb, and I doubt Ubuntu included one...unless maybe if you count KDE4 ;), but that's not on this install.

> **karlwbloedorn said:**
> In response to your updates, I would try disabling the nvidia driver temporarily and using vesa or nouveau and see if the same problem occurs.

Alright, I'll try another driver for gfx

EDIT:  I don't think it's the gfx driver because the proprietary one took fOREVER to install (and it generally installs pretty quick) which means the issue was already rearing its head at that point.

---

### Post by Syndacate on 2010-11-23
Took out the nvidia proprietary drivers, no effect.  System is still completely unusable.  Took 5m just to get from GRUB to the login screen.

---

### Post by karlwbloedorn on 2010-11-23
Well, if thats the case, then I guess the next thing that could be causing an issue would be the CPU. You mentioned it was overclocked, could you try _not_ overclocking it for a bit? Try it both with Hyperthreading enabled and disabled. Let me know if either of those changes do anything.


> **Syndacate said:**
> Takes a hell of a lot more time if you allocate memory each time to fork, malloc is an expensive command (relatively speaking) which doesn't do anything about the goal...if a fork bomb is used as a DOS attack on the CPU than nobody really cares about memory usage, and vice versa if it's attacking RAM.  Recursive spawning using fork will go probably 2-3x as quickly due to it being an exponential time usage, while the CPU is bogged to hell.  The only thing side-attacking RAM will do is make the processor have more PF's...which aren't nearly as detrimental as the amount of children processes which could have forked in that time.


Running the standard "while(fork())" on my system doesn't cause it to lag out. I can still use the computer at this point. However when running "while(malloc(512)) fork();", my computer becomes unresponsive within 1 second and I am forced to manually reboot as even switching to another TTY doesn't work.

Try it sometime if you're bored (well after you fix this lag problem)

---

### Post by Syndacate on 2010-11-23
> **karlwbloedorn said:**
> Well, if thats the case, then I guess the next thing that could be causing an issue would be the CPU. You mentioned it was overclocked, could you try _not_ overclocking it for a bit? Try it both with Hyperthreading enabled and disabled. Let me know if either of those changes do anything.

If this kernel is that poorly written that I need to downclock my CPU to use it, I rather not use it.  I doubt that has any effect, regardless, if written correctly the kernel shouldn't even know the CPU speed short of processor info instructions.  It works perfectly fine in 10.04, Windows 7, and god knows how many other linux distros I've tested on here since I've OC'ed.  Now it *could* be a problem with the 64 bit I suppose, I haven't tested the 32 bit version of 10.10 yet, but I'm going out of town tomorrow until Friday so I won't be able to re-install until then.

> **karlwbloedorn said:**
> Running the standard "while(fork())" on my system doesn't cause it to lag out. I can still use the computer at this point. However when running "while(malloc(512)) fork();", my computer becomes unresponsive within 1 second and I am forced to manually reboot as even switching to another TTY doesn't work.

Yeah, unfortunately it's real hard to time a fork bomb, it's very system and compiler dependent.

> **karlwbloedorn said:**
> Try it sometime if you're bored (well after you fix this lag problem)

I have, I'll try it with malloc sometime, though I really see no reason ram usage would create a processor DOS attack.  Maybe if you don't have enough ram and it has to start page faulting almost immediately I could see it being an issue, but for a server with lots of RAM, most likely not.

I suppose in the end everything is system, compiler, and hardware specific.

---

### Post by karlwbloedorn on 2010-11-23
> **Syndacate said:**
> If this kernel is that poorly written that I need to downclock my CPU to use it, I rather not use it.


When you over clock a CPU you are limiting the amount of time per cycle and taking whatever the CPU has for a result as the answer, even though it might have changed if you gave it a little bit more time (due to propagation delay of gates in the pipeline)

Now, if you are running into an issue where particular instructions are running out of time at your current speed, it should totally mess everything up. But either the results are being ignored and recalculated, or this isn't the problem.

Even if its unlikely to be the problem, you should at least give it a try because it is just one part that is running outside of the range intel binned your particular chip at. (It is not that hard to reboot and change your clock speed)

Just because it works in other distributions or operating systems doesn't mean it will work in all operating systems. It really just depends on if the instructions that cause problems are executed or not.

---

### Post by Syndacate on 2010-11-23
> **karlwbloedorn said:**
> When you over clock a CPU you are limiting the amount of time per cycle and taking whatever the CPU has for a result as the answer, even though it might have changed if you gave it a little bit more time (due to propagation delay of gates in the pipeline)

While what you said is true at some point, I am quite confident that I haven't overclocked the CPU to the point where there the individual x86 instructions cannot execute.  People run these things at 4+ all day long without issue.

> **karlwbloedorn said:**
> Now, if you are running into an issue where particular instructions are running out of time at your current speed, it should totally mess everything up. But either the results are being ignored and recalculated, or this isn't the problem.

Normally I'd agree with the possibility knowing how a CPU works well enough..but also having used this processor before at this speed for quite some time, knowing others using this exact processor at well over what I'm running, plus knowing x86 assembly pretty damn decently enough, I'm confident that isn't the problem.

After things are compiled, they would NOT be recalculated, if the result was incorrect after a fetch execute cycle, it will keep on going provided the instruction pointer is in a valid program space given the current context.  That being said, theoretically it is possible that gates are in an indeterminate state because of OC'ing, happens all the time when people heavy over clock...  Regardless, knowing much how assemblers work, there is only a handful of the ISA that GCC will compile to - I don't really believe that there's something special in this version that's causing GCC to write some obscene instruction combination that is tweaking my processor out just the right way causing it to give indeterminant results.  That just sound crazy - the odds.

> **karlwbloedorn said:**
> Even if its unlikely to be the problem, you should at least give it a try because it is just one part that is running outside of the range intel binned your particular chip at. (It is not that hard to reboot and change your clock speed)

It just took me awhile to set everything up and I don't remember what I changed, it was over a year ago.  Though I suppose at some point if nobody can give me any realistic ideas I'll have to do that, just as a sanity check if nothing else.

> **karlwbloedorn said:**
> Just because it works in other distributions or operating systems doesn't mean it will work in all operating systems. It really just depends on if the instructions that cause problems are executed or not.

True, but generally everything is compiled with GCC, and GCC generally doesn't deviate, it's decently predictable - it's just a symbol matcher.

------

Anybody have any other ideas (software side)?

---

### Post by admiralspark on 2010-11-23
Well, since nothing else seems to work, and you mentioned that triggering firefox set it off once, could the problem potentially be Java? I've had ubuntu lock up on me before because Java didn't want to execute right, though this is pretty far out on a limb. Does booting into a terminal (runlevel.....3?) still lag? Have you had to reconfigure your xorg.conf file? Was there anything wrong with 10.04 that made you want to upgrade to 10.10? Cause if it worked before....

---

### Post by Syndacate on 2010-12-02
> **admiralspark said:**
> Well, since nothing else seems to work, and you mentioned that triggering firefox set it off once, could the problem potentially be Java? I've had ubuntu lock up on me before because Java didn't want to execute right, though this is pretty far out on a limb. Does booting into a terminal (runlevel.....3?) still lag? Have you had to reconfigure your xorg.conf file? Was there anything wrong with 10.04 that made you want to upgrade to 10.10? Cause if it worked before....

I doubt it's a problem with Java as sometimes it would just finish booting and be damn near unusable from the start.  Nothing I know of in the default program list relies on Java.

It's hard to tell if it's lagging in a terminal, you have to think about how much more expensive GUI operations are for a full fledged DE compared to being restricted to the simple calculative/storage/system operations most commonly used in command line only programs.  They don't need to have window listeners or layout managers, or calculate estimated guesses for widget locations within a panel or frame based on size and way it was expanded.  So what do you compare it to?  I suppose you can try to match up timings of "ls" of the same directory on the same computer with the same linux kernel, same version of the ls program, but you still won't have definitive results.  When it all happens damn near instantly (or too fast to see),  hard to say whether it's laggy or not.

I have not touched my xorg.conf file.

Nothing made me upgrade to 10.10 - this is a fresh install, not an upgrade.  Reason why I'm using 10.10?  None.  I said randomly "*I'm going to format/install 10.10 today*" - and did.  Had nothing but problems :(.

This almost has to be a problem with either
A)  Latest drivers from Nvidia (although switching to NV or Vesa or whatever the default is when I disabled them didn't fix the issue)
B)  There's something different about this kernel which doesn't like my system configuration

I Mean if you think about it there's not much else, tested on both KDE4, KDE3, and Gnome, so you have different tools, different tool kits, different desktop environments for stuff to run in, the only constant stuff is the tool-chain, kernel, peripheral drivers, etc.  Does anybody know of any serious changes to the linux kernel between whatever they used in .04 and now (I think it's .35 or .36)?  This is a stupid problem to have :(  I never thought Ubuntu would give me this much crap, never had any major problems with it..

---

### Post by NCLI on 2010-12-02
Could you post the output of this command?
```
ps -ef
```

---

### Post by kaldor on 2010-12-02
I fixed this exact problem once before by removing the package *ubuntu-one* with apt-get. I replicated that on two machines and it somehow worked on both.

Everything was intensely slow, laggy, etc as you describe. All fixed after ubuntu-one was removed.

---

### Post by NightwishFan on 2010-12-02
If all else fails try adding this PPA to get newer Nvidia drivers.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Syndacate on 2010-12-12
Alright, so here's what happened.

I needed Ubuntu, so I installed 10.04 (which didn't have the problem).  Eventually, I saw the solution to try and remove the ubuntu-one package, and decided that seemed feasible.

So I partition off some space (this is about 1 week ago, right after kaldor posted what he did), so I did, installed Ubuntu on that...**LAGGY AS HELL**, so I do all the updates, take a nap while it's updating.  Come back, restart, computer starts back up.

To verify that there was an issue, I needed to confirm the lag before I removed the ubuntu-one package...but I couldn't.  After the update, I COULD NOT replicate the lag, I used it for a couple of days straight, no issues in the slightest.  I most definitely did lag, though, just opening up the update-manager.

My guess:  There was a patch to some package that was causing it which got fixed in between the time I posted this thread, and the last time I installed it.

I tried looking for ubuntu-one's update history, but couldn't find anything.

Either way, since all the other times it lagged even after I updated, and the way it lagged before I updated last time, there's something in later updates that fixed the issue.  Any ideas?  Anybody know how I can get the ubuntu-one change log?

---

### Post by zbee on 2010-12-30
Hi all,  I found one main reason for Ubuntu 10.10 painfully slow GUI: **Ambiance Theme's 'controls'.**
(in particularly menu scrolling)

Under System->Preference->Appearance:
Select a different theme or 'customize' and change Ambiance Theme's 'controls' to other.
'Squarish' design controls such as Xfce themes are fast, though curve designs like Qtcurve, Dust, are just fine too.

>>>>> It must be a bug for Ambiance theme. Ubuntu team, please note this <<<<<<<<<
Test: try System->Preference->scroll, Nautilus top menu-scroll And folders-open/close

As for general slowness when system is under load, i read somewhere that kernal 2.6.37 shall includes an important patch for snappier UI responsiveness under heavy load.

[http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1)

Other than these, Ubuntu still lags behind windows for UI responsiveness.
These I  believe is due to the design of Xwindows, GTK, Gnome/Metacity.
Gotta wait for Xwindows to be replaced by Wayland or tryout FBDirect or something. (anyone tried before?) :p

---

### Post by zbee on 2010-12-31
I realise ubuntu default ambiance theme (and a few others) had been reported as bug.
This is disastrous, i cant believe Ubuntu allow Ambiance theme to be approved and released as default.

Is the quality approval process even in place?!?

---

### Post by Syndacate on 2011-01-18
It must have not been happening to everybody or it wouldn't have really gone unnoticed.

I'll try that next time I do a *buntu install, but I experienced the same thing in KDE3.X (if you want to really see QA fail look at KDE 4.X) (Trinity) Ubuntu 10.10.  As soon as I was fully updated the lag went away.  I'm assuming it's an issue with my system that set it off, or I doubt it would have been released.

---

### Post by Syndacate on 2011-01-27
> **kaldor said:**
> I fixed this exact problem once before by removing the package *ubuntu-one* with apt-get. I replicated that on two machines and it somehow worked on both.

Everything was intensely slow, laggy, etc as you describe. All fixed after ubuntu-one was removed.

Well I can say with definite uncertainty that it is NOT the ubuntu-one package.

I'm trying Linux Mint - which is based off of Ubuntu Linux (not the Debian one).  It follows the same release pattern in line with Ubuntu.

Same problem, it's absolutely horrific.  This type of random **** makes me want to close the door on Linux and never look back..  EVERYTHING is laggy - it is NOT a driver issue (at least not a video driver issue).  Whatever the hell the problem was, it was fixed in one of the updates to Ubuntu (updated like 3 weeks after the initial install and bam, everything was fixed) but I have no idea what it was!!

Does anybody have any idea what causes MASSIVE amounts of lag in the early 10.10 release.  This is NOT a CPU usage issue, top reports < 1%  I don't have a slow computer either.  I'm using the proprietary Nvidia drivers.

Does anybody know about any MAJOR lag issues that existed in the initial 10.10 release, but were fixed soon after, and what it was?  I can't find the fix, anywhere - find lots of issues with windowing system lag, but I don't believe this is that - like, the cursor when I type in a terminal is laggy!

Anybody??????  This is the most annoying bug, EVER.  It renders the OS completely useless.

---

### Post by Syndacate on 2011-01-27
> **NCLI said:**
> Could you post the output of this command?
```
ps -ef
```

As for what processes are running:

```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 19:10 ?        00:00:07 /sbin/init
root         2     0  0 19:10 ?        00:00:00 [kthreadd]
root         3     2  0 19:10 ?        00:00:01 [ksoftirqd/0]
root         4     2  0 19:10 ?        00:00:00 [migration/0]
root         5     2  0 19:10 ?        00:00:00 [watchdog/0]
root         6     2  0 19:10 ?        00:00:00 [migration/1]
root         7     2  0 19:10 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 19:10 ?        00:00:00 [watchdog/1]
root         9     2  0 19:10 ?        00:00:00 [migration/2]
root        10     2  0 19:10 ?        00:00:00 [ksoftirqd/2]
root        11     2  0 19:10 ?        00:00:00 [watchdog/2]
root        12     2  0 19:10 ?        00:00:00 [migration/3]
root        13     2  0 19:10 ?        00:00:02 [ksoftirqd/3]
root        14     2  0 19:10 ?        00:00:00 [watchdog/3]
root        15     2  0 19:10 ?        00:00:00 [migration/4]
root        16     2  0 19:10 ?        00:00:00 [ksoftirqd/4]
root        17     2  0 19:10 ?        00:00:00 [watchdog/4]
root        18     2  0 19:10 ?        00:00:00 [migration/5]
root        19     2  0 19:10 ?        00:00:00 [ksoftirqd/5]
root        20     2  0 19:10 ?        00:00:00 [watchdog/5]
root        21     2  0 19:10 ?        00:00:00 [migration/6]
root        22     2  0 19:10 ?        00:00:00 [ksoftirqd/6]
root        23     2  0 19:10 ?        00:00:00 [watchdog/6]
root        24     2  0 19:10 ?        00:00:00 [migration/7]
root        25     2  0 19:10 ?        00:00:00 [ksoftirqd/7]
root        26     2  0 19:10 ?        00:00:00 [watchdog/7]
root        27     2  0 19:10 ?        00:00:00 [events/0]
root        28     2  0 19:10 ?        00:00:00 [events/1]
root        29     2  0 19:10 ?        00:00:00 [events/2]
root        30     2  0 19:10 ?        00:00:00 [events/3]
root        31     2  0 19:10 ?        00:00:00 [events/4]
root        32     2  0 19:10 ?        00:00:00 [events/5]
root        33     2  0 19:10 ?        00:00:00 [events/6]
root        34     2  0 19:10 ?        00:00:00 [events/7]
root        35     2  0 19:10 ?        00:00:00 [cpuset]
root        36     2  0 19:10 ?        00:00:00 [khelper]
root        37     2  0 19:10 ?        00:00:00 [netns]
root        38     2  0 19:10 ?        00:00:00 [async/mgr]
root        39     2  0 19:10 ?        00:00:00 [pm]
root        41     2  0 19:10 ?        00:00:00 [sync_supers]
root        42     2  0 19:10 ?        00:00:00 [bdi-default]
root        43     2  0 19:10 ?        00:00:00 [kintegrityd/0]
root        44     2  0 19:10 ?        00:00:00 [kintegrityd/1]
root        45     2  0 19:10 ?        00:00:00 [kintegrityd/2]
root        46     2  0 19:10 ?        00:00:00 [kintegrityd/3]
root        47     2  0 19:10 ?        00:00:00 [kintegrityd/4]
root        48     2  0 19:10 ?        00:00:00 [kintegrityd/5]
root        49     2  0 19:10 ?        00:00:00 [kintegrityd/6]
root        50     2  0 19:10 ?        00:00:00 [kintegrityd/7]
root        51     2  0 19:10 ?        00:00:00 [kblockd/0]
root        52     2  0 19:10 ?        00:00:00 [kblockd/1]
root        53     2  0 19:10 ?        00:00:00 [kblockd/2]
root        54     2  0 19:10 ?        00:00:00 [kblockd/3]
root        55     2  0 19:10 ?        00:00:00 [kblockd/4]
root        56     2  0 19:10 ?        00:00:00 [kblockd/5]
root        57     2  0 19:10 ?        00:00:00 [kblockd/6]
root        58     2  0 19:10 ?        00:00:00 [kblockd/7]
root        59     2  0 19:10 ?        00:00:00 [kacpid]
root        60     2  0 19:10 ?        00:00:00 [kacpi_notify]
root        61     2  0 19:10 ?        00:00:00 [kacpi_hotplug]
root        62     2  0 19:10 ?        00:00:00 [ata_aux]
root        63     2  0 19:10 ?        00:00:00 [ata_sff/0]
root        64     2  0 19:10 ?        00:00:00 [ata_sff/1]
root        65     2  0 19:10 ?        00:00:00 [ata_sff/2]
root        66     2  0 19:10 ?        00:00:00 [ata_sff/3]
root        67     2  0 19:10 ?        00:00:00 [ata_sff/4]
root        68     2  0 19:10 ?        00:00:00 [ata_sff/5]
root        69     2  0 19:10 ?        00:00:00 [ata_sff/6]
root        70     2  0 19:10 ?        00:00:00 [ata_sff/7]
root        71     2  0 19:10 ?        00:00:00 [khubd]
root        72     2  0 19:10 ?        00:00:00 [kseriod]
root        73     2  0 19:10 ?        00:00:00 [kmmcd]
root        74     2  0 19:10 ?        00:00:00 [khungtaskd]
root        75     2  0 19:10 ?        00:00:00 [kswapd0]
root        76     2  0 19:10 ?        00:00:00 [ksmd]
root        77     2  0 19:10 ?        00:00:00 [aio/0]
root        78     2  0 19:10 ?        00:00:00 [aio/1]
root        79     2  0 19:10 ?        00:00:00 [aio/2]
root        80     2  0 19:10 ?        00:00:00 [aio/3]
root        81     2  0 19:10 ?        00:00:00 [aio/4]
root        82     2  0 19:10 ?        00:00:00 [aio/5]
root        83     2  0 19:10 ?        00:00:00 [aio/6]
root        84     2  0 19:10 ?        00:00:00 [aio/7]
root        85     2  0 19:10 ?        00:00:00 [ecryptfs-kthrea]
root        86     2  0 19:10 ?        00:00:00 [crypto/0]
root        87     2  0 19:10 ?        00:00:00 [crypto/1]
root        88     2  0 19:10 ?        00:00:00 [crypto/2]
root        89     2  0 19:10 ?        00:00:00 [crypto/3]
root        90     2  0 19:10 ?        00:00:00 [crypto/4]
root        91     2  0 19:10 ?        00:00:00 [crypto/5]
root        92     2  0 19:10 ?        00:00:00 [crypto/6]
root        93     2  0 19:10 ?        00:00:00 [crypto/7]
root        98     2  0 19:10 ?        00:00:00 [kstriped]
root        99     2  0 19:10 ?        00:00:00 [kmpathd/0]
root       100     2  0 19:10 ?        00:00:00 [kmpathd/1]
root       101     2  0 19:10 ?        00:00:00 [kmpathd/2]
root       102     2  0 19:10 ?        00:00:00 [kmpathd/3]
root       103     2  0 19:10 ?        00:00:00 [kmpathd/4]
root       104     2  0 19:10 ?        00:00:00 [kmpathd/5]
root       105     2  0 19:10 ?        00:00:00 [kmpathd/6]
root       106     2  0 19:10 ?        00:00:00 [kmpathd/7]
root       107     2  0 19:10 ?        00:00:00 [kmpath_handlerd]
root       108     2  0 19:10 ?        00:00:00 [ksnapd]
root       109     2  0 19:10 ?        00:00:00 [kondemand/0]
root       110     2  0 19:10 ?        00:00:00 [kondemand/1]
root       111     2  0 19:10 ?        00:00:00 [kondemand/2]
root       112     2  0 19:10 ?        00:00:00 [kondemand/3]
root       113     2  0 19:10 ?        00:00:00 [kondemand/4]
root       114     2  0 19:10 ?        00:00:00 [kondemand/5]
root       115     2  0 19:10 ?        00:00:00 [kondemand/6]
root       116     2  0 19:10 ?        00:00:00 [kondemand/7]
root       117     2  0 19:10 ?        00:00:00 [kconservative/0]
root       118     2  0 19:10 ?        00:00:00 [kconservative/1]
root       119     2  0 19:10 ?        00:00:00 [kconservative/2]
root       120     2  0 19:10 ?        00:00:00 [kconservative/3]
root       121     2  0 19:10 ?        00:00:00 [kconservative/4]
root       122     2  0 19:10 ?        00:00:00 [kconservative/5]
root       123     2  0 19:10 ?        00:00:00 [kconservative/6]
root       124     2  0 19:10 ?        00:00:00 [kconservative/7]
root       329     2  0 19:10 ?        00:00:00 [scsi_eh_0]
root       332     2  0 19:10 ?        00:00:00 [scsi_eh_1]
root       338     2  0 19:10 ?        00:00:00 [scsi_eh_2]
root       341     2  0 19:10 ?        00:00:00 [scsi_eh_3]
root       357     2  0 19:10 ?        00:00:00 [scsi_eh_4]
root       358     2  0 19:10 ?        00:00:00 [scsi_eh_5]
root       359     2  0 19:10 ?        00:00:00 [scsi_eh_6]
root       360     2  0 19:10 ?        00:00:00 [scsi_eh_7]
root       361     2  0 19:10 ?        00:00:00 [scsi_eh_8]
root       362     2  0 19:10 ?        00:00:00 [scsi_eh_9]
root       369     2  0 19:10 ?        00:00:00 [scsi_eh_10]
root       370     2  0 19:10 ?        00:00:00 [scsi_eh_11]
root       373     2  0 19:10 ?        00:00:00 [scsi_eh_12]
root       374     2  0 19:10 ?        00:00:00 [scsi_eh_13]
root       391     2  0 19:10 ?        00:00:00 [usbhid_resumer]
root       435     2  0 19:10 ?        00:00:00 [flush-8:0]
root       511     2  0 19:10 ?        00:00:00 [jbd2/sda3-8]
root       512     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       513     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       514     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       515     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       516     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       517     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       518     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       519     2  0 19:10 ?        00:00:00 [ext4-dio-unwrit]
root       571     1  0 19:10 ?        00:00:00 upstart-udev-bridge --daemon
root       575     1  0 19:10 ?        00:00:00 udevd --daemon
root       720     2  0 19:10 ?        00:00:00 [edac-poller]
root       810     2  0 19:10 ?        00:00:00 [kpsmoused]
root       990     2  0 19:10 ?        00:00:00 [hd-audio0]
root      1101     1  0 19:10 ?        00:00:00 smbd -F
syslog    1109     1  0 19:10 ?        00:00:00 rsyslogd -c4
root      1124  1101  0 19:10 ?        00:00:00 smbd -F
102       1132     1  0 19:10 ?        00:00:00 dbus-daemon --system --fork
avahi     1141     1  0 19:10 ?        00:00:00 avahi-daemon: running [Syndacate
avahi     1142  1141  0 19:10 ?        00:00:00 avahi-daemon: chroot helper
root      1143     1  0 19:10 ?        00:00:00 NetworkManager
root      1145     1  0 19:10 ?        00:00:00 /usr/sbin/modem-manager
root      1155     1  0 19:10 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      1156  1143  0 19:10 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/N
root      1322     1  0 19:10 ?        00:00:00 nmbd -D
root      1344     1  0 19:10 ?        00:00:00 gdm-binary
root      1366     1  0 19:10 ?        00:00:00 /usr/sbin/console-kit-daemon --n
root      1444  1344  0 19:10 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root      1464     1  0 19:10 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root      1511  1444  1 19:10 tty7     00:00:31 /usr/bin/X :0 -nr -verbose -auth
root      1518     1  0 19:10 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1521     1  0 19:10 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1529     1  0 19:10 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1530     1  0 19:10 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1533     1  0 19:10 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1540     1  0 19:10 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root      1542     1  0 19:10 ?        00:00:00 cron
daemon    1544     1  0 19:10 ?        00:00:00 atd
root      1547     1  0 19:10 ?        00:00:00 /usr/sbin/irqbalance
root      1651   575  0 19:10 ?        00:00:00 udevd --daemon
root      1652   575  0 19:10 ?        00:00:00 udevd --daemon
root      1685     1  0 19:11 tty1     00:00:00 /sbin/getty -8 38400 tty1
gdm       1704     1  0 19:11 ?        00:00:00 /usr/bin/dbus-launch --exit-with
root      1725  1444  0 19:11 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
rtkit     1733     1  0 19:11 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
root      1735     1  0 19:11 ?        00:00:00 /usr/lib/upower/upowerd
root      1739     1  0 19:11 ?        00:00:00 /usr/lib/policykit-1/polkitd
1000      1834     1  0 19:11 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
1000      1853  1725  0 19:11 ?        00:00:00 gnome-session
1000      1888  1853  0 19:12 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
1000      1891     1  0 19:12 ?        00:00:00 /usr/bin/dbus-launch --exit-with
1000      1892     1  0 19:12 ?        00:00:00 /bin/dbus-daemon --fork --print-
1000      1897     1  0 19:12 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
1000      1898  1853  0 19:12 ?        00:00:00 gnome-power-manager
1000      1904     1  0 19:12 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
1000      1910     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfsd
1000      1916     1  0 19:12 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
1000      1924     1  0 19:12 ?        00:00:00 /usr/bin/pulseaudio --start --lo
1000      1929  1853  0 19:12 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
1000      1930  1853  0 19:12 ?        00:00:00 bluetooth-applet
1000      1931  1853  0 19:12 ?        00:00:00 gnome-panel
1000      1932  1853  0 19:12 ?        00:00:10 /usr/bin/compiz
1000      1933  1853  0 19:12 ?        00:00:00 nautilus
1000      1936  1853  0 19:12 ?        00:00:00 nm-applet --sm-disable
1000      1942  1853  0 19:12 ?        00:00:00 /usr/bin/python /usr/bin/mintupd
1000      1945  1942  0 19:12 ?        00:00:00 sh -c /usr/lib/linuxmint/mintUpd
1000      1946  1945  0 19:12 ?        00:00:00 python /usr/lib/linuxmint/mintUp
1000      1960     1  0 19:12 ?        00:00:00 gnome-screensaver
1000      1968     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
1000      2003     1  0 19:12 ?        00:00:00 /usr/lib/bonobo-activation/bonob
1000      2023     1  0 19:12 ?        00:00:01 python /usr/lib/linuxmint/mintMe
1000      2025     1  0 19:12 ?        00:00:00 /usr/lib/gnome-panel/wnck-applet
1000      2027     1  0 19:12 ?        00:00:00 /usr/lib/gnome-panel/clock-apple
1000      2030     1  0 19:12 ?        00:00:00 /usr/lib/indicator-applet/indica
1000      2031     1  0 19:12 ?        00:00:00 /usr/lib/gnome-panel/notificatio
1000      2050     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
1000      2061     1  0 19:12 ?        00:00:00 /usr/lib/indicator-sound/indicat
1000      2064     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
root      2069     1  0 19:12 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      2070  2069  0 19:12 ?        00:00:00 udisks-daemon: polling /dev/sr0
1000      2072     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
1000      2078  1932  0 19:12 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
1000      2079  2078  0 19:12 ?        00:00:00 /usr/bin/gtk-window-decorator
1000      2084     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
1000      2088     1  0 19:12 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
1000      2095     1  0 19:12 ?        00:00:00 /usr/lib/indicator-application/i
1000      2098  1924  0 19:12 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
1000      2147  1853  0 19:12 ?        00:00:00 /usr/bin/python /usr/share/syste
1000      2149  2023  0 19:13 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.13/
1000      2153  2149  0 19:13 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.13/
1000      2157  2153  2 19:13 ?        00:00:30 /usr/lib/firefox-3.6.13/firefox-
1000      2360  2023  0 19:16 ?        00:00:00 gnome-terminal
1000      2364  2360  0 19:16 ?        00:00:00 gnome-pty-helper
1000      2365  2360  0 19:16 pts/0    00:00:00 bash
1000      2451  2157  0 19:23 ?        00:00:02 /usr/lib/firefox-3.6.13/plugin-c
1000      2542  2365  0 19:36 pts/0    00:00:00 ps -ef
```

---

### Post by Syndacate on 2011-01-27
On a side note, it flashes some "fatal error" message right before the loading/splash screen.  I am not sure if this is related to the problem, I did NOT see it on Ubuntu.

Does this get dumped to a log file anywhere?  Or is it missed, gone forever?

It flashes too fast to see it..

---

### Post by oODeanOo on 2011-03-30
I fixed the lag introduced by the native ATI drivers using the simple fix here

[http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04](http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04)

Dean

---

### Post by Syndacate on 2011-03-30
> **oODeanOo said:**
> I fixed the lag introduced by the native ATI drivers using the simple fix here

[http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04](http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04)

Dean

Does the lag introduced by the ATI drivers have any effect if you have an Nvidia card (and hopefully it's running those native ones)?  I don't have an ATI card.

My guess is it won't be here next month, April, when they come out with the next version.  Though right now I'm trying FC14 so, guess we'll see what happens O.o.

---

