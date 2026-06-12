---
title: "PC won't boot... Not good!"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by ydnom89 on 2009-10-31
So, a little backstory. I got this ancient HP XE783 that my parents let me take off to college when they upgraded. For the unitiated, this particular model was originally specced to run Windows ME, so this machine has been around for about 9 or 10 years. Throughout its existance, my parents have upgraded particular parts, the power supply and the CD drive. Nothing too special right?
I took it away to college and decided to reinstall Windows XP. To be save I popped out the CMOS battery and put it back to reset the BIOS settings. After I put the case back on and turned the power supply on, it instantly booted, before I pushed the soft power button in the front. I installed XP and played around a little bit, then shut it off through the software. After that, the fan kept running at full power, so I decided to flip off the power supply in the back. The kicker now is that this arcane monster won't boot. Any ideas? 
When I begin to get money, the first thing I'm doing is getting a new case. the HE783 is a monster to get around in and I cry a little on the inside whenever I open it.

---

### Post by stinger30au on 2009-11-01
ok the pc wont boot

so what *EXACTLY* happens

does it beep??

does any thing come up on the screen or does it stay black??

does it give you any errors???


please elaborate so we can help

---

### Post by yanceypd on 2009-11-01
There may be a couple of pins you can jump on the motherboard to get it to boot.  Look for some Manufacture id on the board and see if you can google it.  T%hen in the bios setup make sure power features are setup.  You may have to flash the bios.  Good luck on getting the info.

---

### Post by jrrader on 2009-11-01
Not really sure why this is on the Ubuntu forums, but sounds to me like your power supply went out.  Common problem.  You can probably get a new PSU for about 20 dollars (but you could also get a refurbished, newer computer for around 100 from ebay.  My dad buys them for his work and they aren't bad for general computing.)

---

### Post by cascade9 on 2009-11-01
I would try popping the BIOS battery out or using the CMOS clear jumper/button before trying a new power supply. It might have corrupted.

Edit- froma quick look, the HP XE783 doesnt use a standard ATX power supply. Its a bit smaller than standard, so if you just go out and buy a power supply there is a good chance it wont fit.

---

### Post by ovroniil on 2009-11-01
I am not sure why on earth you write this thing here? :-k This is not a Ubuntu related problem. You are using Windows! And this forum is for LINUX!!

If you would provided the specification of your computer then I may be suggest you to use Xubuntu.

---

### Post by cascade9 on 2009-11-01
@ ovroniil- point. But theres no real harm in asking, and is the ubuntu forums help, then thats good. Linux in general needs all the friends it can get, and if helping someone gets that then this is A Good Thing. 

BTW- Celeron 700, 64MB of RAM, 30 GB Hdd standard. Xubuntu would be slow...at best....with that, but I would guess it has to have a bit more RAM, WinXP + 64MB = 'OMG the swap disc gets hit so often it sounds like bolts being shaken in a coffee tin' 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph06558&lc=en&cc=us&dlc=en&product=81921](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph06558&lc=en&cc=us&dlc=en&product=81921)

---

### Post by ovroniil on 2009-11-01
How about Minimal Ubuntu + LXDE ??

---

### Post by QLee on 2009-11-01
[QUOTE=ydnom89]So, a little backstory. I got this ancient HP XE783 that my parents let me take off to college when they upgraded. For the unitiated, this particular model was originally specced to run Windows ME, so this machine has been around for about 9 or 10 years. Throughout its existance, my parents have upgraded particular parts, the power supply and the CD drive. Nothing too special right?[/QUOTE]

Does it still have only 64 meg RAM? I would expect XP to be real dog on a system with so little resources.

[QUOTE=ydnom89]I took it away to college and decided to reinstall Windows XP. To be save I popped out the CMOS battery and put it back to reset the BIOS settings. After I put the case back on and turned the power supply on, it instantly booted, before I pushed the soft power button in the front. [/QUOTE]

Humm, shouldn't have been any need to reset CMOS but since you did, that's likely the reason that the unit now start booting upon restoration of power after an outage, that's probably the default.


[QUOTE=ydnom89]I installed XP and played around a little bit, then shut it off through the software. After that, the fan kept running at full power, so I decided to flip off the power supply in the back. The kicker now is that this arcane monster won't boot. Any ideas?[/QUOTE]

Just to confirm, you did turn it back on, eh?

Try to boot the XP install disk and choose "install" again, this should eventually lead to a place where you can choose "install" or "repair", try the repair. Might work, might not, probably is worth trying.

 
[QUOTE=ydnom89]When I begin to get money, the first thing I'm doing is getting a new case. the HE783 is a monster to get around in and I cry a little on the inside whenever I open it.[/QUOTE]

I advise not spending too much on a case for a mainboard that old. Some of the mini-ITX systems available these days are pretty cheap and you don't have to buy the most expensive to obtain better performance than a socket370 700MHz celeron. Those mini_ITX have a small footprint which can be helpfull in a small dorm room too.

---

### Post by ydnom89 on 2010-02-28
Oh, an update. I completely scrapped everything on the old build and got brand new stuff, which runs beautifully, so I suppose this thread could be considered closed :P. 
PS - I am pretty sure I know what I screwed up: I never reconnected the power switch back to the mobo, or any of that other stuff in that little 2 x 4 pin connector grid!

---

