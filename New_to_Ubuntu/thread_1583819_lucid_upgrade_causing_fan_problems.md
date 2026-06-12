---
title: "lucid upgrade causing fan problems"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by stripey on 2010-09-28
I have just upgraded to Lucid Lynx and everything went very smoothly but the computer is reaching critical temperature and shutting down without the fan ever kicking in. 

I ran a live CD for another distribution and the fan was fine so it is not a hardware problem. 

I have found lots of bug reports but no fix.
Help!?

I am using an acer aspire 5315

Thanks

---

### Post by stripey on 2010-09-28
So it seems that by sleeping the computer and waking it up the fan kicks in.

[http://kubuntuforums.net/forums/index.php?topic=3109755.0](http://kubuntuforums.net/forums/index.php?topic=3109755.0)

But how exactly do you upgrade a kernel?

Thanks

---

### Post by nalgarryn on 2010-10-10
[FONT="Palatino Linotype"]The fan problems you are experiencing are due to a lack of Acer's proprietary software that only runs under Microsoft operating systems.

However, Acer has updated the BIOS for the 5315 and it now allows for hardware control and you won't need that proprietary software after all. I updated my bios just the other day and am not having any problems.

The bad news is, I couldn't get the .exe file I downloaded from acer.ca to run under a dos boot. What I ended up doing is installing windows xp professional on the first part of my drive and running the downloaded .exe file. I then reinstalled ubuntu on the back part of my drive and am running dual boot.

It is possible that you could use some sort of bootable (USB, CD, whatever) to load a windows 98 OS or something and run the .exe from there.


I installed the 1.45 version of the BIOS. You may want to verify you have no issues. Search this forum for the post "acer aspire shuts down". There are a few good tidbits in it. Starting on page 11 you may want to read to the end. In particular look for the post with:

```
sudo apt-get install lm-sensors
sudo apt-get isntall conky
```

because it has *an attached archive with a script in it for conky*. If you use the gnome panel temperature sensor it will only read in 5' jumps (35, 40, 45, etc) but if you use Conky you will get 1' jumps.

On my system (Acer Aspire 5315-2681) I only have one thermal zone (TZ01) and the other sensors don't show anything.

Hope that helps.

Edit:
[http://ubuntuforums.org/showpost.php?p=4726231&postcount=111](http://ubuntuforums.org/showpost.php?p=4726231&postcount=111)[/FONT]

---

