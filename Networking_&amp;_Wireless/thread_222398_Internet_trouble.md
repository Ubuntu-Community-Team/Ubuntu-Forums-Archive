---
title: "Internet trouble"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by .Maleficus. on 2006-07-24
Well, I don't know why I can't get internet.  The lights on my ethernet card are on, and the light on my router is on.  All I did was move my computer from one room to another.  Does cable length matter?  I'm guessing it doesn't, but before I was using an approximately 10' cable, and now I'm using a +100' cable.  Would that cause me to no longer have a connection?

---

### Post by dtfinch on 2006-07-25
If you're using gigabit, try switching it to 100mbit. If at 100mbit already, try 10mbit.

Did you put the ends on the cable yourself? Where I work we had an issue with some long cables where the color pairs weren't grouped together correctly, and the cables could only handle 10mbit as a result. For the longest time we suspected a distance or noise problem, because the cables actually did work, just at slower speeds. The correct color pairing is a bit non-obvious, and problems may only show up with longer cables. Kinks in the cable are another common cause of problems. If you're using stranded cable, and all else fails, switching to solid (if it's not too much work) might help.

---

### Post by .Maleficus. on 2006-07-25
Ok, I'll try to go at a slower speed.  This may sound dumb, but how do I switch it?

Yes I did put them on myself.  Should I get rid of excess cable too?  The guy at the store I bought it from gave me probably 50' more than I needed so I have a bunch coiled around a shoebox in my basement, but it's still all one wire.

---

### Post by mips on 2006-07-25
[http://www.ubuntuforums.org/showthread.php?t=191653](http://www.ubuntuforums.org/showthread.php?t=191653)

---

### Post by .Maleficus. on 2006-07-25
This is what I tried.  Is this right?
```
sudo ethtool -s eth1 speed 10
```
I believe eth1 is what my PCI card is, but I'm not sure.
Did I do it right?  Because I still couldn't get on to the internet.  I'm probably going to cut the app. 30' excess wire soon, and put on another connecter.  Will that help my problem at all?

BTW, I'm a n00b at ethernet and Linux in general, so please bear with all of my questions.

---

### Post by .Maleficus. on 2006-07-25
I cut the wire, put on the connecter, and found out I had the wires backwards.  Awesome.  Time to get another connecter.  When stringing the excess wire through to a place where I could cut it, I made sure that there were no kinks in the wire and everything is straight.

Also, what is a stranded cable and what is a solid cable?

---

### Post by mips on 2006-07-25
> **.Maleficus. said:**
> I cut the wire, put on the connecter, and found out I had the wires backwards.  Awesome.  Time to get another connecter.  When stringing the excess wire through to a place where I could cut it, I made sure that there were no kinks in the wire and everything is straight.

Also, what is a stranded cable and what is a solid cable?

Stranded: If you look at the cable you will see it has 8 cores (or wires), each of these cores are made up of thin strands of copper wire.

Solid: Each of the 8 cores is a single piece of copper wire.

Stranded cable is only used in patch & fly- leads and RJ-45 connectors seem to crimp better onto stranded cable.
Solid cable is used between patch panels and outlet boxes where you would battle to to terminate a stranded cable.
There are also differences in electrical properties of the two types of cable.

Cable should not exceed 100m of which 90m is solid and 10m is stranded which should not be exceeded.

---

### Post by .Maleficus. on 2006-07-25
I think that my wire is solid, but I could be wrong.  100m you say... Then it should work right?  Because I'm only using 100ft. which is like a 1/3 of what I can have, if I'm correct.

Also, I did this to get some information about my ethernet card.
```
dmesg | grep eth1
```
It mostly told me what I already knew, but it also told me that it was running at 100.  That means that my attemp to switch it to 10 didn't work.

---

### Post by .Maleficus. on 2006-07-25
I got my connector on and when I run dmesg ... I get No IPv6 routers present.  I'm sure I'm connected to my router.

When I do sudo ethtool -s eth1 speed 10, and half duplex, is anything supposed to happen after I type it?  Because nothing does.



Edit:  Ah ha!  I think I have something useful.  On my ethernet card, there are 3 lights.  The only one that is lit up is the one by the number 10.  There is also a light by 00 (I'm guessing meaning 100) and one by ACT.  Anybody know what ACT means and how I can fix this problem?

---

### Post by mips on 2006-07-26
ACT=Active I think ?

---

### Post by sonnywise on 2006-07-26
act means activity. In normal conditions it should be blinking.

Some checks to do:
- verify you respect one of the two color layouts specified by the Ethernet standard:

 586A 
1. White-Green
2. Green
3. White-Orange
4. Blue
5. White-Blue
6. Orange
7. White-Brown
8. Brown

 586B 
1. White-Orange
2. Orange
3. White-Green
4. Blue
5. White-Blue
6. Green
7. White-Brown
8. Brown

- the link speed of your nic should be leaved in auto mode if you don't know which is your router's interface setting otherwise set them accordingly.

I hope this can help.

---

### Post by monkieie on 2006-07-26
have you tried the terminal command
ifconfig

Please enter the output here.

---

