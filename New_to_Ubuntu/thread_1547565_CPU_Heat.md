---
title: "CPU Heat?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by ohlawd on 2010-08-06
Are my temps supposed to be so high on Ubuntu? I'm running 10.04, temps never drop below 50c, usually 55-60 (each core). On Win 7 I idled around 35-40c, 60-62c full load.
What gives? :sad:

---

### Post by oldsoundguy on 2010-08-06
> **ohlawd said:**
> Are my temps supposed to be so high on Ubuntu? I'm running 10.04, temps never drop below 50c, usually 55-60 (each core). On Win 7 I idled around 35-40c, 60-62c full load.
What gives? :sad:

What is the ambient temp in your room and are you talking laptop or desktop?

I have had to add extra cooling to my desktops as the room tends to get warm and I run the processors at 100% 24/7/365 doing background crunching for BOINC.

Temps run between 40-48c

Without the after market coolers .. 52-60c .. one machine has Windows one machine has Ubuntu.

---

### Post by ohlawd on 2010-08-06
Desktop:
Intel E6400 OC'd to 2.8ghz
Stock HSF
Antec 902 case

Does ubuntu just run hotter then windows?

Edit: Ambient is around 73F

---

### Post by Elmer Fudd on 2010-08-06
Would you bring up system monitor and see what your "idle" CPU loads are?
Sometimes the high temps are due to a process that shouldn't be running.

---

### Post by oldsoundguy on 2010-08-06
> **ohlawd said:**
> Desktop:
Intel E6400 OC'd to 2.8ghz
Stock HSF
Antec 902 case

Does ubuntu just run hotter then windows?

Edit: Ambient is around 73F

Never noticed but a few degrees and it really depended on what I was doing on the boxes.

IF you are concerned, adding an after market cooler for that chip.  Check eBay, that is where I got my pipe coolers and they work great. Or some of the on line sellers.

---

### Post by ohlawd on 2010-08-07
Only thing that really seems active in the system monitor is Xorg, it spikes a lot, is this normal?

---

### Post by Jazzy_Jeff on 2010-08-07
When was the last time you cleaned the inside of your computer? I know mine starts getting a bit hotter after a couple of months without cleaning. That is how I judge when to clean it.

---

### Post by ohlawd on 2010-08-07
Well, I clean it every month or so, and my case has dust filters. 55c+ just seems off, especially when windows sits at 40. :(

---

### Post by clhsharky on 2010-08-07
ohlawd


> Does ubuntu just run hotter then windows?
No never noticed much difference on desktop cpu.

Maybe frequency scaling issue, have read some threads on this forum on Intel multi core and scaling. 1 core running 100% all the time, I don,t know if it pertains to your set up.

Sharky

---

### Post by ohlawd on 2010-08-07
Both cores seem to be used pretty equally, but are always 10%+, haven't seen 100% usage yet.

---

### Post by Elmer Fudd on 2010-08-07
> **ohlawd said:**
> Only thing that really seems active in the system monitor is Xorg, it spikes a lot, is this normal?

There are problems that will cause Xorg to take a lot of cycles.
What is your idle CPU load - System monitor, Resources tab.

---

### Post by ohlawd on 2010-08-07
Well, here's a screenshot if that will help any...

---

### Post by Jazzy_Jeff on 2010-08-07
Since you are running your processor overclocked you may want to get a different fan/heat sink for it. 

I am not sure why it is running hotter under Ubuntu. My temperatures are the same under XP or Linux. Not that I use XP any more...hehe.

---

### Post by clhsharky on 2010-08-07
ohlawd

OK, It was just a thought.

My ambient temp is 81F, CPU 38C, GPU 57C, usage 2-7% using chromium , duel core 2.5Hz stock clock n cooler. It seams like something not right with your temp.

Happy hunting

Sharky

---

### Post by ohlawd on 2010-08-07
Even with everything closed, it seems to stick to 20-30% usage. I've reinstalled ubuntu more then once, and temps always seem to be this high.

---

### Post by Elmer Fudd on 2010-08-07
> **ohlawd said:**
> Well, here's a screenshot if that will help any...

Looks like a normal (same as mine) idle CPU load to me. I just checked my Win7 OS load and it was a little less. So the answer to your question may be yes 10.04 runs a little hotter than win7.

Check you win7 CPU loads in the Task manager.

---

### Post by clhsharky on 2010-08-07
ohlawd

Do you have unneeded services off in back ground, maybe its normal.
[ATTACH]165714[/ATTACH]

Sharky

---

### Post by ohlawd on 2010-08-07
Hm, that's odd, performance seems ok, temps just bother me. I'll try underclocking/cleaning here soon... idk what else to do

---

### Post by clhsharky on 2010-08-07
ohlawd

Whats your Heat sink past? or is it maybe getting old, some don't hold up over time.

Sharky

---

### Post by ohlawd on 2010-08-07
Yeah, it still idles at around 35-40c in windows, still sitting 50c+ in ubuntu, I'm out of ideas

---

### Post by QLee on 2010-08-07
Here's one possible more idea.

Have you verified the actual temp independently of either operating system?

---

### Post by ohlawd on 2010-08-07
In bios it sit's around 40c, same within windows.

---

### Post by QIII on 2010-08-07
If I have some time to research today, I'll see what I can come up with.

I think that the suggestion to clean up the machine is just good, normal maintenance, but it does not explain why your temperature readings would be different between OSes.  A maintenance issue for one would be the same for the other.

I am currently on my quad core (until the wife authorizes the purchase of the six core!) AMD machine.  AMDs are generally thought to run hotter than Intel (I haven't done any testing myself).

The ambient room temperature is 22C, and the machine is running at 25-27C at the core.  (But I always buy huge after-market coolers). To be honest, I think the "max temperature" ratings OEMs publish for their hardware are a bit optimistic.  I like to think of them as the point at which they spontaneously erupt into flames rather than a temperature at which I would like to run them.  I get worried between 35C and 40C and shut down above that.  Even during a period when our air conditioning broke down a few weeks ago in 100F weather (37C - 38C), my machine was running just barely over my usual limit at 41C.

With an OEM cooling system, I would not expect *either *OS to run as hot as you are with Ubuntu.  In the 40s at idle, maybe, depending on the number of cores and the wattage.

I also scale the frequency of the CPU to On Demand.  I may have missed it, but do your motherboard and BIOS allow for frequency scaling for your CPU?  If it does, I would highly recommend using frequency scaling in Linux.

---

### Post by ohlawd on 2010-08-07
Yes, my motherboard supports scaling, and I have it turned off, maybe that's the issue? I'm about to clean my pc, and turn on scaling to see if it makes any difference.

EDIT: Throttling/speedstep don't seem to have any effect at all, if anything its runs hotter. I was at 72c for a awhile, now it seems to idle at 62c.

EDIT #2: ```
ohlawd@ohlawd-desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +60.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +58.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +57.0°C  (high = +78.0°C, crit = +100.0°C)
```
```
ohlawd@ohlawd-desktop:~$  acpi -t
Thermal 0: ok, 40.0 degrees C
```

---

### Post by ohlawd on 2010-08-07
Completely reset bios, and it seems a little cooler, but not much considering. It sits about 50c now, instead of 55 :-/

---

### Post by KdotJ on 2010-08-07
My CPU is around 62C just at idle...

---

### Post by ohlawd on 2010-08-07
That can't be good, can it?

---

### Post by bildr on 2010-08-07
If the only thing reaching for CPU is xorg and your processor is running hotter it is probably because linux offloads less graphics processing to the GPU and keeps more in the processor, particularly when using open source/reversed drivers.  I had this happen on my laptop using open drivers.  It disappeared when I went to binary nvidia drivers.  I am not a fan of binary drivers, just trying to give some explanation.  You could use some of the laptop tools(even on a desktop) to tweak some of the power management settings.  I just accept it and move on...

---

### Post by TBABill on 2010-08-07
Things that make it run hot and you can correct:

1. Install Sun Java - remove open source Java
2. Install Adobe Flash and remove gnash
3. Install an available video card proprietary driver, if available. 
4. Enable CPU scaling by installing CPUFREQ utilities, then in a terminal type> sudo cpufreq-set --governor ondemand You may have to restart after enabling scaling. You will see NO indication it is active in a terminal until you verify it by typing > cpufreq-info
You should then see somewhere in the text (almost a page of it) the word "ondemand" instead of "performance", which is the normal default.

If you run cool in Windows, no need to clean the machine other than just good maintenance practice. If cooling ducts, fans, vent holes were a problem you'd be hot in any OS.

**Note: Flash is not capable of hardware acceleration in Linux like it is in Windows so you will naturally run hotter using any flash application. Until Adobe improves Linux support, it just is what it is.

Hope that helps!

---

### Post by ohlawd on 2010-08-07
Haha, cpufreq reduced it by 3c, better then nothing I suppose.
To revert it'd be sudo cpufreq-set --governor performance?

---

### Post by TBABill on 2010-08-07
Yep....that'd be how to revert. If you're actively using the machine you may be demanding at higher levels, but if you let it sit for some time hopefully it will do better at reducing temps. If not, I guess 3C is all we can get if other actions have been taken. Proprietary drivers was the biggest change for me, along with flash and java. CPU scaling did a little, but not like the other changes.

---

### Post by ohlawd on 2010-08-07
Excuse me for sounding dumb, but what are 'proprietary drivers'?
I have 256.44 (Nvidia 9600 GT) installed from xorg-edgers.

---

### Post by nmaster on 2010-08-07
> **TBABill said:**
>  Proprietary drivers 

this is exactly what i was thinking.  i just started reading this thread from the beginning, but the issue of Xorg spiking seems to point to something with the GPU.  

Go to the "System" menu and find the option for "Hardware Drivers".  this should tell you if you have a proprietary driver installed.

if that doesn't give you the option of installing the proprietary driver, check out this: [http://www.nvidia.com/object/product_geforce_9600gt_us.html](http://www.nvidia.com/object/product_geforce_9600gt_us.html)

---

### Post by cloyd on 2010-08-07
To answer you question, propiertary driver are drivers that come from the hardware of commercial software people. They are not open source. They may give them to you, but there is a license agreement that usually prohibit reverse engineering or modifying them.

But, what I really wanted to tell you, my netbook  has run as hot as your. I've tweaked and worked, and found that changing kernels gave me more relief than anything.  I used a 2.6.34 kernel and it ran cooler than some others.  Yesterday, I got a new kernel (2.6.32-24) that is running cooler, sometime running in the 40's, and never going to the 60's **except** when watching flash videos on line. If I download the videos, and watch them later on VCL, I stay in the 50's.  That is a definite improvement on any other kernel I've seen in 10.4.

But I have a AMD processor, and they have almost always ran in the 50's if I am doing anything at all. I'm on a net book, and I don't think I can do much better without a cool pad with a fan.

I do remember that someone  on the forums said that the heating was due to excessive wakeups. I don't really understand that, other than saying that it has something to do with the kernel. Someone else may clarify that for you; I need more education before I can explain it.

However, I really don't think that the low 60's will harm you processor. Look for the critical temp on the manufacturers website. Mine says 100 C. I think 62 as a high should be ok. I've never seen 70, though I think I could with online flash videos. Really, I'd probably be wanting to shut the thing down in the high 60's, though no one who should know has told me that.

---

### Post by ohlawd on 2010-08-07
Apparently I do have proprietary drivers.
Also, I'm on kernel 2.6.35-020635, but had the same temps on .32.
Good news is, since using cpufreq, I haven't hit 60s... yet. Idles around 46-49 now.

---

### Post by TBABill on 2010-08-09
That's great news that you are running so cool now. When I first tried 10.04 my machine hit 82C before I called it quits. Mine peaks at 100C before cutout, but getting anywhere near that makes me too hot to handle holding it in my lap (vents kept clear) and makes me way too nervous to let it go like that. I now run 48-55 normal and mid 60s with lots of flash.

---

