---
title: "My processor frequency?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-26
Hey, Ubuntu-ers!
I did a search about this issue, but cant seem to find nothing, im sure that this topic has been discussed, but I still have to ask.
I have noticed a few times when I looked at my CPU frequency and its 1000MHz in Ubuntu. Is this a display only freq? My CPU is clocked @ 3000MHz, but Ubuntu sysinfo is showing 1000MHz (it recognizes CPU model correctly, and sees both cores). Does this affect my CPU speed?

---

### Post by Joeb454 on 2009-01-26
I'm going to hazard a guess that you processor is scaling it's speed down to draw less power etc.

I can't be 100% sure, but I'm sure somebody will come here and post a way to find out for certain :)

Mine does it to if that's any consolation :p

---

### Post by Ben Page on 2009-01-26
Does Ubuntu have that capability? I have turned off Cool'n'quiet feature in MB bios. Bios is always showing 3000MHz at boot (hit del).

---

### Post by abyssius on 2009-01-26
> **Ben Page said:**
> Does Ubuntu have that capability? I have turned off Cool'n'quiet feature in MB bios. Bios is always showing 3000MHz at boot (hit del).

The BIOS will always show the frequency of your CPU clock settings. It sounds like Ubuntu is applying Frequency Scaling, even though disabling Cool n Quiet should disallow this.

To find out for sure, there is a frequency scaling applet available that you can add to the top panel. Right-click in a blank area of the top panel and click on [add to panel] to select the applet menu. The applet is called the *Frequency Scaling Meter*. This will show you if Ubuntu is applying frequency scaling to your CPU. The meter should range between 1000Mhz and 3000Mhz, depending on what you do. 

The way I halted this behaviour is to uninstall a program called powernowd. 

```
apt-get remove powernowd
```

However, I thought later that this is actually kinda cool. It doesn't lower the performance of your system since it will provide and maintain 3000Mhz on demand. During idle, the CPU running at 1000Mhz means over-all it's running cooler than it would at full-blast all the time.

---

### Post by Ben Page on 2009-01-26
yep, this seems to be the issue, sys info is not refreshing its showings, but this thingy does, and I can see the scaling is working. It is a nice feature for an OS, but im not sure it is doing a good job.
For example, when Im loading OO word, it is obvious the hdd is struggling, but CPU stays on 1GHz (I think it could use more CPU power). Max I could squeeze was 2.2GHz while running the synaptic.

---

### Post by epswinde on 2009-01-26
> **Ben Page said:**
> For example, when Im loading OO word, it is obvious the hdd is struggling, but CPU stays on 1GHz

The hdd is the 'slowest' part of your machine, to be honest.  The reason your cpu is seemingly idle is because your hard disk can't get the data to the cpu fast enough.  It would be like driving a car in bumper to bumper traffic and putting the accelerator all the way to the floor -- simply unnecessary.

If you really want to do some cpu-intensive tasks, try converting some .flac files to .mp3, or transcoding a movie from one format to another.  Or try playing some resource intensive game.

The long and short of it is that cpu frequency is not even the most important factor in overall performance, much of the speed limit is set by I/O tasks and bus speed.

---

### Post by Ben Page on 2009-01-26
I knew that about the HDD, it is the slowest part of the comp, but I still wanted to see if I will get some improvements if I turn the thing off. And I got them, my comp now flies! Thing is that this scaling program is working with the default CPU freq. I have AMD Athlon x2 4200+, that is 2200GHz per core, but I overclocked my CPU to 3.0GHz in bios, but it seems that while powernowd is running I can't get past 2.2GHz. Now it really is running in 3.0GHz mode, even sysinfo is confirming that.

---

### Post by sdennie on 2009-01-26
> **Ben Page said:**
> yep, this seems to be the issue, sys info is not refreshing its showings, but this thingy does, and I can see the scaling is working. It is a nice feature for an OS, but im not sure it is doing a good job.
For example, when Im loading OO word, it is obvious the hdd is struggling, but CPU stays on 1GHz (I think it could use more CPU power). Max I could squeeze was 2.2GHz while running the synaptic.

Most processes aren't CPU bound when starting up but instead I/O bound (as you've noted here).  Scaling the CPU to max wouldn't make them any faster and, in fact, using the dynamic scaling is both almost impossible to notice and very good for the CPU as it keeps it much cooler.  Making your CPU run faster isn't going to make disk I/O any faster.

---

### Post by abyssius on 2009-01-26
> **Ben Page said:**
> I knew that about the HDD, it is the slowest part of the comp, but I still wanted to see if I will get some improvements if I turn the thing off. And I got them, my comp now flies! Thing is that this scaling program is working with the default CPU freq. I have AMD Athlon x2 4200+, that is 2200GHz per core, but I overclocked my CPU to 3.0GHz in bios, but it seems that while powernowd is running I can't get past 2.2GHz. Now it really is running in 3.0GHz mode, even sysinfo is confirming that.

Actually, I think you can set the scaling factors for powernowd and perhaps set 3000mhz as the upper limit. Anyway, if you're overclocking  - I'm sure you have a robust cooling system, so keep it pumping, mate....

---

### Post by epswinde on 2009-01-26
Theres nothing in the powernowd man page regarding pushing the upper limit of the cpu scaling frequency, so you might be out of luck with that.  The biggest reason I use the dynamic frequency settings (and don't overclock) is because the sound of my fan running a full blast is second only to fingernails on a chalkboard in terms of annyoing sounds...  if only i could afford a nice liquid cooling system, i'd be in hog heaven...

---

### Post by bruce89 on 2009-01-26
The gnome-panel CPU Frequency Scaling Applet can be used to force a specific speed, but as noted above, this is probably pointless.

---

### Post by abyssius on 2009-01-26
> **epswinde said:**
> Theres nothing in the powernowd man page regarding pushing the upper limit of the cpu scaling frequency, so you might be out of luck with that.  The biggest reason I use the dynamic frequency settings (and don't overclock) is because the sound of my fan running a full blast is second only to fingernails on a chalkboard in terms of annyoing sounds...  if only i could afford a nice liquid cooling system, i'd be in hog heaven...

LOL, I never noticed the "noise factor" until you pointed it out. I was wondering if he changed upper-limit percentage from 80% to 100%, would he be able to achieve the full clock. However, now that I think about it,  I scale to 2.4Ghz which is 100% of my CPU clock, using all the default settings,,,,

---

### Post by Ben Page on 2009-01-26
I have a nice self composed cooling system involving two coolermaster "super" silent fans, one for GPU and one for CPU, there is no difference in noise when overclocked. Ever since I discovered overclocking, I am overclocking everithing that can be overclocked (and I never coocked nothing so far) ;). Current CPU never crossed 51C ~ 120F.
Anyway, how to set powernowd's limit? Maybe some code would help me do this (since I cannot see any GUI). I feel performance boost now when I uninstalled the powernowd, but I like the idea of dropping the clock when it is not needed, so I would like to use this feature in Ubuntu.

---

### Post by epswinde on 2009-01-26
> **abyssius said:**
> I was wondering if he changed upper-limit percentage from 80% to 100%, would he be able to achieve the full clock.

The upper-limit percentage is the percent of cpu usage before powernowd increases the cpu frequency.  meaning under greater than 80% load, the speed of the processor increases.

You may need to alter the source and build your own powernowd to add the capability to dynamically scale to an overclocked speed. then again, if you don't mind the extra power bill, or youre not running on a laptop (battery life ftw), then overclocking and disabling powernowd isn't as big of a deal.  especially if you have some sweet cooling fans to keep everything nice and cool...:)

---

### Post by Ben Page on 2009-01-27
So I guess overclocking is disabled in Ubuntu? I need powernowd to enable loads up to 150%, is there a solution, or the only solution is uninstalling the powernowd and say goodbye to this nice feature?

---

### Post by abyssius on 2009-01-27
> **Ben Page said:**
> So I guess overclocking is disabled in Ubuntu? I need powernowd to enable loads up to 150%, is there a solution, or the only solution is uninstalling the powernowd and say goodbye to this nice feature?

Hey Ben

I don't think "over-clocking" is disabled in Ubuntu. You pointed out yourself that sysinfo reported your 3gig clock speed after you disabled powernowd. You do bring up an interesting point, though. Is the powernowd program getting the clock frequency information directly from the CPU, and ignoring your BIOS settings? The info I got about powernowd comes from the MAN text. Maybe if you google the program, you'd find the developer's site and get more information. I simply uninstalled it (basically to troubleshoot a video driver problem), then re-installed it once I discovered that it wasn't affecting the driver. It doesn't seem to affect my performance. However, I'm not over-clocking.

---

### Post by abyssius on 2009-01-27
> **epswinde said:**
> The upper-limit percentage is the percent of cpu usage before powernowd increases the cpu frequency.  meaning under greater than 80% load, the speed of the processor increases.

You may need to alter the source and build your own powernowd to add the capability to dynamically scale to an overclocked speed. then again, if you don't mind the extra power bill, or youre not running on a laptop (battery life ftw), then overclocking and disabling powernowd isn't as big of a deal.  especially if you have some sweet cooling fans to keep everything nice and cool...:)

Thanks for pointing out how powernowd actually works. Good information. I wonder why powernowd doesn't acknowledge his over-clocked CPU frequency when it creates scaling parameters? I didn't set any options when I installed powernowd. It seemed to figure things out by itself.

---

### Post by stchman on 2009-01-27
You want your CPU to scale it's frequency.  There is no reason for the processor to run at 3GHz when you are reading a web page.

Processor scaling dramatically improves heat generation.  The processor will ramp up when it needs to.

---

### Post by Ben Page on 2009-01-27
All that is clear, now the problem is that if powernowd is installed processor works within its default frequencies (in my case 2200MHz), it seems that powernowd is getting info from MB, or CPU drivers and sets the scaling according to processors default values, 100% is 2200MHz, so any overclocked value vould have to be 120% or more (for example). When I uninstall the powernowd, sysinfo is showing the 3Gig freq, but that way I don't have the scaling feature, it is always 3Gig. So my issue is that I can't use scaling or I can't overclock. All my clocks are set in MB bios, but Ubuntu seems to override those settings (if powernowd is installed). I don't want to edit any source code, I vould just want another app witch will do the job (witch can be set higher than 100%) or set powernowd to support overclocking.
But having all this in consideration, Ubuntu does not support overclocking by default (this could be an issue in some cases - like mine).

---

### Post by mcduck on 2009-01-27
I assume you have done the overclocking by increasing the bus speed (as most modern CPU's have their max CPU multipliers locked and only allow lower multipliers for saving power, disabling the multiplier lock can't be done by any BIOS setting or software but requires physical modifications to the CPU itself).

In that case powernowd has no way to change that setting (as all it does is changing the CPU multiplier, not bus speed), your CPU is still working at overclocked speeds, and software is simply reporting wrong speed as it still calculates the speed assuming standard bus speeds.

You have also misunderstood the powernowd's limit percentage. It has nothing to do with CPU speed, it simply tells how much load there needs to be until powernowd changes to next available CPU multiplier. If the limit percentage is 0% your CPU will run at max speed at 0% CPU usage, with 100% limit your CPU load needs to be at 100% before next multiplier is used. This doesn't limit your max CPU speed in any way, only defines hot the frequency is scaled to save power. (If you would somehow change the limit to 110% it would mean that your CPU would never change to higher multiplier.)

In other words, overclocking works just fine with Ubuntu, but I got the feeling that you should do a bit more research about how overclocking and CPU speed controlling really works. Overclocking is a great way to get more performance out of your computer but you _really_ need to know what you are actually doing.. ;)

---

### Post by Ben Page on 2009-01-27
I know what you mean, every intel is locked, but Amd is not, I can modify multiplier, it's set to 11x, it can be downscaled only though.
Maybe its true that scaling thing is showing the wrong frequency, based only on percentage of use, but sysinfo is showing the correct values. If powernowd is installed, I can't get past 2200MHz (the default), but if it's uninstalled, sysinfo is showing 3000MHz. But it's not about showing the numbers, my comp simply flies after uninstalling the powernowd. Its like using DSL or xfce without any effects.

---

### Post by mcduck on 2009-01-27
> **Ben Page said:**
> I know what you mean, every intel is locked, but Amd is not, I can modify multiplier, it's set to 11x, it can be downscaled only though.
Maybe its true that scaling thing is showing the wrong frequency, based only on percentage of use, but sysinfo is showing the correct values. If powernowd is installed, I can't get past 2200MHz (the default), but if it's uninstalled, sysinfo is showing 3000MHz. But it's not about showing the numbers, my comp simply flies after uninstalling the powernowd. Its like using DSL or xfce without any effects.
Yeah, both Intel and AMD allow lower multipliers, that's the basic idea behind frequency scaling. Setting the multiplier higher than the default, however, is a bit more tricky thing to do. (Unless you have the money for AMD's Black Edition or Intels EE versions, or manage to acquire some engineering sample processor)

Ir really sounds quite strange that powernowd would limit your processor speed, but if it for some treason really is limiting your frequency it must be because it has stored some pre-set frequency values in some file and ties to use those instead of simply working directly with available multipliers. So it's now using lower than maximum allowed multiplier bacuase using highest multiplier would result in higher frequency than what it believes  to be allowed..

If this is the case it should be possible to edit it's configuration to get rid of the problem. At least with Intel CPU's you can simply edit a text file that contains allowed CPU frequencies.. (doing that will of course not overclock the CPU, it still has to support the multipliers required to reach those frequencies).

You could try to find out what file contains those settings for powernowd (It's been a while since I've had AMD processor so I'm not able to give more detailed information).

Other solution would be to disable powernowd and use other means to handle power saving. You could try athcool, although it was originally made for older AMD prcessors that didn't support frequency scaling it should work just as fine with new ones. While not as efficient as frequency scaling it can still reduce both power usage and heat generation quite radically when the processor is idle.. And using athcool definitely won't have any effect on your overclocking (I used it with my overclocked Athlon XP setup, worked great.)

edit: I almost forgot, sorry for being a bit skeptical about your knowledge about overclocking, you just didn't tell very much information about your actual setup and multipliers/bus speeds/voltages you are using so I wanted to make sure you're not just somebody who read some web page about overclocking and started playing with BIOS settings without knowing what they really are.. After all, this is the "Absolute Beginner" forum and I wouldn't want to help anybody fry their hardware.. ;)

---

### Post by stchman on 2009-01-27
My Core 2 Quad Q6600 I own is a 2.4GHz processor.  I have overclocked it to 3.0GHz.  The multiplier is 9.0 and I cannot change that.

I changed the FSB from 266 to 333 to get the processor up to 3.0GHz.  I don't believe that Ubuntu would have any way of changing the FSB for me so even though Ubuntu reports 2.4GHz the processor is actually running at 3.0GHz.

What I believe Ubuntu does is simply read the CPU ID string and not the actual frequency itself.

I would like to have an actual CPU frequency meter in Ubuntu.  Does anyone know of one.  I use the frequency scaling monitor that comes with the Panel.

---

### Post by mcduck on 2009-01-27
> **stchman said:**
> 
What I believe Ubuntu does is simply read the CPU ID string and not the actual frequency itself.

That's what I believe as well. 

It might be a good idea to simply compare some CPU performance test results (superpi, for example) with power saving features enabled/disabled to check if they really limit the CPU's max speed or if the reported speed is just wrong).

---

### Post by stchman on 2009-01-27
> **mcduck said:**
> That's what I believe as well. 

It might be a good idea to simply compare some CPU performance test results (superpi, for example) with power saving features enabled/disabled to check if they really limit the CPU's max speed or if the reported speed is just wrong).

Good idea.  I would assume linearity and should see a 25% increase in processor intensive applications.  Any apps come to mind?

---

### Post by mcduck on 2009-01-27
> **stchman said:**
> Good idea.  I would assume linearity and should see a 25% increase in processor intensive applications.  Any apps come to mind?

Superpi has a native Linux version, gives easily comparable results and is pretty much the standard test for pure CPU performance anyway.

There's a thread about it in Cafe section, with a link for downloading the app: [http://ubuntuforums.org/showthread.php?t=60264]("http://ubuntuforums.org/showthread.php?t=60264")

---

### Post by epswinde on 2009-01-27
check what the system says in /proc/cpuinfo, that may be where powernowd gets its information from.

Although, i'm not going to advocate changing anything in /proc, i've never used it for anything besides information, so i don't know what can happen

---

### Post by abyssius on 2009-01-27
> **stchman said:**
> 
What I believe Ubuntu does is simply read the CPU ID string and not the actual frequency itself.

I would like to have an actual CPU frequency meter in Ubuntu.  Does anyone know of one.  I use the frequency scaling monitor that comes with the Panel.

Ben says that with powernowd disabled, Ubuntu reports his over-clocked frequency accurately. So it's probably not Ubuntu, but powernowd itself that only relies on the CPU ID string.

---

### Post by Ben Page on 2009-01-27
super pi not working, I follow instructions, and it starts but says there is no (some kind of) parameter. In "/proc" I can't edit files via any txt editor I have installed (should I do sudo gedit?). Could find only 32bit athcool, I am using 64bit, so it won't install.
As for my overclocking skills go, I was overclocking 4 PCs with Intels till now, so I assume I know what I'm doing. This IS absolute beginners corner, but UBUNTU beginners. I am overclocking trough/via BUS +1 clock, I am not touching my multiplier because I can only lower it. Voltage is also default, because there is no need to change it (only DDR voltage is altered), system is stable, and by increasing it I will only get higher CPU temps.
P.S. English is not my native language, so maybe I'm not expressing myself correctly.
Still looking for a tool to enable scaling, but also overclocking. And a link to a good benchmark tool (witch doesn't have to be compiled).

---

### Post by mcduck on 2009-01-28
> **Ben Page said:**
> super pi not working, I follow instructions, and it starts but says there is no (some kind of) parameter. In "/proc" I can't edit files via any txt editor I have installed (should I do sudo gedit?). Could find only 32bit athcool, I am using 64bit, so it won't install.
As for my overclocking skills go, I was overclocking 4 PCs with Intels till now, so I assume I know what I'm doing. This IS absolute beginners corner, but UBUNTU beginners. I am overclocking trough/via BUS +1 clock, I am not touching my multiplier because I can only lower it. Voltage is also default, because there is no need to change it (only DDR voltage is altered), system is stable, and by increasing it I will only get higher CPU temps.
P.S. English is not my native language, so maybe I'm not expressing myself correctly.
Still looking for a tool to enable scaling, but also overclocking. And a link to a good benchmark tool (witch doesn't have to be compiled).

Superpi doesn't need to be compiled. Just extract the package and run it. You have to tell Superpi how many decimals you wish to calculate.

Typical test would be a million decimals, for that use:
```
./super_pi 20
```
the number means powers of two, 2^20=1048576. For more accurate results change the number to 23 (for 8M decimals test)

(These instructions were in the thread where you downloaded the package, and included with the package itself)

Also, I just made the simplest thing ever and read through the doc file for powernowd. You might be interested in checking /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by stchman on 2009-01-28
> **abyssius said:**
> Ben says that with powernowd disabled, Ubuntu reports his over-clocked frequency accurately. So it's probably not Ubuntu, but powernowd itself that only relies on the CPU ID string.

I have a Core 2 Quad and tried Super Pi.  At 3.0GHz with Ubuntu reporting 2.4GHz I got ~12.6 sec.  At 2.4GHz with Ubuntu reporting 2.4 GHz I got ~16.3 sec so it is indeed overclocked and Ubuntu not giving actual clock frequency.

---

### Post by Ben Page on 2009-01-28
> **stchman said:**
> I have a Core 2 Quad and tried Super Pi.  At 3.0GHz with Ubuntu reporting 2.4GHz I got ~12.6 sec.  At 2.4GHz with Ubuntu reporting 2.4 GHz I got ~16.3 sec so it is indeed overclocked and Ubuntu not giving actual clock frequency.

This seems to be right.
I have managed to run super_pi (after a little hustle), and I got same results, with powernowd installed - and reporting 2.2GHz (CPU_OC), was the same as powernowd uninstalled and sysinfo reporting 3.0GHz. I even got a 1 sec. better result when I was using powernowd in "performance mode".
So, it looks like this was an misunderstanding produced by powernowd misreading the correct CPU freq. and add a little of mine paranoia and placebo, and there you have it!
As for the compiling, I was referring to hardinfo, app that supports benchmarking more hardware categories.
Well, all is good, if super_pi is an accurate and reliable tool.

:popcorn:

---

### Post by mcduck on 2009-01-29
> **Ben Page said:**
> This seems to be right.
I have managed to run super_pi (after a little hustle), and I got same results, with powernowd installed - and reporting 2.2GHz (CPU_OC), was the same as powernowd uninstalled and sysinfo reporting 3.0GHz. I even got a 1 sec. better result when I was using powernowd in "performance mode".
So, it looks like this was an misunderstanding produced by powernowd misreading the correct CPU freq. and add a little of mine paranoia and placebo, and there you have it!
As for the compiling, I was referring to hardinfo, app that supports benchmarking more hardware categories.
Well, all is good, if super_pi is an accurate and reliable tool.

:popcorn:

Great that you got it sorted out and there isn't any problem overclocking with Ubuntu..

Superpi definitely is reliable, it's pretty much the standard performance test for overclockers around the world (although Windows users claim that Linux versions results wouldn't be comparable with the Windows version.. I wonder why.. ;))

It's not perfect, it only runs as single thread so you won't get any benefits from multi-core CPU's unless you run several instances of superpi at the same time. But as it does large amount of simple calculations with small amount of data it doesn't depend on your other hardware which makes it a pure CPU performance test.

Of course it would be nice to get the correct readings for CPU frequency as well, but I suppose getting the extra performance is more important than getting accurate frequency readings.

---

### Post by Ben Page on 2009-01-29
> **mcduck said:**
> Great that you got it sorted out and there isn't any problem overclocking with Ubuntu..
Of course it would be nice to get the correct readings for CPU frequency as well, but I suppose getting the extra performance is more important than getting accurate frequency readings.

Thats right!
When I ran super pi, in windows, it offered me different "parameters", it seems it runs a calculation in bits or something like that, it offers only 256 bits, 512 bit etc. what would be the closest to "super_pi 20"? Or how would I get super_pi in linux to calculate with, say 256bits? I would like to compare windows and Ubuntu.

---

### Post by mcduck on 2009-01-29
> **Ben Page said:**
> Thats right!
When I ran super pi, in windows, it offered me different "parameters", it seems it runs a calculation in bits or something like that, it offers only 256 bits, 512 bit etc. what would be the closest to "super_pi 20"? Or how would I get super_pi in linux to calculate with, say 256bits? I would like to compare windows and Ubuntu.

I don't remember any setting about "bits". You are probably talking about decimal digits. The same setting as the number you add as parameter when running it in Linux.

Like I said, the number is powers of 2, "20" calculates 2^20 decimals (about 1 million, same as the 1M test in Windows.) 256 decimals would be 2^8, so run "super_pi 8" to do that.

The test is more accurate the more decimals you calculate. The standard tests used are either 1M or 8M (20 or 23 in Linux)

---

### Post by Ben Page on 2009-01-29
If this is right, mcduck, than Ubuntu is faster with these calculations by far! The difference in my case is 6.477 secs for Ubuntu! Windows7 B1B7000 = 33.181
        Ubuntu I.I. 8.10 = 26.770

Athlon x2 4200+ @ 2750MHz (current clock i'm using) no "cool'n'quiet"

---

### Post by ProNux on 2009-02-17
You may try to install emifreq-applet to check/scale down CPU usage.  My max speed is 1.86 GHz, I can use power saving mode, automatic mode, fixed speed, and performance (maximum) mode.  Good luck.

---

