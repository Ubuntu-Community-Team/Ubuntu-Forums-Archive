---
title: "KDE crashing.."
date: 2011-03-24
forum: New to Ubuntu
---

### Post by .py on 2011-03-24
Hello ubuntuforums,
well, as the title says, KDE crashes A LOT!!
and its really starting to become annoying..
it usually happens in two ways, one is that everything disappears
and it just shows me a blank screen, the other is that the desktop freezes, so my desktop is still there but i can do nothing.
So is there anyway to at least minimize those crashes..?
Thanx. :)

---

### Post by Old *ix Geek on 2011-03-24
KDE shouldn't be crashing--this isn't windows. :lolflag:

So--and this is purely a guess--I'm thinking there's something wrong with your installation. Either some files are missing or corrupted, or perhaps you somehow failed to install everything that should be installed, or it's possible you're using an incorrect driver (graphics card, for example).

There are different ways you can go about this, depending on your preference. If it's a relatively new installation that you haven't invested a lot of time in (customizing, installing apps, etc.), my suggestion would be to start over. Do a fresh install, formatting the / partition before putting the OS on it again. If you followed the preferred protocol of placing your OS on / and having a separate /home partition for your data, you can reinstall the OS without losing your data--just be *SURE* you don't tell the installer to format /home!

If that's not the route you want to go, then I'd start out by looking at which drivers you're using and switch them up to see if that solves the problem. I'd also go into Synaptic and search for everything related to **kubuntu** and/or **kde**; look at the search results and see if everything's installed that ought to be. This involves looking for files/apps that seem like they SHOULD be installed for Kubuntu to work correctly, NOT extraneous stuff (like extra cursors or text editors).

---

### Post by .py on 2011-03-25
Thanx a lot Old *ix Geek, for your time, really appreciate it.
well, i don't think there is anything wrong with the installation,   its more likely a drivers issue, because i haven't spend a lot of time on getting the right ones, actually i haven't spend any.
btw: i have a Toshiba Satellite Pro L450, with only Kubuntu 10.10 running on it, and graphics card is Intel, any advice?
and i'll see what i can do at Synaptic, Thanks again. :)
-----------
P.S: i'm an Emacs fan..:wink:

---

### Post by mastablasta on 2011-03-25
perhaps:
 
- the graphics card/chip is dying
- computer is overheating and causing freezes
 
-----
 
if we can exclude these two, then it might be possibel to upgrade to newe KDE. perhaps that culd solve the problem.
 
KDE carshes on me as well occasionally, but not fataly/completely. i can still work normaly with it.

---

### Post by Dutch70 on 2011-03-25
You may also want to try disabling desktop effects & see if that fixes your problem. 

To see exactly which Intel graphics card you have, run the following command in a terminal & paste the output into your next post.
```
lspci
```

---

### Post by mastablasta on 2011-03-25
> **Dutch70 said:**
> You may also want to try disabling desktop effects & see if that fixes your problem. 
 

 
I think they get disabled automaticly in KDE if it crashes.

---

### Post by .py on 2011-03-25
> **Dutch70 said:**
> 
To see exactly which Intel graphics card you have, run the following command in a terminal & paste the output into your next post.
```
lspci
```
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by Dutch70 on 2011-03-25
> **mastablasta said:**
> I think they get disabled automaticly in KDE if it crashes.

Yeah, that's just a little too late isn't it? ;)

 If disabling the desktop effects permanently stops the "crashes". Then it's probably the graphics card. In which case their may be a workaround.

.py I'm not familiar with that exact video card, but does disabling the desktop effects before it crashes prevent it from crashing? 
I think that would be helpful information for anyone that tries to help.

---

### Post by .py on 2011-03-25
> **Dutch70 said:**
> Yeah, that's just a little too late isn't it? ;)
.py I'm not familiar with that exact video card, but does disabling the desktop effects before it crashes prevent it from crashing? 
I think that would be helpful information for anyone that tries to help.

No i've tried it before, disabling the Desktop effects doesn't seem to make any difference.

---

### Post by Dutch70 on 2011-03-25
Well, I had hoped I would have better info for you. 

 I was having the same problem with Ubuntu & Kubuntu. Disabling the effects stopped mine from freezing & then post #22 of the link in my sig allowed me to use Compiz on both. It has worked with other Intel cards, but not all of them.

Maybe someone else will have a solution.

---

### Post by .py on 2011-03-25
Thanks a lot for your time Dutch70.
Anyway i'll try to Disable effects (i have that done by now), and use compiz(i'll follow the instructions in this #22 post)
i'll give it a couple of days, and then post back.
thanks again

---

