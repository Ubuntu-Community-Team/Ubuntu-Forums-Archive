---
title: "got any ideas for VOIP for small business ?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by henry cow on 2010-07-28
I need to set up a phone service for a new small business. We will need a half-dozen voice mailboxes, with capacity to grow. Free would be great, cheap is good, but the $4K PBX we were quoted is way too much.

A live attendant will be on hand for some varying amount of time during business hours, otherwise I would like to be able to direct calls to one of a few voice mailboxes. Goodies like hold, transfer, conferencing, music-on-hold would be nice, but are not essential.

Can anybody advise me on the hardware and software that I need to accomplish this? I am "advanced" but not "expert" in the Microsoft universe, and struggling to get out of "beginner" in Linux.

Thank you very much!

---

### Post by lijcam on 2010-07-28
You could setup an Asterisks Box to do all this. Problem with Asterisks is its very difficult to setup for a new user. Watched episode 4 at asterikast. 

[http://www.asterikast.com/episodes.php]("http://www.asterikast.com/episodes.php")

It will show you how to setup basically everything you just asked for. 
Caveat: These guys are uber Asterisks gurus are can be hard to follow at times. 

If you want a GUI for Asterisks you could look at Trixbox [http://fonality.com/trixbox/]("http://fonality.com/trixbox/")
Guide (PDF) [http://dumbme.mbit.com.au/trixbox2/trixbox2_without_tears.pdf]("http://dumbme.mbit.com.au/trixbox2/trixbox2_without_tears.pdf")

I tried this once and found the amount of options and configurations confusing. But I much prefer the command line as at least in my setup. I only need to maintain two config files.

---

### Post by TBABill on 2010-07-28
A lot of what you want requires no PBX at all. The cable companies and telephone companies have telephone switches with advanced call routing capabilities. Multiple mailboxes, rollover numbers (call in on one number but roll to whatever you setup....so no busy signals until all lines in use), forwarding, hold (can even use a cheap phone set for some of these functions), etc. I was a tech for a major phone company and all these capabilities are easily done through basic services, not advanced PBX's with servers. Let their equipment do the work, not yours...saves you a ton, especially for the maintenance that you absolutely need unless you are qualified to troubleshoot and fix any failure within your PBX.

Cable companies offer similar services via VOIP. If you have Comcast or another major cable company in your area, try their business sales rep to see if they can do what you want WAY cheaper. And the quality is normally as good as, or superior to, a telephone company. And your voice signal does not utilize the Internet for transport if they have their own phone switch.

---

### Post by henry cow on 2010-07-28
TBABill - 

I appreciate your response, as an "insider"

We are looking to open an office in an industrial/commercial area, I am  not sure that cable is available there, although in general Comcast is  big around here (I have them for my personal TV, and am not particularly  impressed with their quality or service). For my personal home  computing, I have a DSL with Bellsouth, with a modem and router with 4  XP PCs on ethernet (2 dual-boot into Ubuntu) and an Apple laptop  wireless via Airport.

So, I am not afraid of having to screw around with something to make it  work, but ultimately it has to work properly 99%+ or we have a problem.  If we could avoid paying for multiple "business" phone lines and/or  complicated hardware sets, that would be great. 

In my imagination, if I could bring broadband into a strong (Ubuntu) PC  server and then send out lines to several thinner clients it would be  ideal. Even more perfect would be to have cheap phones plugged into  client PCs (rather than $200 sets with a dozen buttons on them), and the  ability to plug in at home somehow some miles away from the office.
 
This is a long wish list, and I can't expect to get everything, but we need to present a very "professional" face to the public.

Where should I go from here?

Thank you again.

---

### Post by TBABill on 2010-07-29
Check out this company. Cosmocom provides both on-site and hosted (probably ideal for a small company) solutions. I worked heavily with them for about 8 months to try to implement a multi-state (East coast) phone system for call centers remotely located to be linked together. They were great and may have a solution on the scale you are looking for. I'm not an employee and my contact with them ended in 2008. [http://www.cosmocom.com/Solutions/EndUsers.htm](http://www.cosmocom.com/Solutions/EndUsers.htm)
 
There are other providers as well. Research "hosted" contact center solutions, which will result in thin client setups on your end and all the hardware/software maintained on theirs. You'll just have usage/maintenance fees I think.

---

