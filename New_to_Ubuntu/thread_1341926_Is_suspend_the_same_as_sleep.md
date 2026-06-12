---
title: "Is suspend the same as sleep?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-30
To do the ubuntu equivalent of windows' sleep, you select "suspend" right?

---

### Post by lotharmat on 2009-11-30
That is correct - Suspend maintains RAM
Hibernate writes RAM to disk

Suspend uses more power than hibernate so will drain a battery quicker

Hope this helps

---

### Post by Space-Wolf on 2009-11-30
Thanks, that's exactly what I needed to know.

---

### Post by 3rdalbum on 2009-11-30
If it's supported on the hardware, the closest equivilant to the new Windows "sleep" command is:

```
sudo pm-suspend-hybrid
```

(or, as I like to call it, "hybridation").

It hybernates, then suspends.

Unfortunately my hardware doesn't support it so it does nothing.

---

### Post by sal_m on 2009-12-07
Any ideas on how to get the pm-suspend-hybrid to be the default rather than pm-suspend?  

I would like to setup my wife's laptop to pm-suspend-hybrid in case she can't get back to whatever she was working on, but I don't see an easy way to make this happen when she closes the lid in the power manager.

---

### Post by The_Pirate_King on 2009-12-07
I actually have a few questions relating to this. 

Is there a way to figure out how many amps suspend uses in comparison to hybrid? 

and

For some reason, my laptop does nothing when I close the lid with Ubuntu running, even though power manager says it's supposed to hibernate.  Is there any known fix for this?

---

### Post by tmy123 on 2010-01-01
> **lotharmat said:**
> That is correct - Suspend maintains RAM
Hibernate writes RAM to disk

Suspend uses more power than hibernate so will drain a battery quicker

Hope this helps

Hibernate don't use any power because it's like power off.

> Is there a way to figure out how many amps suspend uses in comparison to hybrid? 
The same.
Hybrid takes longer because it's hibernates the system too.
If you have a battery it makes no reason to use hybrid.

---

