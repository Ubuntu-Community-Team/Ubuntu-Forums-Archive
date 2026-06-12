---
title: "Taking care of a laptop hard drive"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Salamancero on 2010-02-13
I bought a laptop hdd (Fujitsu,sata, 5400 rpm) and after nine months of use, I'm getting a warning from palimpsest disk utility that I have "too many bad sectors" and that I need to "back up and replace hard drive" as soon as possible.  I'm assuming that I'm the cause of my hard drive failing but I'm not sure what it is that I'm doing wrong.

Is it because I do not unmount my partition?  I have two major partitions.  I have one for Ubuntu and a larger one for music and movies.  I mount my "storage" partition but I don't unmount it when I switch off my laptop.  (I never thought it was necessary as it is the same disk)

Is it because of the temperature of hdd?  On Gnome sensor applet, it says 62 degrees Celsius but on palimpsest it says its 42 degrees Celsius.  

I used to have a windows partition but I deleted it a long time ago.  I haven't reformatted that part of my disk for some time now.  Is the disk utility program taking that partition into the equation?

Well, I'm planning to replace the hard drive soon but I'm wondering what I should do next time to prevent something like this from happening again. Thanks for the help or clarification! :)

---

### Post by samantha_ on 2010-02-13
> **Salamancero said:**
> I bought a laptop hdd (fujitsu,sata, 5400 rpm) and after nine months of use, I'm getting a warning from palimpsest disk utility that I have "too many bad sectors" and that I need to "back up and replace hard drive" as soon as possible.  I'm assuming that I'm the cause of my hard drive failing but I'm not sure what it is that I'm doing wrong.

Is it because I do not unmount my partition?  I have two major partitions.  I have one for ubuntu and a larger one for music and movies.  I mount my "storage" partition but I don't unmount it when I switch my laptop of off.  (I never thought it was necessary as it is the same disk)

Is it because of the temperature of hdd?  On Gnome sensor applet, it says **62 degrees celsius** but on palimpsest it says its 42 degrees celsius.  

I used to have a windows partition but I deleted it a long time ago.  I haven't reformated that part of my disk for some time now.  Is the disk utility program taking that partition into the equation?

Well, I'm planning to replace the hard drive soon but I'm wondering what I should do next time to prevent something like this from happening again. Thanks for the help or clarification! :)
if it IS actually 62 degrees, thats a bit too hot, but it may be related to the legendary palimpest bug. Thats still going.
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

---

### Post by audiomick on 2010-02-13
Hi.
You really shouldn't need to be unmounting partitions or anything along those lines.
What I know is hard on the drive in a laptop includes:
Mechanical shocks, like putting the laptop down hard, when the sytem is running.
Obviously too big a bump when it is off is also not good...

The laptop running too hot because the vents are often blocked (sitting in bed with the laptop on your lap, for instance)

Too much dust and dirt. Will also cause things to get too hot, if the vents get blocked and/or heat sinks get clogged up.

If you treat your laptop nicely, i.e. like the high precision machine it is, it should last well. My last one has 5 years as a tool used in setting up PA systems behind it, including being dropped twice and having the motherboard changed once. It now has a fault in the screen that is no doubt due to the whole case having become a bit "mobile", but the drive still tests old but ok.

---

### Post by Salamancero on 2010-02-13
Thanks for the info guys!  I really do take care of my laptop.  No bumps or spills or anything though I've been remiss lately with cleaning the ports.  The old guy kinda saw me through college and has been my workhorse for the past 5 years so it a was a big shocker on my part with palimpsest warning me that I screwed up my hard drive.  I read through the forum and I have no idea how to test my hard drive if it does have a problem or no but I'll definitely be trawling the forum to clear this issue.  Again, thanks.  :)

---

### Post by tgalati4 on 2010-02-13
smartctl will give you power-on hours.  How old is the drive and how many hours?

---

### Post by audiomick on 2010-02-14
I've used smartmontools with success
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

It is not difficult; in principle, you make sure the drive will support it and the function is enabled (probably is), run the check then go and get the results. It does not report automatically.

---

### Post by The Real Dave on 2010-02-14
62 strikes me as hot for even a laptop drive. Around 40-50 is normal I believe. So ya, the heat could have something to do with it, heat tends to kill computer parts, one of the reason why I try to keep my desktop as cold as possible, even to the point of burning out fans. 

Try cleaning your laptop. Go buy an airduster (can of compressed air) and open it up. You won't damage it so long as your careful. Clean out all the dust you can find, in heatsinks and around components. You'd be amazed at the stuff that builds up.

Lastely, buy yourself a laptop cooler/stand. It increases the amount of air under the laptop, and most even have fans, adding to the cooling. Keep your computer cool, and it'll last longer :)

Sorry I can't be of much help with your harddrive issue though...

---

### Post by audiomick on 2010-02-14
> **The Real Dave said:**
>  Go buy an airduster (can of compressed air)...
An alternative to the can of air is one of the squishy bulb blowers that you can get in camera shops for dusting off lenses with. The air stream is surprisingly strong, and it has the advantage that it never gets empty. I bought one about 10 years ago for about $10AUD and I am still using it.

---

### Post by Salamancero on 2010-02-16
> **tgalati4 said:**
> smartctl will give you power-on hours.  How old is the drive and how many hours?

About 9 months, give or take. Thanks for the tip on SMARTCTL. I'll be fooling around with the program in a few days. :)

---

### Post by Salamancero on 2010-02-16
> **The Real Dave said:**
> 62 strikes me as hot for even a laptop drive. Around 40-50 is normal I believe. So ya, the heat could have something to do with it, heat tends to kill computer parts, one of the reason why I try to keep my desktop as cold as possible, even to the point of burning out fans. 

Try cleaning your laptop. Go buy an airduster (can of compressed air) and open it up. You won't damage it so long as your careful. Clean out all the dust you can find, in heatsinks and around components. You'd be amazed at the stuff that builds up.

Lastely, buy yourself a laptop cooler/stand. It increases the amount of air under the laptop, and most even have fans, adding to the cooling. Keep your computer cool, and it'll last longer :)

Sorry I can't be of much help with your harddrive issue though...

Oh don't worry too much about it and thanks for the suggestions.  I've been rather paranoid about my laptop's hd so I'm planning to buy an external hard drive to serve as my backup for the meantime.  Regarding cleaning my laptop, I've been rather reticent about doing so as its plastic is rather brittle.  I let another pair of hands do some of that work before and I sorely regretted.  The man was a total brute cracked the bezel and a few other sections of the plastic.   I guess there's no going about it but to clean the thing again.   One thing I'm learning from this whole thing is that a celeron-m based laptop and a tropical environment isn't a good combination.

---

### Post by Salamancero on 2010-02-16
> **samantha_ said:**
> if it IS actually 62 degrees, thats a bit too hot, but it may be related to the legendary palimpest bug. Thats still going.
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

I read through a bit of that forum and I have to admit that I'm out of my depth in that place.  :)

---

### Post by tigerking615 on 2010-02-16
Fujitsu laptops get quite hot. Mine used to routinely reach 90 C when I was playing games or something. I realize this is bad, so I bought a cooling pad (this was a while ago). Right now it's on the cooling pad and I'm not playing anything, and it's 70 C.

I'm lucky enough to not have any hard drive failures, though, and I've had this for four years.

---

### Post by Salamancero on 2010-02-18
I now have a short term fix before i break open my laptop for its periodic dust up.  I got back my cooling pad and borrowed a mini industrial fan.  haha! :D

---

