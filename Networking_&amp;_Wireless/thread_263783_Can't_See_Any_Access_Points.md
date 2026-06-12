---
title: "Can't See Any Access Points"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by evillawngnome on 2006-09-23
Thursday night, i could see my wireless access point, and then friday i couldnt. I reset my router and, long story short, even went out and replaced the router. Im still having the problem.

I have a broadcom 4318 in a compaq presario v2000. Does anyone have any ideas?

---

### Post by happy-and-lost on 2006-09-24
Where are you looking for it? Network-manager or wifi-radar?

If you're using network-manager, I recommend trying to connect using wifi-radar (sudo apt-get install wifi-radar)

---

### Post by NetworkGuy on 2006-09-24
I don't have a broadcom card, but did you verify the internal kernel module (bcm something) was blacklisted?  It's possible it's conflicting with you NDISWrapper

---

### Post by evillawngnome on 2006-09-26
After spending an inordinate amount of time on chat with tech support at linksys. You can read the transcript here ([http://www.evillawngnome.com/2006/09/25/id-ten-t-error-id10t/](http://www.evillawngnome.com/2006/09/25/id-ten-t-error-id10t/))

You can see i lied to him about my OS, i wasnt going to listen to him tell me that linux wasnt supported. Anyway, after all that, i ended up getting a new router just to see if it was the router. TUrns out, we were BOTH right: The problem wasnt the laptop OR the router, per se, it was the fact that every router in my apartment building was on the same channel. Why it decided to be  an issue that day, i have no idea. But after playing with a few different channels, i found one that works realiably.

THanks for the suggestions guys.

---

