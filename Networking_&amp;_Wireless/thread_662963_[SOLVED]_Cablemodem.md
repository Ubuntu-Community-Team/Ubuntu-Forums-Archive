---
title: "[SOLVED] Cablemodem"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Bruce M. on 2008-01-09
Why is my computer downloading 10-13 k/s even when "Wired Network Connection" is turned off?  Come to think of it, why is it doing the same when "Wired Network Connection" is on but I'm not doing anything with the computer? ie: it's sitting idle.

As you can see from the two images, I've received 321 MiB (Mega Bytes or Mega Bits?) of info in 6 hrs 39mins of being online.

These images were taken 2 minutes apart, during the 30 minutes or so of testing things, with my "Wired Network Connection" turned off.  And during that time, my conkyweather didn't work, I couldn't collect email or come here with Firefox, but the k/s kept coming, in fact 2 MiB came down in the two minutes between screenshots. All this with an IP addy 0.0.0.0

Any ideas of what this is and how to stop it, or if I should even worry about it?
Turning off the computer is not an option.  :lolflag:

I know that my ISP considers me online even if I turn the computer off, like I do at night, without physically unplugging the Cablemodem, as the PC light is always blinking (even now), and the Power and Cable lights are always on solid. The Data Send and Data Receive lights are off (now too) until I actually send receive something.

*To restate my questions:*

Why is my computer downloading 10-13 k/s even when "Wired Network Connection" is turned off?  Come to think of it, why is it doing the same when "Wired Network Connection" is on but I'm not doing anything with the computer? ie: it's sitting idle.

Any ideas of what this is and how to stop it, or if I should even worry about it?

Thanks for listening to me.
Bruce

---

### Post by Anduu on 2008-01-09
I see the same thing with my network as well....

Since I have no bandwidth limits or anything I pretty much don't worry about it
I have just been chalking it up to the modem and the isp "chitchatting"

I would be interested to know what is actually going on in the background as well.

---

### Post by Bruce M. on 2008-01-17
> **Anduu said:**
> I see the same thing with my network as well....

Since I have no bandwidth limits or anything I pretty much don't worry about it
I have just been chalking it up to the modem and the isp "chitchatting"

I would be interested to know what is actually going on in the background as well.

Guess there isn't an answer out there.
Mean time I keep racking up hundreds of MB a day at 14-20 k/s

For example: Uptime this session: 1h 27m  Down: 107MiB   :(

---

### Post by Anduu on 2008-01-18
I installed and configured bandwidthd a while back and in my case I am seeing a constant flow of UDP traffic...see screenshots

How to track where it is coming from I don't know but I suspect it is betwen my network and my ISP.

---

### Post by Bruce M. on 2008-04-06
Hi Folks,

When I finish here I'll be marking this thread [Solved] after all I think everyone will agree. In fact it seems like it makes this question rather silly for the asking.  :lolflag:

It is the ISP talking with the "Cablemodem", just look at your setup.

A cable comes into the house, and there is a splitter in some cases, one wire to the TV, the other to the "Cablemodem" at this point there is a cable running to the computer.

Now, while the computer is off, the ISP is still "chatting" (for the sake of a word) with the modem that is hooked up to their cable.

It's (probably) not something that you'd have to worry about even if you did have a limit.

Have a nice day folks.
Bruce

---

