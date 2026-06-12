---
title: "Control WiFi interfaces with Python"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by itamar-landsman on 2013-11-19
Hi,

I am starting work on a project where I want to create a dynamic Mesh between moving endpoints (in my case robots). my plan is to use three wifi sticks on each of the robots, every stick would be set to use one RF channel so that there would be minimum interference between the sticks.
My intention is that the robot would be able to make decisions as to where each stick will connect to and also if one or more of it's sticks need to become and AP to enable other robots to connect to it.

The networking part (i.e. routing protocols etc.) should be fine - handled by the [BATMAN]("http://en.wikipedia.org/wiki/B.A.T.M.A.N.") project. 

I am looking for a way where I can use python to collect data about available AP, connect to an AP and switch the stick mode between being a client to abecoming a serving AP.
searching around the net I could not find anything specific. Might anyone here have an idea?

Thanks,
Itamar.

---

