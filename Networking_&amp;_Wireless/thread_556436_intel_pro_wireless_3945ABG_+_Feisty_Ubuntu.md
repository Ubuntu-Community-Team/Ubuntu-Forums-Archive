---
title: "intel pro wireless 3945ABG + Feisty Ubuntu"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by piuma12 on 2007-09-21
Hello friends,
i've just installed on my laptop Ubuntu Feisty (last version):
i have a intel pro wireless 3945ABG, which ubuntu seems to
detect and activate. Infact, on the Network Manager, i can
see the list of wireless networks in my neighborhood. But
when i try to connect, it asks for WEP key and when i type
it ... it doesnt connect. Also when i try to connect to a free
network (there is one here), it does not go on.
So the problem is that my box notices networks, but can't
connect them....

Seems like it does not give me an ip address.

What should i do, in your opinion?
Someone has this configuration  (feisty+intel pro wireless 3945abg) ?
 
**THANKS **for your help guys... :-)


Regards,
Jack

---

### Post by piuma12 on 2007-09-21
:confused:

---

### Post by Zorael on 2007-09-21
You're running DHCP, I imagine. You could try switching to a static IP configuration and see if that helps, and/or you could try switching from the standard network managers to [wicd](http://wicd.sourceforge.net).

Some 3945ABG cards are behaving strange, actually. Some get it to work effortlessly, some manage to connect after putting in considerable effort (at each connect; it also disconnects randomly), some don't manage at all, left with a recognized interface with a correctly loaded driver that still doesn't work. I've had one card that, like the first-mentioned one, Just Worked™ out-of-the-box, and now this second one that doesn't work at all.

Since it works for some, it's often interpreted as user error (i.e, "my wireless doesn't work at all, tried everything" vs "it works for me, no issues whatsoever, have you tried turning it off and on again"), and left at that.

And I don't know nearly enough about programming and debugging to help with remedying it; I can but raise awareness.

---

### Post by piuma12 on 2007-09-22
gonna try wicd :(

---

