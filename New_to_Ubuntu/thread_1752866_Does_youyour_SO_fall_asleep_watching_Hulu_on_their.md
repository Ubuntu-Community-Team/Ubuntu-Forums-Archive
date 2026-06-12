---
title: "Does you/your SO fall asleep watching Hulu on their laptop; Flash pegging CPU"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-08
Sorry I couldn't think of a shorter thread title.

Anyway I kinda have an open ended problem that's of really no serious priority and just thought I'd toss it to the crowd to get some wide variety of ideas about how best to approach and come up with a working solution.

My fiancé enjoys watching TV/Movies as she falls asleep.  This can take it's toll on the CPU (particullarly on the heatsink fan because the fins collect dust and get blocked and then the thing is noisy).  This doesn't bother me so long as it's being put to good use, but if you've ever used Hulu or any website that has flash on it, you may notice that even if it may not appear to be actively rendering anything, it might actually rendering the hell out of something that's not even moving.  So there will be nights I'll come home and walk in to the bedroom after she's asleep and her show is finished, the screen has even gone to sleep, but the heatsink is blowing full blast all because Firefox is still sitting on Hulu.

So I'm looking for idea about ways to approach this problem in a smart way.  The first idea I had was to have some kind Sleep Timer (to kill Firefox or perhaps just Flash alone?) after either a certain fixed amount of time (just like a sleep timer on a TV that has one... do they still have sleep timers on TVs?  I never use them anymore so I don't know) or perhaps a certain amount of time based on inactivity if that's something easy to do.  But then I thought, what if she was shopping for something in a separate tab in firefox, hasn't book marked it...  I suppose you could just make sure it remembers previous tabs when being closed right?  But she might not want it to do that; do you do that?  I don't even do that or would want to do it really; just makes for more house keeping type work, needlessly closing times you'd rather close in groups.

I digress.  I'm heading to bed now but just wanted to toss this idea out as I was about to go to bed and walked into a room with noisy laptop.

---

### Post by rosencrantz on 2011-05-08
Did you consider using acpi event scripts? 
There should be a number of examples in your /etc/acpi/events directory.
I'd try to put in the following switches (in order not to endanger your pre-marital felicity) in the script called under action:
-desktop inactivity threshold (that's what acpi scripts are meant to do anyway)
-check for high cpu or memory usage (or long running times)  by piping top to a file (top -n 1 |grep firefox > somefile.txt).
-how about a pop-up message that allows your SO to cancel killing firefox during a 30 second grace period?
zenity --timeout should do it, or maybe notify-send (never tried that one).

---

