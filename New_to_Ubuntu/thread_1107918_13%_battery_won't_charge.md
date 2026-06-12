---
title: "13% battery won't charge?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by kmtopper01 on 2009-03-27
I just switched to ubuntu last night after trying to get vista on my new hard drive and failing, and I have a charger cord for my laptop, but it keeps telling me the battery is at 13% and might be 'broken'. What's this mean? Why isn't it charging? I've got tons of other questions but this one is my first concern. If I can't use my laptop unwired, what good is it?

---

### Post by BDNiner on 2009-03-27
How old is your battery? Did you try and condition it yet? Was is working fine before?

---

### Post by mbzn on 2009-03-27
Try unplugging the AC, the 13% should now go lower... try to get the battery to discharge completely. Remember that if you are in an os this is probably a bad idea, try to use a lightbulb or something. If you can get the battery to completely discharge, the laptop is now off and cannot switch on, connect the AC and let it charge, if the problem is still there the battery might be faulty.

---

### Post by amauk on 2009-03-27
the battery indicators on operating systems are just estimates
it may take a little bit for the indicator to show sane numbers

Charge it all the way up,
shutdown, unplug the AC cord
startup, and run the laptop on battery until it's empty

that should give Ubuntu all the information it needs to show more accurate %ages

---

### Post by damis648 on 2009-03-27
Agreed. Boot your laptop up to GRUB (the bootloader, because when the laptop dies there nothing can really be too damaged) and just let it sit until the battery dies. When it does, plug it in and let it charge overnight to make sure it is absolutely full. Boot it up, and see if Ubuntu still says 13%. If it does, you may want to try the procedure again, or you may want to check in your BIOS. I know mine has a whole battery section, with Battery Health and charge, see if you BIOS has anything to say about it.

---

### Post by sylvainrb on 2009-03-27
The same message came up when I installed Ubuntu 8.10 on my laptop. I just clicked on ignore message or do not show again, and when restarting the battery indicator worked fine. Does it keep poping up even when starting the laptop again?

---

