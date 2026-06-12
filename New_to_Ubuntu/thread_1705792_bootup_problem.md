---
title: "bootup problem"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by LadyA on 2011-03-12
I am helping a friend with a compac computer, which is about 5 years old and has Ubuntu installed. When turned on, the compac screen comes up and the next screen has a black background with red lines about an inch long in rows across the screen. nothing happens after this screen. Could this be a bad graphics card? Ubuntu was working fine until her husband blew the dust  out of it with an air chuck.

---

### Post by Hedgehog1 on 2011-03-12
> **LadyA said:**
> ...Ubuntu was working fine **until her husband blew the dust  out of it with an air chuck.**

LadyA,

Every time I think I have heard it all, someone surprises me.

The violence of blowing out the 'dust' with that level of compressed air is likely the cause.  I suspect that cabling was knocked loose in the computer, and needs to be pressed back into place. 

If this is a laptop, the chore of getting cables pressed back into place can be really hard.

If this is a desktop, then removing the cover and pressing the cables back into place (making sure any boards are properly seating into the motherboard, too) is a much easier task.

***The Hedge***

:KS

p.s. Please don't let the husband near the BluRay player...

---

### Post by fabricator4 on 2011-03-12
> **LadyA said:**
>  Could this be a bad graphics card? Ubuntu was working fine until her husband blew the dust  out of it with an air chuck.

The problem may not have been the cleaning as such - old machines do tend to develop these reliability problems anyway - it could have failed at any time.

You do have to be a little careful however, at the kinds of pressures that tradesmen usually use: about 400+ kpa (60 psi, if you like) it's possible to blow dust into sockets instead of out of them.

My guess is something's been dislodged, or is making poor contact.  Try removing the RAM and cleaning the contacts.  Take precautions against static discharge otherwise you could finish up with even more problems.  The fact that the machine is getting through post is encouraging.

If the machine has a plug in video card the remove that and clean the contacts/socket as well.

Any unused cards like old dialup modems, remove them permanently.

Once you get the machine booting, I recommend you boot up with memtest86+ and leave it running overnight.  This will help to show up any reliability problems or problems with the ram itself.  If it's still running in the morning and shows no errors, you can have some confidence in the machine.  If it's hung or has thrown up some memory errors, then obviously you do still have a problem.

Chris.

---

### Post by fabricator4 on 2011-03-12
> **Hedgehog1 said:**
> LadyA,

Every time I think I have heard it all, someone surprises me.


Actually, it's not so silly. I've had jobs where I had fix lots of old machines, and an air compressor and air gun make the whole thing a lot more pleasant.  It also lets you get the dust out of heat sinks and power supplies which would would otherwise require completely dismantling the machine.  This is done outside in the fresh air, of course.

The absolute worst thing is working on a machine clogged with dust and lint.  In places where it wasn't possible to clean the machine like this, I've sometimes been made ill, once for about two days.  You really have no idea what some people have inside their machines.

Laptops need special care of course, but generally speaking, if it gets broken by cleaning it out, it needed fixing anyway.


Chris.

---

### Post by LadyA on 2011-03-12
This is a desktop and he did clean it outside. I checked the connections and cleaned the ram contacts. I now get this on the next screen after the compac screen: [ 0.764679] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block (0,0) 
Ubuntu booted up the first time I turned it on, but I tried to reboot to see if it would work again and it came up with that error. I really don't know much about fixing ubuntu, since mine has been working with no problems. Could I reinstall it and not have this error?

---

### Post by fabricator4 on 2011-03-12
> **LadyA said:**
> This is a desktop and he did clean it outside. I checked the connections and cleaned the ram contacts. I now get this on the next screen after the compac screen: [ 0.764679] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block (0,0) 
Ubuntu booted up the first time I turned it on, but I tried to reboot to see if it would work again and it came up with that error. I really don't know much about fixing ubuntu, since mine has been working with no problems. Could I reinstall it and not have this error?

I don't believe an re-install is indicated at this point - you may just finish up with a messed-up install.

I think what is happening is that the hard drive is not working reliably.  This could just be due to an issue with a cable.  Try removing the cable from the drive and re-inserting it, and do the same thing for the other end where it plugs into the main board.  Be careful not to plug it in wrong way round, or bend any pins in the socket.

If there is a DVD or CD drive plugged into it as well, leave this unplugged for now.

What type of drive is it - IDE or SATA?  IDE has a flat ribbon cable about 50mm wide.  Sata is also a flat cable, but thicker and only about 7 or 8 mm wide.

Chris.

---

### Post by LadyA on 2011-03-13
It is a sata drive. I will try removing the cable on the hard drive and reinserting it to see if that works. The computer does have a dvd so I will leave that unplugged for now.

---

### Post by fabricator4 on 2011-03-13
> **LadyA said:**
> It is a sata drive. I will try removing the cable on the hard drive and reinserting it to see if that works. The computer does have a dvd so I will leave that unplugged for now.

Is the DVD also a SATA drive?  Try using the DVD SATA cable for the HDD and see if it works (ie swap the cables)

Chris

---

### Post by Hedgehog1 on 2011-03-13
> **fabricator4 said:**
> Actually, it's not so silly. I've had jobs where I had fix lots of old machines, and an air compressor and air gun make the whole thing a lot more pleasant.  It also lets you get the dust out of heat sinks and power supplies which would would otherwise require completely dismantling the machine.  This is done outside in the fresh air, of course.

I see your point.  In your hands I would trust the use of an air gun (and besides, you are able to fix it if you break it).

I just had this vision of a laptop, slowly inflating like a blow-up mattress. :D

I am very happy at LadyA's comment:
>  I really don't know much about fixing ubuntu, since mine has been working with no problems. 

I am very pleased that she has not needed to fix anything, that is the kind of reliability I like to see in an OS.

***The Slightly Deflated Hedge***

:KS

---

### Post by LadyA on 2011-03-13
I tried unplugging and switching the cables and the only thing I get is the compac screen and then either the screen with the red lines or the error screen. Do you think a new hard drive would fix the problem?

---

### Post by wilee-nilee on 2011-03-13
> **LadyA said:**
> I tried unplugging and switching the cables and the only thing I get is the compac screen and then either the screen with the red lines or the error screen. Do you think a new hard drive would fix the problem?

Have you booted a live cd too see if it runs?

---

### Post by LadyA on 2011-03-13
I can't get the live cd to boot either. I think they really messed up their computer. I've switched two other people over to Ubuntu and we have been using it every day for a year and have had no problems, so I don't know what this couple is doing to have so many problems.

---

### Post by fabricator4 on 2011-03-13
> **LadyA said:**
> I tried unplugging and switching the cables and the only thing I get is the compac screen and then either the screen with the red lines or the error screen. Do you think a new hard drive would fix the problem?

No, I don't.  I was going to suggest trying to boot off the LiveCD, but I see wilee-nilee has already suggested that. 

At the moment it's starting to look like a very broken computer.

Is there an internal speaker?  I want to see if the MB is acting sanely. Leave the drives disconnected for now.  Remove the RAM from the machine and turn it on.  Yes, take the RAM out and turn it on.  It should start beeping Beeeeeeep eight times.  That's the system error for no ram. 

Now put the RAM in the machine and turn it back on.  Go into BIOS setting a look for a default reset mode that will be called something like "Fail-safe Defaults".  Select this and save/exit.

The machine will go through post slowly.  It should then complain that there is no boot device.  If this works, go back into the BIOS and select "Optimised Defaults" - it's normal running mode.

If this this operates normally and you get the message about no boot device, turn the machine off and plug the hard drive back in.  Start the machine up and see what happens.

Chris.

---

### Post by fabricator4 on 2011-03-13
> **Hedgehog1 said:**
> 
***The Slightly Deflated Hedge***
:KS

No need to feel deflated Hedge, you always give GREAT advice. :-)

So you were surprised at something outside your experience...  That's part of the adventure.


Personally, I know if I ever stop learning, being surprised, (and yes, making mistakes) or find I can't keep an open mind I'll know it's time to hang up my screwdriver. ;-)

Chris

---

### Post by LadyA on 2011-03-13
When I took the ram out and turned it on it gave one short beep and one long beep. I put the ram back in and finally got into bios settings. When I would do the F10 it would come up with the screen that has the red lines. When I got into the settings the only thing I could find was at the bottom it had F5 Setup Defaults and when I went to that it was a box that said Load Setup Defaults yes or no.

---

### Post by LadyA on 2011-03-13
fabricator4, I did everything that was in your last post. When I turned it on it booted into Ubuntu, but the mouse was frozen, so I rebooted with Alt+SysRg+b. This time the compac screen came up then the screen with the red lines. I tried again and this time the screen came up with the error [0.9267937 Kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block )0,0). One more try. This time I was able to boot into Ubuntu with a working mouse, but when I hit on restart, it went off and the compact screen came up and the next screen just sat there blank. Should I give up on this computer or is there something else I could try.

---

### Post by fabricator4 on 2011-03-13
> **LadyA said:**
> When I took the ram out and turned it on it gave one short beep and one long beep. I put the ram back in and finally got into bios settings. When I would do the F10 it would come up with the screen that has the red lines. When I got into the settings the only thing I could find was at the bottom it had F5 Setup Defaults and when I went to that it was a box that said Load Setup Defaults yes or no.


Hi LadyA, bad news I'm afraid.  If you're getting the screen with red lines trying to get into the BIOS then the machine is seriously unhappy.  I would try plugging a graphics card in and seeing if that works - It might be the memory on the graphics that is playing up - that memory is probably soldered onto the MB so there's no easy way to fix it.  I'm assuming the graphics card you're currently using is on the MB - I don't recall you saying you'd pulled the graphics card out and cleaned the contacts?

If you don't have another graphics card to try, I would suggest maybe not spending any money on this machine. Being able to get something really cheap to try would be key. (and Ubuntu compatible of course)

The only other thing I can think to try at this stage is to replace the memory, or do a mem86+ memory test if you can get the machine to go that far, but it's really sounding more like the graphics sub-system that is playing up.  I doubt is was the cleaning that caused this - you would have had problems with the machine sooner or later...  probably sooner.

Chris.

---

### Post by LadyA on 2011-03-13
Yes the graphic memory is soldered to the MB. I talked to the girl today,who's computer this is, and she said that she was getting the screen with the red lines sometimes before the cleaning. I had a feeling it might be a graphics problem. I suggested that she looks for another computer. 
Thankyou so much for your time and information with this problem. It is much appreciated and thankyou to others that replied to this thread.

---

### Post by Hedgehog1 on 2011-03-13
> **LadyA said:**
> ...I talked to the girl today,who's computer this is, and she said that she was getting the screen with the red lines sometimes before the cleaning....

LadyA, Fabricator4,

If the 'red lines' were already happening before the cleaning, then I guess the compressed air cleaning didn't start it.  I may have been too harsh about the Gent with the Air Nozzle.

***The Hedge***

:KS

p.s. But if someone uses a garden hose to clean out a PC next time, I reserve the right to stare at the post in absolute disbelief...

---

### Post by LadyA on 2011-03-14
Hedgehog1, I do know somebody who uses a garden hose to clean their computer. He said he never had a problem.

---

### Post by Hedgehog1 on 2011-03-14
> **LadyA said:**
> Hedgehog1, I do know somebody who uses a garden hose to clean their computer. He said he never had a problem.

[SIZE="2"]*Now I am going to have nightmares...*[/SIZE]

***The Hedge***

:KS

---

### Post by wep940 on 2011-03-14
In about 1979 or so I worked at a bank in IT.  The data center and all of our offices were in the basement.  We had a flood the blew the walls in on one side and out the other of the computer room, with the mainframe and other computers running.  Needless to say, that create quite the mess.  I worked with the field engineers pulling boards, dipping them in a bucket of water and scrubbing them with a toothbrush, blowing them dry with a hair dryer and setting them on paper towels.  We had to clean mud, grass blades, leaves, pretty much everything you could think of, out of the backplanes and the card slots.  Not a pretty sight (or site, for that matter!).  Couldn't even get the service processor working so ended up getting a different mainframe.  We also had a card punch and reader on the system.  I don't know if you've ever seen what millions of those little hole punchouts do when their wet, but believe me they stick to everything.
 
Would I use a regular air compressor to clean my PC?  Only if I was outside, had the boards removed and really needed to.  Otherwise I'd stick to one of the cans of compressed air.  But......that's just me.  ;)

---

### Post by 5149.5 on 2011-03-14
I worked for a company that assembled computers. In the mid 80s they got the ESD message and started making investments in all the anti-static gadgets. We wore special smocks and shoes that grounded us through a high resistance to the special flooring while we worked at static free work surfaces, etc. 

The QC people had this nifty meter that would measure static charges on things. It was kind of neat to play with. We could really peg it with an air hose and a nozzle. After that discovery we got these neat air nozzles that had plutonium or some such stuff in them. They were bright yellow, had the atomic symbol on them, had to have annual inspections by an outside lab,and were awfully expensive.

---

### Post by fabricator4 on 2011-03-14
> **Hedgehog1 said:**
> 
p.s. But if someone uses a garden hose to clean out a PC next time, I reserve the right to stare at the post in absolute disbelief...

Well, you _could_ use a garden hose.  I don't think I'd want to immerse the HDD or DVD recorder, but actually most electronics, as in discreet components, are quite waterproof.

The trouble would only start if everything was not completely dry before you turned it on.

A place I worked at had baths of special solvents, designed for cleaning crud and corrosion off circuit boards. You just dropped the board in there, then scrubbed away at it with something like a heavy duty toothbrush.  It was amazing how it restored the board, components and all to near-new appearance.  Many of these boards were digital based and had several microprocessors on them.  About the only components we removed before dunking them were batteries, piezo speakers, and variable caps.

The boards were then hosed off with de-mineralised water and put out in the sun to dry.  A fast drying method was to immerse it in a bath of alcohol.  The alcohol displaced the water and then air dried very quickly in a warm place.

So yeah, get out the garden hose and give it a go.  (just kidding) :-)

Chris.

---

### Post by fabricator4 on 2011-03-14
> **LadyA said:**
> cleaning. I had a feeling it might be a graphics problem. I suggested that she looks for another computer. 


Well you can't win them all.  Hopefully they'll ask you to put Ubuntu onto the next one as well.

Chris

---

