---
title: "Everything is slow -- video driver perhaps?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-20
Something is wrong. I'm new to Linux, and I love it. But something doesn't feel right. Everything is really slow, it prints weird colors when I print, my screen saver locks up, the web browser drags along slowly. DVD movies are somewhat dimmer than usual. 

I think I don't have the video card drivers installed. It's the one that came with my computer--  a 64MB integrated Intel Extreme. My computer runs fine in Windows. But I hate using it. I much prefer to boot Linux so I can learn more about it. 

What should I do to install the right video driver?

---

### Post by sanubie on 2008-12-20
I must admit, however, I'm not 100% sure it is a driver issue. But that is what I've been told by a few techies at work, etc. I'd really like to get up to speed on all this, and I appreciate anyones assistance. 

Things are usable, obviously I'm here writing this. But it is very frustrating. :confused:

For example: when I scroll in my browser there is a slight delay. Which doesn't sound too bad, but an accumulation of delays starts wearing on your patience. A third of a second delay in scrolls amounts to hours of lost time a month. Please give me a hand.

---

### Post by sanubie on 2008-12-20
It isn't just Firefox. I'm noticing a lot of lag. It's driving me insane. Here is some more info. My specs are: 768 MB RAM, 2.4 GHz single intel 4 processor, 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

--my computer is pretty fast usually. In fact, before I upgraded to Hardy it was the best OS I had ever used. It booted up in seconds. All the applications opened flawlessly and quickly, nothing ever crashed, it was righteous, and I was thoroughly pleased with its performance. I had imagined that I'd never even need that XP partition again. 

Unfortunately my joy was short lived. After upgrading to Hardy it has caused me nothing but frustration. Everything is slow, everything lags, my videos don't look right, things don't print accurately, my update manager freezes half the time, Firefox is slow... all other applications are slow, things crash, I'm forced to kill applications, when I watch movies and try to full screen it takes forever... 

What is the deal? How come it used to work, but now it's a mess? Anybody got any ideas how to fix this?

---

### Post by baruch60610 on 2008-12-21
Your computer's response is not normal.  Something is wrong, as you say.

You have a few places you can look.  If you are OK with using the command line, try typing 'top'.  This will display a listing of running processes, with the ones taking the most resources at the top (guess why they named it that).  When you want to stop the program, just type 'q' for 'quit'.

To get to the command line, you can use 'konsole' (for KDE), or 'gnome-termina' for Gnome.  'top' is a harmless program.

See what's up there.  You may very well have some unexpected process running that is hogging CPU cycles.  On KDE, I found that strigi was really slowing things down.  Strigi is a desktop search engine, useful to some, but it needs to read every single file on your computer.  That takes time, and slows things down.  If you don't want strigi, you can uninstall it.

I don't recall the name right now, but there are a couple of other programs that perform some housekeeping chores and may slow things down while they work.

You might also look to see what programs you have that automatically run at boot time - 'daemons' they may be called.  Those would often end with a -d, as in 'spamd' or 'hald'.  It might help to review whether you need all of those things going.

Another possibility is that you may be swapping too often.  If your RAM gets full, the system will use part of your hard drive as virtual memory.  That keeps programs from crashing, but it is thousands of times slower than RAM.  If you have many programs running at the same time, you may be running out of RAM, and that could slow your system down considerably.

To check your memory, type 'free'.  You'll get something like this:
```

baruch@ubuntu:/boot$ free
             total       used       free     shared    buffers     cached
Mem:       1034284    1015904      18380          0     205380     322672
-/+ buffers/cache:     487852     546432
Swap:       976552      40864     935688

```That tells me that I am, indeed, swapping a little bit.  I don't know of a way to fix that, other than to close out of programs you aren't using, or that you only use occasionally.  Much as I like to have everything up and running for my viewing pleasure, I often need to just shut certain programs down or suffer the consequences.

You might double-check that first line (where it starts with 'Mem:'.  Is your system reporting all your memory?  Or are you missing some?  If the system thinks you only have 500 Meg, that could do it too - not likely, but it's something to consider.

---

### Post by sanubie on 2008-12-21
> **baruch60610 said:**
> Your computer's response is not normal.  Something is wrong, as you say.

You have a few places you can look.  If you are OK with using the command line, try typing 'top'.  This will display a listing of running processes, with the ones taking the most resources at the top (guess why they named it that).  When you want to stop the program, just type 'q' for 'quit'.


Indeed, I am comfortable using the shell. Entering commands is half the fun of Linux. At least... that's how I feel. I'm trying to learn more about, and I've found a lot of good tutorials online that are helpful. 

I followed the advice outlined above, but I don't usually have many programs running at once. And there doesn't appear to be anything taking up a substantial amount of space except for a process called "Xorg". Top tells me it's 6 to 14.6% of my CPU. I'm not familiar with Xorg. But it has a cool name, so I'm okay with it unless it is the source of my problem. I doubt it is, though.   


> **baruch60610 said:**
> 
...On KDE, I found that strigi was really slowing things down.  Strigi is a desktop search engine, useful to some, but it needs to read every single file on your computer.  That takes time, and slows things down.  If you don't want strigi, you can uninstall it.


I didn't see that process listed in the readout. So I'm guessing that isn't the problem either.  
 

> **baruch60610 said:**
> 
I don't recall the name right now, but there are a couple of other programs that perform some housekeeping chores and may slow things down while they work.


Something tells me it's a driver issue. Nothing appears to be working while it lags. It just seems to lag. For example: When I put in a DVD and play it. It plays dim and it's somewhat choppy at times. When I go to full screen it will freeze, and then the movie will catch up to itself eventually by playing everything is super-fast speed until it starts playing normally again. 

I checked under **System / Administration---> Hardware Drivers** to see if my video card was listed, but there is nothing there. It's just an empty Window.

 
> **baruch60610 said:**
> 
You might also look to see what programs you have that automatically run at boot time - 'daemons' they may be called.  Those would often end with a -d, as in 'spamd' or 'hald'.  It might help to review whether you need all of those things going.

Another possibility is that you may be swapping too often.  If your RAM gets full, the system will use part of your hard drive as virtual memory.  That keeps programs from crashing, but it is thousands of times slower than RAM.  If you have many programs running at the same time, you may be running out of RAM, and that could slow your system down considerably.

To check your memory, type 'free'.  You'll get something like this:
```

baruch@ubuntu:/boot$ free
             total       used       free     shared    buffers     cached
Mem:       1034284    1015904      18380          0     205380     322672
-/+ buffers/cache:     487852     546432
Swap:       976552      40864     935688

```That tells me that I am, indeed, swapping a little bit.  I don't know of a way to fix that, other than to close out of programs you aren't using, or that you only use occasionally.  Much as I like to have everything up and running for my viewing pleasure, I often need to just shut certain programs down or suffer the consequences.


You might double-check that first line (where it starts with 'Mem:'.  Is your system reporting all your memory?  Or are you missing some?  If the system thinks you only have 500 Meg, that could do it too - not likely, but it's something to consider.


Okay, I tried that out too. Here is what my system returned. 

```

             total       used       free     shared    buffers     cached
Mem:        766636     445828     320808          0       4412      85108
-/+ buffers/cache:     356308     410328
Swap:      1322960      39796    1283164

```

You tell me. Does there look to be any problem here? I don't understand all these numbers fully yet. Thanks a lot for your help. I'll eventually get the hang of this.

---

### Post by densou on 2008-12-21
let's check if video driver works fine .... how many fps do you get with glxgears ? [just type glxgears in the prompt windows and wait ;) ]

:)

---

### Post by northern lights on 2008-12-21
Can you please post the output of ```
sudo lshw -C display
```for information on your video device and whether it's setup correctly?

Are you running compiz? It might also be the culprit. The following is not a long-term solution, but for now try switching it off (enable metacity) via```
metacity --replace
```

---

### Post by sanubie on 2008-12-21
First I'd like to start by personally thanking everyone for their time and assistance. Linux simply wouldn't be what it is if it were not for people like you and this fine community of support. You guys rock. 

Okay, not for the rest. That glxgears command is awesome! I wasn't expecting to actually see turning gears-- haha. Linux is full of surprises. The animation played just fine. Not sure what the readout means. But here are 5 of the results. 

```

2177 frames in 5.0 seconds = 435.263 FPS
2075 frames in 5.0 seconds = 414.907 FPS
2113 frames in 5.0 seconds = 422.527 FPS
2165 frames in 5.0 seconds = 432.792 FPS
2148 frames in 5.0 seconds = 429.444 FPS

```

And here is the output to the following command, requested by northern lights. 

> 
sudo lshw -C display


**The result:**
```

  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

```

---

### Post by sanubie on 2008-12-21
> **northern lights said:**
> Are you running compiz? It might also be the culprit. The following is not a long-term solution, but for now try switching it off (enable metacity) via```
metacity --replace
```

Okay, strange enough... I'm not sure exactly if this was what did it or not. But after I typed in the following command things run much smoother. I even tried watching a movie and it would go into full screen without freezing for several seconds. 

The video stills looks a little dim. But things are moving better now. Firefox is much more responsive to the scroll wheel. Any idea how that could of helped, or what that being the problem may indicate, and what else to do to that might make things even better. Things are much more bearable now, though.  THANKS!! :)

---

### Post by northern lights on 2008-12-21
> **sanubie said:**
> 
```

  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: [COLOR="Red"]driver=i810_smbus[/COLOR] latency=0 module=i2c_i810

```
The device has been assigned the correct driver and appears to be setup properly.


> **sanubie said:**
> [After running *metacity --replace*]Okay, strange enough... I'm not sure exactly if this was what did it or not. But after I typed in the following command things run much smoother. I even tried watching a movie and it would go into full screen without freezing for several seconds.
You've changed the window manager. metacity is nowhere near as powerful as compiz, but also much more resource efficient. It appears compiz was slowing your system down. After rebooting, compiz should be enabled again. If the machine slows down again, this was definitely it. Make metacity your default WM or try other alternatives such as IceWM or enlightenment (not pre-installed).

---

### Post by HavocXphere on 2008-12-21
I'd suggest ignoring the printing and dim DVDs for now...those sound like they are, at best, going to confuse the troubleshooting efforts.

I'd agree that it sounds like a video related issue. It would help if you posted the contents of your xorg.conf.

Firstly disable all fancy desktop effects/compiz etc like northern lights said. If that doesnt work try using the Vesa driver...thats usually a pretty safe choice for troubleshooting.

Also, there are some issues with the intel integrated graphics atm. I don't use one so I don't know the details...but I know I ran across something about certain types of intel integrateds that don't work correctly under 8.10 while googling a video issue of my own.

---

### Post by northern lights on 2008-12-21
> **HavocXphere said:**
> try using the Vesa driver...thats usually a pretty safe choice for troubleshootingThe graphics device is setup correctly. This would be a step backwards.

> **sanubie said:**
> Not sure what the readout means. But here are 5 of the results. 

```

2177 frames in 5.0 seconds = 435.263 FPS
2075 frames in 5.0 seconds = 414.907 FPS
2113 frames in 5.0 seconds = 422.527 FPS
2165 frames in 5.0 seconds = 432.792 FPS
2148 frames in 5.0 seconds = 429.444 FPS

```

The OP is getting over 400 FPS (frames / second). That is plenty.

---

