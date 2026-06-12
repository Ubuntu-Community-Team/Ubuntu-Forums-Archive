---
title: "Ubuntu freezing-- but so did windows. How to diagnose?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Fieari on 2011-05-10
After switching to Ubuntu on my own system and starting to get a feel for it, my parents decided they wanted to switch as well. They were using Windows Vista, and getting the blue screen of death at least twice a day. I happily obliged and popped ubuntu on here.

The problem is, it seems ubuntu isn't being much more stable!  It doesn't give the blue screen... no, it simply locks up entirely, freezing everything, requiring a hard boot.

I'm starting to suspect that this may be an issue with the hardware itself, and not the OS, but how can I find out for certain?

---

### Post by GiuHei3u on 2011-05-10
> **Fieari said:**
> After switching to Ubuntu on my own system and starting to get a feel for it, my parents decided they wanted to switch as well. They were using Windows Vista, and getting the blue screen of death at least twice a day. I happily obliged and popped ubuntu on here.

The problem is, it seems ubuntu isn't being much more stable!  It doesn't give the blue screen... no, it simply locks up entirely, freezing everything, requiring a hard boot.

I'm starting to suspect that this may be an issue with the hardware itself, and not the OS, but how can I find out for certain?

I am having the very same problem. In fact I put a post about this very thing this morning. Post I think is 
Computer Freezing.

gumshoe

---

### Post by dFlyer on 2011-05-10
> **Fieari said:**
> After switching to Ubuntu on my own system and starting to get a feel for it, my parents decided they wanted to switch as well. They were using Windows Vista, and getting the blue screen of death at least twice a day. I happily obliged and popped ubuntu on here.

The problem is, it seems ubuntu isn't being much more stable!  It doesn't give the blue screen... no, it simply locks up entirely, freezing everything, requiring a hard boot.

I'm starting to suspect that this may be an issue with the hardware itself, and not the OS, but how can I find out for certain?

Two things to try. First check the HD to see if there are damaged sectors using ubuntu destop cd. Second thing is check your ram to see if it's damaged.

---

### Post by no2498 on 2011-05-10
install htop type it in a terminal click enter it tells you how to install it

after installed type htop click enter

look an see if its using to much memory 

if not its heat or the power pack going bad
if not heat replace the power pack fast or they take mother board out

---

### Post by egalvan on 2011-05-10
If it's a Vista machine, it may be old enough that it's full of lint and dust-bunnies.

take it outside, open it up and give it a good cleaning with some compressed air cans (if needed).

further steps to take:
un-plug and re-plug **every thing** that can be un-plugged/disconnected.
do it ONE PIECE/WIRE/CABLE/CARD at a time so you don't loose track of where things belong.
(sometimes minor corrosion on the metal contacts can be removed this way.)

---

### Post by debd on 2011-05-10
I faced the same problem a few months back when I tried to do a wubi install in a friend's computer. It was freezing at times and then getting back to normal. I suspected a low disk space problem and did a reinstall with a 10gb filesystem (the previous installation size was 5gb)and it didn't freeze that time.

---

### Post by barefootNH on 2011-05-10
I helped someone out with almost the exact same problem just a couple days ago.

Memtest86 showed that it was a bad memory stick: he took it out and it's been working perfectly ever since (he had 2 2GB sticks and is now running just 1 stick of 2GB). He has now ordered a completely new set of memory sticks.

---

### Post by rkillcrazy on 2011-05-10
> **Fieari said:**
> After switching to Ubuntu on my own system and starting to get a feel for it, my parents decided they wanted to switch as well. They were using Windows Vista, and getting the blue screen of death at least twice a day. I happily obliged and popped ubuntu on here.

The problem is, it seems ubuntu isn't being much more stable!  It doesn't give the blue screen... no, it simply locks up entirely, freezing everything, requiring a hard boot.

I'm starting to suspect that this may be an issue with the hardware itself, and not the OS, but how can I find out for certain?

Troubleshooting hardware is best done with known-good hardware.  For example, swap out your power supply unit with a known good PSU and see how it responds.  Unfortunately, many people don't have a lot of spare parts to play trial-and-error with and can't warrant spending money on parts they may not need.  If the system is set up as a dual-boot system and Windows is still on that PC, you can see if it logged anything in Event Viewer prior to a lockup.  Or, if the BSoD listed the same error all the time.  I've found that if a Windows system doesn't log anything, then the issue may be power related.  Swapping out a PSU was a quick and relatively inexpensive fix.  The Ubuntu install media has a memory checker on it so that may help.  If it was showing the same error on your BSoD all the time, you could Google it and see what others have found.  Same with anything found in Event Viewer.  Unfortunately, I'm not familiar enough with Linux to know if it has something similar to Event Viewer but I would like to think it does...  Beyond that, you could run a check-disk in Windows - again, assuming you still have access to the OS.  I think Linux also has something of the sort.

---

### Post by Fieari on 2011-05-10
How do I check my RAM and the HD in Ubuntu?  I'll try that first, given that, you're certainly right, I don't have spare hardware lying around to swap out and test.

---

### Post by triceratops on 2011-05-10
> **Fieari said:**
> How do I check my RAM and the HD in Ubuntu?  I'll try that first, given that, you're certainly right, I don't have spare hardware lying around to swap out and test.

In your user account $, type

```
df 
``` to see the space left in your various HDD partitions (in 1000 KB segments), including swap partition space.

```
free -m
```will show you your RAM memory use in MB.

---

### Post by audiomick on 2011-05-10
> **Fieari said:**
> How do I check my RAM and the HD in Ubuntu?  I'll try that first, given that, you're certainly right, I don't have spare hardware lying around to swap out and test.

The memtest option in the boot menu checks the RAM for faults.

Now I am at a loss. I am nearly sure that this is available from the live CD, but I am not at home, so I can't check. Anyway, you have just installed, so you should still have the CD or USB medium. Boot from that, use the cursor arrows to go to the icon on the very first screen that looks a bit like a monitor. That should give you menu to choose from, and the last entry should be memtest, I think. Let it run for a couple of hours or even overnight. If the RAM is ok, then you will have zero errors.

To check the drive, one option is smartmontools. Unfortunately, this is not very intuitive. The advantage is that it reads out data from the drive that the manufacturer also would use to check the condition of the drive.

Here is some info. Take a particular look at the bit about gSmartControl

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by Throne777 on 2011-05-10
> **audiomick said:**
> The memtest option in the boot menu checks the RAM for faults.

Now I am at a loss. I am nearly sure that this is available from the live CD, but I am not at home, so I can't check. Anyway, you have just installed, so you should still have the CD or USB medium. Boot from that, use the cursor arrows to go to the icon on the very first screen that looks a bit like a monitor. That should give you menu to choose from, and the last entry should be memtest, I think. Let it run for a couple of hours or even overnight. If the RAM is ok, then you will have zero errors.


The 11.04 boot disc hides the Mem Test option (annoyingly).
Before you get to the really shiny/pretty graphical interface that gives you the option to Try or Install, there'll be a low graphic purple screen with one or two icons at the bottom. When that screen appears, press any key and you get a more old skool installer where you can opt to run the Mem Test.

---

### Post by jtarin on 2011-05-10
BSOD and Freeze-ups.....two very different animals.
BSOD's will give you a number to cross-reference everytime.
Dust-bunnies......eliminate.
Event viewer for linux?
System > administration> log file viewer
If you want to look at the logs in another manner they are also stored in /var/log.

---

### Post by mastablasta on 2011-05-11
open the box and check for bulged capacitors like this: [http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)
 
it can be on motherboard or graphics card or power supply. this is often the cause of freezing but it can also cause BSOD if capacitors on crucial system are malfunctioning.
 
second option is simpler so while you have the case open clean it - it might be that it's simply the CPU ventilator that is not working porpperly due to dust causing the CPU to overheat resulting in crashes. you can also check this with a couple of temp monitors.

---

### Post by Fieari on 2011-05-12
Sorry for slow status updates, I've been working on this intermittently since it's not my own computer.

Just ran the memtest (I initially installed from ubuntu 10, so the boot list does still show it as an option) and it came back 100% clean. Looking into hard drive tests now...

---

### Post by audiomick on 2011-05-12
Cool. Keep us posted... ;)

---

### Post by skypuppy on 2011-05-12
I've seen machines do this and it is usually dust that has accumulated in the cpu's heatsink fins.  Hard to clean safely, too.

---

### Post by jtarin on 2011-05-12
> **skypuppy said:**
> I've seen machines do this and it is usually dust that has accumulated in the cpu's heatsink fins.  Hard to clean safely, too.Not if you have a leaf-blower.:P

---

### Post by wildmanne39 on 2011-05-13
I would check the dust also before getting into to much other stuff because dust causes a large amount of problems,I have known people to buy a new computer when all they needed was to clean there's out. I personally clean mine every six months.:)

---

### Post by daniell59 on 2011-05-13
> **Fieari said:**
> Sorry for slow status updates, I've been working on this intermittently since it's not my own computer.

Just ran the memtest (I initially installed from ubuntu 10, so the boot list does still show it as an option) and it came back 100% clean. Looking into hard drive tests now...

I was having the same problem on my homebuilt computer. The memory checked out fine. 
It turned out that memory voltage and timings were incorrect. Once set properly, I have not had a single freeze.

---

### Post by rkillcrazy on 2011-05-13
> **skypuppy said:**
> I've seen machines do this and it is usually dust that has accumulated in the cpu's heatsink fins.  Hard to clean safely, too.

A very [safe and] easy way to clean a PC safely is by using some canned air and a vacuum.  One can do this while the PC is on but it's not advised...  Whilst holding the vacuum's hose-attachment in the case, use the canned air to shoot short bursts into whatever device you're trying to clean out.  The canned air will break loose various particulates and the vacuum will draw them in so you don't have much of a mess on the floor when you're done.

---

### Post by audiomick on 2011-05-13
> **rkillcrazy said:**
> A very [safe and] easy way to clean a PC safely is by using ...so you don't have[COLOR=Blue] much[/COLOR] of a mess on the floor when you're done.

Well said... :lol:

Getting the dust out is indeed a good plan, and is a good first step. I didn't mention that in my earlier post, but should have. ;)

---

