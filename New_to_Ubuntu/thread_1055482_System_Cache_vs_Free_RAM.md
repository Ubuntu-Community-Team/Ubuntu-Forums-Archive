---
title: "System Cache vs Free RAM"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by icanfly0307 on 2009-01-30
Hi,
   I've just noticed the output of the command [FONT="Courier New"]free -m[/FONT] and it shows this:

[FONT="Courier New"]    total       used       free     shared    buffers     cached
Mem:           248        244          3          0          0         74
-/+ buffers/cache:        168         79
Swap:           86         34         52[/FONT]

So, with the System Cache, I have 78MB of free RAM, but without the System Cache, I have only 3MB of RAM...

What exactly does this mean? Do the caches count as free memory and what are they used for? Are they just a waste of resources or is there anyway to use them like "regular" RAM? Thanks for your suggestions... :)

---

### Post by snova on 2009-01-30
> **icanfly0307 said:**
> ```

              total       used       free     shared    buffers     cached
Mem:           248        244          3          0          0         74
-/+ buffers/cache:        168         79
Swap:           86         34         52

```

[noparse]```

```[/noparse] tags preserve indentation. ;)

> What exactly does this mean? Do the caches count as free memory and what are they used for?

Yes, it's free memory (essentially). You've got 250 MB of memory, about 75 of which is being used as buffers/cache. Taking it into account, all but 3 MB of memory is being used; ignoring it, only 168 is being used.

> Are they just a waste of resources or is there anyway to use them like "regular" RAM? Thanks for your suggestions... :)

It is "regular" ram. It's just being used as a disk cache. If more memory is called for, they will be shrunk as needed to accomodate.

And it's by no means a waste of resources- if nothing were cached, disk operations would be very slow. So the bigger these are, generally, the better.

---

### Post by jerome1232 on 2009-01-30
Basically free ram is ram wasted.

What isn't used by applications is used as a file cache, anything used is cached in hopes that it'll get accessed again (and be faster since it's in ram now)

If more space is needed for applications cache will be dropped for the application that needs the ram. So in a sense what's cached is "free ram".

---

### Post by icanfly0307 on 2009-01-30
Thanks guys, that solved my question.

Oh, and I'll remember to use the "[code /code]" tags next time. ;)

---

### Post by SunnyRabbiera on 2009-01-30
This is also aided by swap too, a swap partition acts like an extra memory card to make sure overload is minimum.

---

### Post by icanfly0307 on 2009-01-30
I'm just trying to keep away from SWAP. I'm sure that I can fit my entire os in RAM since I'm using LXDE and not GNOME.

---

### Post by icanfly0307 on 2009-01-30
Oh yeah, one more thing...

If the buffers will be resized as needed, why does my computer use swap everytime I load a number of overabundant apps? Shouldn't it reduce the buffers and use the resulting free ram? Thanks again.

---

### Post by SunnyRabbiera on 2009-01-30
> **icanfly0307 said:**
> I'm just trying to keep away from SWAP. I'm sure that I can fit my entire os in RAM since I'm using LXDE and not GNOME.

Yeh on lower ram machines LXDE is pretty decent.
But if swap is ever used dont worry about it :D

---

### Post by jerome1232 on 2009-01-30
> **icanfly0307 said:**
> Oh yeah, one more thing...

If the buffers will be resized as needed, why does my computer use swap everytime I load a number of overabundant apps? Shouldn't it reduce the buffers and use the resulting free ram? Thanks again.

That's a setting called "swappiness" if ram get's maxed out the kernel will start swapping out application data to maintain some  file cache. I believe Ubuntu is set to "60" by default meaing it does this rather aggressivly. If you have alot of ram it's safe to set this value lower to favor not swapping. Personally if your not experiencing performance degradation due to the swapping I wouldn't bother with it.

--edit-- I thought this was a great explanation [http://lwn.net/Articles/83588/](http://lwn.net/Articles/83588/)

---

### Post by blueridgedog on 2009-01-30
> **jerome1232 said:**
> Basically free ram is ram wasted.



+1  Great way of putting it!

---

### Post by icanfly0307 on 2009-01-30
Thanks everyone! I really appreciate your help... :D

---

### Post by peterquistgard on 2009-02-18
Hi Guys. I am using 4GB of ram. I use the server kernel, so that I can actually use all 4GB. My output from ```
free -m
``` looks like

             total       used       free     shared    buffers     cached
Mem:          4053       2487       1565          0        709       1267
-/+ buffers/cache:        510       3542
Swap:          972          0        972

Now if free memory is wasted memory, how can I make use of my free memory in normal use?

(I write a lot of heavy numerical code so the 4GB gets used for that, just not normally).

---

