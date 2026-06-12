---
title: "[SOLVED] My computer doesn't feel as fast as it used to be with windows"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-12-25
About 4 to 5 months ago I switched to Ubuntu 8.04 from Windows XP SP2. I've really liked Linux, but for some reason it doesn't seem it is going as fast as it is supposed to be. Is there any tests I can run to see whats wrong? I'm still pretty new to linux and I'm not that great with the terminal.

---

### Post by taurus on 2008-12-25
Not as fast as in speed or graphic (scrolling)?

How much RAM does it have and what is the size of the swap partition?

Applications -> Accessories -> Terminal
```
free -m
```

---

### Post by Toshibawarrior on 2008-12-25
What kind of hardware do you have on your computer? And why do you say "it doesn't seem it is going as fast as it is supposed to be.". Is it too slow?...buggy?...sluggish?...

You can always try a fresh install of the newest Ubuntu and see if that helps. Also make sure you install all of the updates that come along. Not to mention that you should clean your Hard Drive every once in a while. :)

Also, keep in mind that some application require more horsepower than others and if you open too many programs at the same time the computer will lose performance.

:popcorn:

---

### Post by albinootje on 2008-12-25
> **Bigbob22 said:**
> About 4 to 5 months ago I switched to Ubuntu 8.04 from Windows XP SP2. I've really liked Linux, but for some reason it doesn't seem it is going as fast as it is supposed to be. Is there any tests I can run to see whats wrong? I'm still pretty new to linux and I'm not that great with the terminal.

What are the specs of your comp ?
And did Ubuntu feel slower over time, or right after the installation ?
Are you using "effects" like compiz ?
The Ubuntu desktop feels a bit sluggish, customizing the theme helps a little. 
Nautilus is also not the fastest file-manager available (e.g. Thunar and pcmanfm are faster)
Removing some applications from the gnome-session startup can also help.
Remove e.g. bluetooth support if you don't use that.

Add the "System Monitor" applet to your panel to get an idea what's going on.
If you click one time on it, you can choose to watch the memory consumption of your applications.

---

### Post by Bigbob22 on 2008-12-25
This is the response i got:
               ```
              total       used       free     shared    buffers     cached
Mem:          1009        974         35          0        102        353
-/+ buffers/cache:        518        491
Swap:         2957          0       2957

```

It is not that fast in speed and graphics.

---

### Post by Bigbob22 on 2008-12-25
I usually don't use compiz to speed up my laptop, but is still seems a bit slow. I have not tried to switch file managers yet. What file manager should switch to and how?

---

### Post by albinootje on 2008-12-25
> **Bigbob22 said:**
> I usually don't use compiz to speed up my laptop, but is still seems a bit slow. I have not tried to switch file managers yet. What file manager should switch to and how?

You could try Thunar, here's a howto how to make Thunar the default file-manager when you find out that you prefer it over Nautilus :
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

Pcmanfm is very fast, but I don't like the default folder-icons, I would need to spend some more time on playing with that.
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

Concerning your computer, you can use preload to speed up apps :
[http://theitreport.com/entries/linux/ubuntu-performance-tip---preload](http://theitreport.com/entries/linux/ubuntu-performance-tip---preload)

And for Openoffice you can use the "quickstart" option, and tweak memory usage settings :
[http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php](http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php)

In general my experience is that Linux is happier with more RAM.
I recommend using at least 512 Mb of RAM especially on older machines like Pentium-III

And.. of course you can try Xubuntu with the XFCE4 desktop.
[http://www.xfce.org/about/](http://www.xfce.org/about/)

---

### Post by Bigbob22 on 2008-12-25
Thanks for the help. My computer has 1gb RAM, how much ram should be used by my computer and how do u set how much can be used.

---

### Post by mkvnmtr on 2008-12-25
To me your memory usage seems high. I normally run about 300 to 350 Mb when I have 2 or 3 browsers open with a game, top, and a few other little things. The only time I have seen it higher is when I was using Gimp with all the other stuff at the same time. I don't know maybe this is normal and mine is the one that is not normal. But if you are going to your swap partition very often it will slow you down.

---

### Post by nhasian on 2008-12-25
in a terminal you can type

```
top
```

to see what applications are taking up the most CPU time and how much ram they are using.  press q to quit from top.  also good to know is to press k to kill an application.

---

### Post by newbee70 on 2008-12-25
> **nhasian said:**
> in a terminal you can type

```
top
```

to see what applications are taking up the most CPU time and how much ram they are using.  press q to quit from top.  also good to know is to press k to kill an application.

would **vmstat ** give a better idea of system usage?

The interesting numbers in vmstat are the first ones. This is the number of processes that are in the run queue. This value shows how many processes are ready to be executed, but can not be run at the moment because other processes need to finish. For lightly loaded systems, this is almost never above 1-3, and numbers consistently higher than 10 indicate the machine is getting pounded.

Other interesting values include the "system" numbers for in and cs. The in value is the number of interupts per second a system is getting. A system doing a lot of network or disk I/O will have high values here, as interupts are generated every time something is read or written to the disk or network.

The cs value is the number of context switches per second. A context switch is when the kernel has to take the executable code for a program out of memory, and switch in another. It's actually _way_ more complicated than that, but that's the basic idea. Lots of context swithes are bad, since it takes some fairly large number of cycles to perform a context switch, so if you are doing lots of them, you are spending all your time changing jobs and not actually doing any work. I think we can all understand that concept.

---

### Post by mdsmedia on 2008-12-25
> **mkvnmtr said:**
> To me your memory usage seems high. I normally run about 300 to 350 Mb when I have 2 or 3 browsers open with a game, top, and a few other little things. The only time I have seen it higher is when I was using Gimp with all the other stuff at the same time. I don't know maybe this is normal and mine is the one that is not normal. But if you are going to your swap partition very often it will slow you down.I don't think your experience is unusual.

I've got 512MB of RAM and usually run at about 60% usage. (edit: currently running at 72% with cache using the rest, Swap at about 11%, with 5 tabs open in Firefox, Thunderbird open, Kontact running, a few applets in the panel, Pidgin.)

The RAM usage of the OP does seem rather high. Swap looks to be plenty large enough for 1GB of RAM.

Firefox, depending on the pages opened, can spike the RAM usage a bit.

---

### Post by sethmaclaren on 2008-12-25
Were you running anything when you took the memory test thing, or was this just your computer idling?

---

### Post by albinootje on 2008-12-25
> **mdsmedia said:**
> I don't think your experience is unusual.

I've got 512MB of RAM and usually run at about 60% usage. (edit: currently running at 72% with cache using the rest, Swap at about 11%, with 5 tabs open in Firefox, Thunderbird open, Kontact running, a few applets in the panel, Pidgin.)

The RAM usage of the OP does seem rather high. Swap looks to be plenty large enough for 1GB of RAM.

Firefox, depending on the pages opened, can spike the RAM usage a bit.

+1

My "free -m" output here :

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1009        969         39          0         59        511
-/+ buffers/cache:        398        610
Swap:         1906          4       1901

Have Thunderbird running and Claws mail, and Firefox with 7 tabs open.. since hours, with Workrave running in the background.
Everything is running pretty well. 
I'm not on a laptop, so my disk is faster than a laptop-disk, and I'm using a few years old simple 128 Mb video-card.
I'm not using the "preload" app, and not using Openoffice's quick-starter.

It's pretty normal for Linux to "pre-take" quite a bit of RAM in use.

---

### Post by Bigbob22 on 2008-12-26
This is what I got for vmstat:
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0  73584  37104 475760    0    0   459    57  159 1689 17  8 60 15

```

I was running firefox while I had vmstat.

---

### Post by Bigbob22 on 2008-12-26
So what do I do to speed up my laptop, if there is a way?

---

### Post by MarblePanther on 2008-12-26
What is your laptop's specs?  Model #, processor, etc...

---

### Post by moredhel on 2008-12-26
(On a side note, htop is a superior (imo) alternative to top)

---

### Post by Bigbob22 on 2008-12-26
My computer is a Dell E1505 Inspiron 1gb RAM 120gb hardrive 1.83 ghz

---

### Post by MarblePanther on 2008-12-26
Have you installed through WUBI or a clean cd install?

---

### Post by Bigbob22 on 2008-12-26
A clean cd install

---

### Post by MarblePanther on 2008-12-26
Are you up-to-date with the latest firefox?  If the problem seems to stem from firefox's hogging of memory, I would try using Opera or Konqueror as you web browser instead.  You obviously have plenty of RAM for linux and a very capable machine. 

When was the last time you restarted your computer?

How many apps do you have open on average? And what apps?

If you are running memory intensive apps like gimp, firefox, etc... all at once, your RAM is going to be used up.

---

### Post by albinootje on 2008-12-26
> **Bigbob22 said:**
> So what do I do to speed up my laptop, if there is a way?

You already got several recommendations.
One easy thing to play with is the following :
```

sudo apt-get update
sudo apt-get install icewm fluxbox openbox

```
After successfully installing this, log out of your desktop environment.
Then at the gdm login screen, click on "sessions", and choose for example icewm, "just for this session".
Test it, and see whether it's also as slow as your Gnome desktop.

---

### Post by Bigbob22 on 2008-12-26
Its faster with icevm, but I'm not really liking the look.

---

### Post by albinootje on 2008-12-26
> **Bigbob22 said:**
> Its faster with icevm, but I'm not really liking the look.

Okay, try fluxbox too then.
And what about your programs ? 
Are they faster too now ?

Inside icewm you can actually do this in a terminal :
```

nautilus

```
and then nautilus would start, bringing you icons and wallpaper :)
(ctl-c to stop it).

---

### Post by moredhel on 2008-12-26
I recommend openbox over icewm, it has some very nice looking skins and combined with pypanel looks great :)

---

### Post by MarblePanther on 2008-12-26
+1
Though you should give kde4 a try also (sudo apt-get install kubuntu-desktop)

I dont see how a system with your specs should have a hard time with gnome....

:confused:

---

### Post by Bigbob22 on 2008-12-26
Thanks a lot. I think i might use openbox.

---

