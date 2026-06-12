---
title: "Using multiple NICs as a 'hub'"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by BullwinkleJones on 2008-08-11
I've got a rather odd request.  I'd like to use my Ubuntu box as a makeshift 'hub'.  I have 25mbit internet service, but only a 10mbit hub, kinda wasting my money a bit.

I have numerous NICs, and was hoping that I could maybe use them as a hub somehow?  Is this possible?  Thanks!

---

### Post by Iowan on 2008-08-11
I'm notorious for doing things the hard/cheap way - just for the experience.  You could probably make Ubuntu into a router or a bridge, but with 10/100 switches going for $10-20, that would be kinda wasting your computer a bit. (Just my opinion).

---

### Post by BullwinkleJones on 2008-08-11
I know I can get a cheap hub, I actually work at a computer store... but this is more than just a way to make it work without buying anything...  I'm trying to learn more about Linux etc, and this kind of strange tweaking should help me learn .:)

---

### Post by cariboo on 2008-08-11
Yes you can use as many nics as you've got slots for. have a look at this howto here:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Jim

---

### Post by BullwinkleJones on 2008-08-11
> **cariboo907 said:**
> Yes you can use as many nics as you've got slots for. have a look at this howto here:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Jim

Thanks, Jim... But this doesn't quite do what I want.  I have four NICs, and three computers.  What I want is the Ubuntu box to be transparent.  I want it to appear to the computers like they're connected thru a basic hub to my cable modem.  So that they pass-through DHCP requests, etc.

---

### Post by Iowan on 2008-08-12
[Here]("https://help.ubuntu.com/community/NetworkConnectionBridge") is an article about a network bridge - based on Kubuntu 6.06, but might have some useful hints.

---

