---
title: "stay power off"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by expatCM on 2011-03-29
I am having a problem getting a computer to stay powered off.

With cron I can use either halt - p or shutdown now -h and either works in that the system will be shut down.  But the system does not close ...  it immediately reboots so there is no power off period at all.

Where do I look to work out what has gone wrong?  The cron event works so it is keeping the machine off I miss.

I should mention that this has just started being a problem on swapping in a new motherboard whilst an RMA is being processed,

---

### Post by Dark_Stang on 2011-03-29
That's a hardware problem, not a software problem. Possibly a fault power or reset switch. Or maybe you've got some of your jumpers hooked up incorrectly on the motherboard. And I hate to bring this up since you've already swapped out boards... but it could also be your new motherboard. If you've got another bad board I'd be wary of the power supply.

---

### Post by expatCM on 2011-03-29
thanks for your input and ...  oh dear ...  you are confirming what was in the back of my mind.

Can there be any possibility that this could be me not getting any of the bios settings correct ...  some of them are reasonably obscure and reading the manual is a reasonable waste of time given the quality of documentation?

---

### Post by Dark_Stang on 2011-03-29
> **expatCM said:**
> thanks for your input and ...  oh dear ...  you are confirming what was in the back of my mind.

Can there be any possibility that this could be me not getting any of the bios settings correct ...  some of them are reasonably obscure and reading the manual is a reasonable waste of time given the quality of documentation?
I've never seen a BIOS setting to attempt power on at all times on a home machine, only on rack servers. It is possible for a manufacturer to do this to a motherboard intentionally, but I can't think of any reason to do it on a home machine.

---

### Post by collisionystm on 2011-03-29
shutdown -P 0

shutdown capital P zero

---

### Post by expatCM on 2011-03-30
thanks for the shutdown -P 0 suggestion, I will give it a try.  I had a look at man shutdown and cannot find the 0 switch though but I guess it means "after zero minutes" ....

---

### Post by collisionystm on 2011-03-30
yes , shutdown -P (power off) 0 meaning 0 minutes, seconds...IMMEDIATELY!

---

### Post by JohnLM_the_Ghost on 2011-03-30
Other funny things to do...

After you've checked the wiring on board is correct...try removing ethernet cable - Wake-on-LAN setting could be buried somewhere in BIOS setup.

And does your PC actually shutdown for few (5 or more) seconds, or just keeps rebooting? Does it spuriously boot up if you do a "hard poweroff"?

---

### Post by msandoy on 2011-03-30
This sounds like a BIOS feature I use on my server.(Not a rack server, but an AsusEee box.) Since I'm away for months at a time, I have this feature enabled in BIOS, so when there is a blackout, the computer automatically starts when power returns. I have only had my server for a year, so I have actually never tried to power it down the way you describe. I have always just rebooted when there have been kernel updates. I'm checking what the feature is called. Can't seem to remember off the top of my head. My first impression is that your MB is OK.

---

