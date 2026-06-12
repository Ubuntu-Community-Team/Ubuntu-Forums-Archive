---
title: "hp pavillion desktop will not power on"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-08-06
My mother has a hp pavillion A1747C.  when i press the power button nothing happens. and i mean nothing.  the light on the back of the powersupply will not light up, there is nothing going on in the system at all. i just replaced the power supply with an oem power supply and double checked that all connectors are in place. still nothing. i then removed the battery on the motherboard for ten seconds and still nothing. Could it be the motherboard is fried too? how can i trouble shoot that the motherboard is good or bad?  is there something else I'm missing? please let me know asap.  thanx in advance!

---

### Post by cariboo on 2010-08-07
The first and easiest thing I would suggest you do is make sure the replacement power supply supplies the correct voltage for the laptop. If you don't have one, I would suggest you pickup an inexpensive VOM (voltage/ohm meter), the next step would be disassemble the laptop and check the power connector on the motherboard. If both of those are good, you will more than likely need a replacement motherboard.

---

### Post by lkraemer on 2010-08-08
STOP!  Don't disassemble, and destroy your mothers computer, when you have
not properly thought about where the problem is!

If the LED on the Power supply is NOT "ON", then the problem is before
the power supply, not downstream.  I'd turn on the closest lamp, then move
the lamp to the outlet where the computer is plugged into, and verify that
the lamp works on both Duplex Outlets.  SIMPLE!  You should see that the lamp
doesn't work.  If it does, your LED on the power supply may be defective, but
that's doubtful, or the power supply may be bad.  Verify that the output is
xx VDC as stated on the case of the power supply.  (Since neither power supply
works, you should have determined what the problem is by now.)

If it should happen to be the Power connector on the Motherboard (99% doubtful),
you're going to be better off getting someone to look at it.  There are three
solder connections to the Motherboard, along with the Center pin that
is riveted to a metal buss that is one of the pins connecting to the
Motherboard.  I've had those riveted connections be loose and have 
CAREFULLY removed my Power Connector, by using the right tools, but
wouldn't recommend it unless you are WELL EXPERIENCED with lots of
time under your belt repairing circuit boards, as those circuit traces
are very thin and are easily destroyed by HEAT and incorrect solder
and desoldering methods.  So, save yourself the cost of a new Motherboard
by paying an experienced technician to do it for you.  Those folks
do exist.  Check your local Amature Radio Club (HAM's).


lk

---

### Post by QLee on 2010-08-08
bradmayne04, 
What the two previous posters seem to have missed is that the system is a desktop, not a laptop.

The power connector (from the power brick) on a laptop is often a source of problems but not on a desktop.

Unless you are experienced and confident in disassembling, the advice to take it to a qualified technician is still the best plan. You'd have to strip everything connected from the system to troubleshoot further and that shouldn't be attempted by inexperienced users. Someone will probably diagnose the problem for you at a reasonable cost. It is likely to be the mainboard but replacements for desktops are often not too expensive if the other components can be reused.

---

### Post by lkraemer on 2010-08-08
Well, I guess I should have searched for Hp Pavillion A1747C to make
sure it wasn't a laptop instead of making that assumption.

OK, If you look at this site:

[http://www.supernotebook.com/power-supply.php?psupart=2889](http://www.supernotebook.com/power-supply.php?psupart=2889)

you will notice the two left most connectors.  These ABSOLUTELY NEED to
be connected to your Motherboard.  That is easy enough to check.  Just
make 100% sure that both connectors fully seated and the connectors snap.
There are signals tied to the Motherboard from the Power Supply, so you
can't just plug it in the AC Mains and test it for correct voltages.
The Power supply also has to have a valid load on the +5 VDC Buss to
make it work properly.  That said, and everything plugged in correctly,
it should power up and allow you to test the voltages on an IDE type
Device Molex Plug that has only RED = +5.0 VDC, Black = Common, and Yellow = ~~ +12 VDC.
(The +12 may be Plus/Minus .5 volt of the specified.)  
[http://www.pcguide.com/ref/power/sup/func.htm](http://www.pcguide.com/ref/power/sup/func.htm) 

If it doesn't power up, then something could have happened to the Motherboard,
or some device connected to the Power Supply that is causing it to go into
Current Limit and shut down.  The easiest thing to do to test for this is to
remove all Power Plugs to all Devices except for one Floppy Drive, and the
Motherboard.  Then test again for the proper voltages.

Since you have tried another OEM Power Supply, and had both Motherboard
Power Plugs installed, it could be a faulty Motherboard.  The only real
easy way to go forward from here is by selective troubleshooting, and
that would mean swapping a suspect device to verify one device on a
working system

Power Supplies I've seen have no LED's or notification that Power is "ON"
other than the Fan running.  That is a tell tale sign.

REF:
[http://www.youtube.com/watch?v=rivoVzxwNtI](http://www.youtube.com/watch?v=rivoVzxwNtI)
[http://www.youtube.com/watch?v=IVFY98ozefw&feature=related](http://www.youtube.com/watch?v=IVFY98ozefw&feature=related)
[http://www.youtube.com/watch?v=yFRXDRxGMco&feature=related](http://www.youtube.com/watch?v=yFRXDRxGMco&feature=related)
[http://www.youtube.com/watch?v=q5XA8666hh4&feature=related](http://www.youtube.com/watch?v=q5XA8666hh4&feature=related)
[http://www.aitechsolutions.net/pchwtrblsht.html](http://www.aitechsolutions.net/pchwtrblsht.html)

lk

---

### Post by bradmayne04 on 2010-08-10
thanks for tryin to help. i am going to take a good look at this tomorrow night. i've been really busy lately.

---

