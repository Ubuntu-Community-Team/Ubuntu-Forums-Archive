---
title: "Slow boot"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Teatro on 2009-03-18
I just installed Intrepid Ibex on an AMD 64 system last week. (I'm new to linux).  Most things seem to work pretty well, such as they are, but it boots slower than molasses. I have the dual boot set up, and windows launches well (strangely, it seems to launch quite a bit faster than before I installed Ubuntu...). Ubuntu is very slow, though, much slower than Windows, which shocks and dismays me. Watching the boot messages, the problem seems to be that it is querying a bunch of addresses to see if ata.oo1 or some such is there, and waiting for the location to time out. It does this a dozen times at different addy's, then gives a timeout message followed by a message to the effect that the device status is {RDY} or some such. Anybody know what's going on and how to fix it? Everything else boots as fast as the screen can scroll.

thanks,
Teatro

---

### Post by DaveG825 on 2009-03-18
I've seen a lot of people report problems with Ubuntu's speed on a Windows/Ubuntu dual boot. Still, your problem seems pretty strange... Are there any other details worth noting about your dual boot setup?

---

### Post by skymera on 2009-03-18
I run 64BIT Ubuntu 9.04
I boot to a full desktop in about 16-18 seconds i guess. (Though i have tweaked almost every bit of Ubuntu to get it that quick)

Ubuntu 8.10 was slow for me also, it's just a bad version.

---

### Post by Teatro on 2009-03-21
Um, thanks, I guess... all I can add is that the messages take the form of 

[   868069] res 40/00:00:00:00/00:00:00:00 Emask 0X4 (timeout)

and 
[   868069] ata1.00 status { DRDY }


there are a whole bunch of them, each taking ten to twenty seconds to process, then the system mounts external devices and does twenty or so other things so fast I can't even see what it's doing and the log in comes up.

Does anybody know what this actually means?

---

