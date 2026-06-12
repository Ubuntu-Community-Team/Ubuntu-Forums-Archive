---
title: "Ubuntu thinks I have 256 of Memory when I have 512!"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by playing_with_matches on 2010-01-20
Lately, ever since upgrading to 9.10, my machine has been running so slow that it's becoming unusable.  I checked the system info, and ubuntu apparently thinks i have 256 mb of ram when I have 512... 

What gives?  I've been using ubuntu since 6.10 and never had a problem.

---

### Post by Finalfantasykid on 2010-01-20
Maybe check in your BIOS to see how much memory it says you have.  Maybe your memory has been damaged.  

Or maybe if you have shared memory, maybe somehow, the amount of memory allocated for graphics is 256 as well, which would explain the loss of the 256MB.

---

### Post by playing_with_matches on 2010-01-20
bios says I have 512, as does windows.

---

### Post by presence1960 on 2010-01-20
> **playing_with_matches said:**
> bios says I have 512, as does windows.

Do you have a dedicated video card or an onboard graphics GPU on the motherboard? If you have an onboard GPU for graphics some of your RAM is allocated to be "shared" with that.

---

### Post by majickmann on 2010-01-20
I know this may sound lame, but why do you think that ubuntu thinks there is only 256M?

There are a number of ways to "see" the memory.  Knowing that may shed some light on why...

Hope this helps...
:-)
--majickmann

---

### Post by presence1960 on 2010-01-20
> **majickmann said:**
> I know this may sound lame, but why do you think that ubuntu thinks there is only 256M?

There are a number of ways to "see" the memory.  Knowing that may shed some light on why...

Hope this helps...
:-)
--majickmann

open a terminal and run ```
free -m
```

---

### Post by playing_with_matches on 2010-01-20
I do have a dedicated graphics card.

I found out by going to the System Monitor -> System

Weird.  I rebooted a few times, and suddenly it says I have 497 now.  Good enough for me.

free -m now states i have 497 since a few reboots.

---

### Post by louieb on 2010-01-20
What kind of PC? Some PCs have a known memory slot problem such as the IBM T30.

---

### Post by playing_with_matches on 2010-01-26
Hey. I think I may have found the source of the problem (maybe).

Does computer memory ever go bad?  I noticed after a few times, my BIOS was saying I only have 256 (even though it's been 512 for the past 7 years... heh)

Anyways, I swapped in a different 512mb stick that I had in a different PC, and not only does my BIOS register that it is 512, ubuntu is going a whoooole lot faster now.  

I guess if I have problems with this memory too now, then it's the slot?

---

### Post by Methuselah on 2010-01-26
You can test the memory with memtest86 -- comes on the LiveCD.

---

### Post by cascade9 on 2010-01-27
> **playing_with_matches said:**
> Hey. I think I may have found the source of the problem (maybe).

Does computer memory ever go bad?  I noticed after a few times, my BIOS was saying I only have 256 (even though it's been 512 for the past 7 years... heh)

Anyways, I swapped in a different 512mb stick that I had in a different PC, and not only does my BIOS register that it is 512, ubuntu is going a whoooole lot faster now.  

I guess if I have problems with this memory too now, then it's the slot?

I've had issues with slots going bad. Its rare, but it does happen.

---

### Post by freak42 on 2010-01-27
I also had once problems with a memory slot going bad (not the memory itself but the plug to the mobo), which resulted in the memory either showing up and working or not beeing there at all (weird, I know).

---

### Post by cascade9 on 2010-01-27
> **freak42 said:**
> I also had once problems with a memory slot going bad (not the memory itself but the plug to the mobo), which resulted in the memory either showing up and working or not beeing there at all (weird, I know).

Weird...but I can beat it. :) 

I've got a motherboard here, three ram slots. Memory in slot 1, boots, doesnt detect the RAM. Memory in slot 2, boots, memory detected fine. Memory in slot 3- boot failure. 

Took me a while to figure that one out, as I tended to run the memory in slots2+3 cause they give the CPU just that bit more breathing room.

---

### Post by halitech on 2010-01-27
> **playing_with_matches said:**
> Hey. I think I may have found the source of the problem (maybe).

Does computer memory ever go bad?  I noticed after a few times, my BIOS was saying I only have 256 (even though it's been 512 for the past 7 years... heh)

Anyways, I swapped in a different 512mb stick that I had in a different PC, and not only does my BIOS register that it is 512, ubuntu is going a whoooole lot faster now.  

I guess if I have problems with this memory too now, then it's the slot?

Yes ram certainly can go bad and does. It's not everyday common for most people but it happens enough that most of the Linux distros I've looked at ship with an option to run memtest right from the boot menu.

The slots can also go bad, only had that happen once to me and it can drive a person batty trying to figure it out as you think of the ram going, not the slots so you spend hours swapping ram around only to find nothing helps and you have to go with the slot being bad.

---

