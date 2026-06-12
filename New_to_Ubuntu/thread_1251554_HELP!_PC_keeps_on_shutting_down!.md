---
title: "HELP! PC keeps on shutting down!"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by furoido on 2009-08-27
Please help! Since yesterday, my pc has been shutting down without warning every few minutes! Sometimes it will automatically re-start, other times not...

Anyone got any idea what is causing the problem and more importantly, STEP-BY-STEP instructions on how to fix it?

Cheers!

PS on one start-up, it performed the regular disk scan, but found no errors....

---

### Post by dfreer on 2009-08-27
First thought would be an overheating issue. Check if all your fans are running, after it restarts check your CPU temps in BIOS if you have them.

---

### Post by stalkier on 2009-08-27
> **dfreer said:**
> first thought would be an overheating issue. Check if all your fans are running, after it restarts check your cpu temps in bios if you have them.

+1

---

### Post by furoido on 2009-08-27
I thought it might be the heat, but the fans are working fine and the pc does not feel even slightly hot...and its just done it again after having been switched off all night...

---

### Post by KinKiac on 2009-08-27
Is your box and/or heatsink/fans/graphics card dusty?  Ive had problems before where my fans where running but due to a lot of dust in and around heatsink and even my graphics card, something was overheating(not sure what it was at the time).  After I dusted out everything with an air duster it worked fine again.

(Also Ive heard of dust causing the thermal sensor to malfunction, making the PC think it is overheating)

---

### Post by furoido on 2009-08-27
Kinkiac,
Yes, the internals were extremely dusty and just given them a good clean! Been going for about 15 minutes without shutting down, so fingers crossed!

---

### Post by nandemonai on 2009-08-27
Hop into BIOS and check out the 'PC Health' option or similar to check on your CPU / Mainboard temps.

---

### Post by SoftwareExplorer on 2009-08-27
If it still gives you trouble it could be that your power supply is failing. Lets hope the dusting did the trick.

---

### Post by furoido on 2009-08-27
Just crashed again after I tried to move the pc! Have a horrible feeling it could be the power supply...this time it would only re-start after I jiggled the power line/socket at the back...but if it is the power supply, why should it shut down when I don't touch/move the pc?

Sorry to sound dumb, but how do I access BIOS?

---

### Post by NoaHall on 2009-08-27
It depends. Normally, press "delete" before anything has started.

---

### Post by fela on 2009-08-27
> **SoftwareExplorer said:**
> If it still gives you trouble it could be that your power supply is failing. Lets hope the dusting did the trick.

+1. I'd backup all your data for one thing, as dodgy power supplies, when they break, can bring down your whole system (including harddrive data with no easy/cheap recovery). This problem is either one of these three:

1) Something's overheating, probably CPU, or the system thinks it's overheating.

2) Dodgy PSU (are there alot of power hungry components - have you upgraded your PC alot without thinking about the power usage of each component - is the PC very old?)

or 3) Some other problem that I can't think of.

---

### Post by fanglinyong on 2009-08-27
is your voltage instability?if not, it can cause your pc reboot frequently!

---

### Post by lisati on 2009-08-27
> **NoaHall said:**
> It depends. Normally, press "delete" before anything has started.

Can also be 'Esc' or one of the F keys, pressed while the manufacturer's splash screen is displayed when you turn on your computer. Look for a message at the bottom of the screen along the lines of "Press <key> to enter setup"

---

### Post by theozzlives on 2009-08-27
> **furoido said:**
> Just crashed again after I tried to move the pc! Have a horrible feeling it could be the power supply...this time it would only re-start after I jiggled the power line/socket at the back...but if it is the power supply, why should it shut down when I don't touch/move the pc?

Sorry to sound dumb, but how do I access BIOS?

Not supposed to move your PC when it's running.

---

### Post by lisati on 2009-08-27
> **theozzlives said:**
> Not supposed to move your PC when it's running.

+1: it's good to play it safe.

---

### Post by SoftwareExplorer on 2009-08-28
The reason I said it might be the power supply is that I have had a few that would overheat and when that happend the computer would shut down after running for a while, even if no one touched it. Of course, where the cord connects in the back could have a bad connection if the cord looses power when you bump it. fela is correct, if your power supply dies, it can take hard drives with it. I've had it happen to me, but the symptoms for that time were different from what you are describing--it kept blowing the circuit breaker and eventually spewed smoke.

---

### Post by blackened on 2009-08-28
> **fela said:**
> ...or 3) Some other problem that I can't think of.

I've additionally seen these symptoms on a few dying mobos and bad sticks of ram. Though it is more likely the PSU.

---

### Post by Bartender on 2009-08-28
I'm guessing the OP doesn't have experience doing it, but I'd pop the CPU heatsink off, clean the surfaces with some alcohol, and re-apply thermal paste.

I had an odd experience with heatsinks a few days ago - removed the side panel off a desktop PC running an ASUS P5GDC-V motherboard.  The board is about five years old now, never used hard.  The northbridge heatsink felt alarmingly hot to the touch.  Checked temps with Speedfan, chipset was 60+ degrees C.  Shut it down, removed the little spring clips, and the aluminum heatsink fell off.  The original thermal paste had dried out.  Cleaned the surfaces, applied a dab of Arctic Silver, seems to be running fine now.  Speedfan reports temps slightly above motherboard temps.

---

### Post by presence1960 on 2009-08-28
i had the same problem last summer. I open my PC once a month and blow the dust out. I kept getting shut downs for no apparent reason so of course I checked the PSU. But it was fine. So I checked all the cables and voila one was loose. It wasn't seated properly. I fixed that and have not had a problem since. I would check all your cables from your power supply to see they are right.

---

### Post by LewRockwell on 2009-08-28
come on!?!

argh!

two pages of posts and no one has even asked the OP for system specifics?!?

for all we know it's a TRS-80 running who-knows-what!?!

let's say the OP has "XYZ" machine and they don't know that there has been a total product recall because "XYZ" machine has caused 27 fatalities in deadly residential home fires...

if you don't know what equipment the OP has...you CANNOT help the OP to the best of your ability...POINT BLANK!?!?!

Anywho...

keeping the internals clean is a must

keeping the thermal compound reasonably fresh is a must

not moving a running desktop is a very good idea

we've had motherboard components emit smoke and sparks as they go bad

we've had power supply components emit smoke and sparks as they go bad

clean internals prevent dust and debris from igniting during these events

our personal advice to OP regarding this trouble-call is to get to know your internals and how they work together and how to troubleshoot and test them

if this is beyond your comfort level then find someone else to do it


and again, shame on all of you who didn't ask the basic mandatory questions


.

---

### Post by KinKiac on 2009-08-28
> **LewRockwell said:**
> come on!?!

argh!

two pages of posts and no one has even asked the OP for system specifics?!?

for all we know it's a TRS-80 running who-knows-what!?!

let's say the OP has "XYZ" machine and they don't know that there has been a total product recall because "XYZ" machine has caused 27 fatalities in deadly residential home fires...

if you don't know what equipment the OP has...you CANNOT help the OP to the best of your ability...POINT BLANK!?!?!

Anywho...

keeping the internals clean is a must

keeping the thermal compound reasonably fresh is a must

not moving a running desktop is a very good idea

we've had motherboard components emit smoke and sparks as they go bad

we've had power supply components emit smoke and sparks as they go bad

clean internals prevent dust and debris from igniting during these events

our personal advice to OP regarding this trouble-call is to get to know your internals and how they work together and how to troubleshoot and test them

if this is beyond your comfort level then find someone else to do it


and again, shame on all of you who didn't ask the basic mandatory questions


.

Wow.  Sorry to offend.  I cant speak for others but I was assuming the OP had a working PC for some time now and it just started doing this.  I also assumed that it didnt start after adding a new component or it would have been reported as such.  Noting these assumptions I assumed exact hardware didnt matter, something was overheating most likely and causing the PC to restart itself.  Aside from the unlikely case of the hardware recall that you noted i think the people who have responded have done a pretty good job of narrowing down the issue to most likely a loose connection or bad PSU, all without hardware details.

---

### Post by SoftwareExplorer on 2009-08-29
> **kinkiac said:**
> wow.  Sorry to offend.  I cant speak for others but i was assuming the op had a working pc for some time now and it just started doing this.  I also assumed that it didnt start after adding a new component or it would have been reported as such.  Noting these assumptions i assumed exact hardware didnt matter, something was overheating most likely and causing the pc to restart itself.  Aside from the unlikely case of the hardware recall that you noted i think the people who have responded have done a pretty good job of narrowing down the issue to most likely a loose connection or bad psu, all without hardware details.

+1

---

### Post by presence1960 on 2009-08-29
> **SoftwareExplorer said:**
> +1

I didn't take it personally. In my opinion Lew has a lot of good info that can help people. Since I didn't feel like I did anything wrong I just let it roll off my back. Everyone has their own methodology to diagnosing problems and helping people. For Installs and boot problems I insist on running the boot info script before I give any suggestions that way I know exactly what setup is on the person's machine. I know Lew always asks for specs, that's his way of figuring out how to help. I won't fault him for that even when specs aren't necessary. Lew is also a big proponent of Super Grub disk. I prefer to fix GRUB through terminal. Both methods work. That is all that matters!

For every task in Linux there are usually multiple ways to accomplish that task. So let's not get hung up on methods instead of looking for RESULTS.

Maybe there could have been a more diplomatic way to state what was said. But that is water over the dam.

---

