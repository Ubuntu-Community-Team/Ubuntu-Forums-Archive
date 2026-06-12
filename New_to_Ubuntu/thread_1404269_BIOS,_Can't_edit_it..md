---
title: "BIOS, Can't edit it."
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Lunami on 2010-02-11
Title explains itself. I can't edit anything, at all. This worked fine yesterday, and the only thing I did was change the boot order. I am able to change it back by hitting F6 on the keyboard, which changes it to it's default choices, but I kinda like the ability to edit these things myself, as I don't like some of the choices in default. I have a CD for the motherboard, but that doesn't work, giving me the invalid OS dialog box. And I haven't found the disk for Ubuntu yet, so that's not even on, but I doubt it will work either, seeing as Ubuntu 9.10, is a fair bit newer than Win XP. I've tried to remove the battery, but either;
1. My hands are too large to grip it properly or,
2. It doesn't want to come out.

Any help with this would be appreciated.

---

### Post by Grenage on 2010-02-11
There will likely be a jumper to reset the BIOS; if it isn't obvious, look for a manual online.

---

### Post by Lunami on 2010-02-11
Hello again Grenage.

Well, what would this jumper look like? The last time I popped her open, I found 4 switches near the battery. Looked like, of the four, only one was switched in the on position, although I don't know if this is what I'm looking for, or not.

Just want to be sure before I open it up again.

---

### Post by Grenage on 2010-02-11
Normally it will be on its own, but don't randomly flip switches on the off-chance.  If you open the case and look at the board model, you can look it up online and be sure.

---

### Post by Lunami on 2010-02-11
Alright, I'll just use AIDA, I suppose. It should be able to tell me, can't quite seem to find it through hardware.

I really should start making a note of the exact parts in my machine, and list them somewhere on paper, would likely make my life much easier.

---

### Post by lidex on 2010-02-11
Resetting via the jumper will just return it to defaults, which may or may not help. Some bios have a password/key-combo to protect from unauthorized changes that you may have inadvertently enabled. Take a close look at the bios screen for any info there or, as suggested, google your MB manual or check manufacturer site.

---

### Post by Mark Phelps on 2010-02-11
Motherboards generally all have a small, circular batter, the size of a penny, that is used to save the CMOS settings -- which you change in the BIOS screens.  The jumper to reset the CMOS to defaults is generally located right next to this batter.

The procedure, in general, is as follows:
1) Find the battery
2) Find the jumper
3) Remove the battery
4) Change the jumper to reset the CMOS
5) Wait 30 seconds
6) Reset the jumper
7) Replace the battery

Then, when you reboot, your BIOS settings will be reset to factory default.

---

### Post by Chris Edgell on 2010-02-11
I was told "here" that if you remove the battery for 15 minutes, the bios automatically reset.  IS that, or is it NOT so?

With my battery one edge of the battery has little plastic edges sticking out over some of the battery, holding it in place. The other edge has plastic holders but they look more like rims than holders.  Lift the side that looks like rim edging and it will slide out from under the edge that has the plastic protruding out a bit over some of the battery.  Re-insert with the same idea in mind.

---

### Post by steve-shinn on 2010-02-11
> **Chris Edgell said:**
> I was told "here" that if you remove the battery for 15 minutes, the bios automatically reset.  IS that, or is it NOT so?

Correct ..... but that would be the minimum ..... 30 minutes should do it.

---

### Post by Grenage on 2010-02-12
In reality the BIOS will reset in seconds, but it never hurts to leave it out, sometimes a reasonable charge is held on the board.

---

### Post by kenweill on 2010-02-12
it would be better to just remove the battery.

remove the power cord of you computer before removing the battery in the motherboard. power cord at the back of the system unit. then remove the battery in the motherboard. 15 minutes? never tried that. i usually remove the battery for about 5 - 10 seconds then put it back.

removing the battery is much safer than resetting through jumper. why? with jumpers, it's just like your shorting the battery. shorting the pins of the battery just makes the battery power drain. if ever you don't have any other choice, then, use the jumper but only about 3 seconds. usually, there are only 3 pins on the jumper.

---

