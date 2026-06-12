---
title: "Lowering CPU temps"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by catatonic on 2009-05-27
I don't know what the norm is for a laptop, it seemed high when I checked the other threads. Is there anyway to lower my CPU temps on my laptop? It runs a lot since it is my only computer for now. My specs are in my sig.
Runs from 55-57 degrees Celsius with no load.

---

### Post by rlj399 on 2009-05-27
i was wondering the same thing, also how can i check if my laptops fan is working?

---

### Post by Weidbrewer on 2009-05-27
Not only working, but *clear*. Those vents suck up crud like you wouldn't believe. If you have any pets in the house, this is even more important.  

Also, for something called "a laptop" the one place they are very poorly suited to working on is, in fact, your lap.  Air circulation under them is terrible, which will also raise the temps.

I hope this helps.

---

### Post by 3rdalbum on 2009-05-27
rlj399: Is your laptop working? If so, then your laptop fan is working. If the fan wasn't working then your computer would freeze after a couple of seconds.

catatonic: As far as I know, 55 degress at idle is normal for a laptop. Laptops run warmer than desktops due to the lack of space for heat to disperse.

---

### Post by catatonic on 2009-05-27
> **3rdalbum said:**
> catatonic: As far as I know, 55 degress at idle is normal for a laptop. Laptops run warmer than desktops due to the lack of space for heat to disperse.

Thanks for clearing that up, I've been monitoring the temperature since thread about overheating poped up.

---

### Post by rlj399 on 2009-05-27
> **3rdalbum said:**
> rlj399: Is your laptop working? If so, then your laptop fan is working. If the fan wasn't working then your computer would freeze after a couple of seconds.

catatonic: As far as I know, 55 degress at idle is normal for a laptop. Laptops run warmer than desktops due to the lack of space for heat to disperse.


well that's the thing, i use my laptop for long periods of time and today its frozen twice :-\ id say maybe its like once per 4 hrs

---

### Post by PhoHammer on 2009-05-28
I've been somewhat dissatisfied with my laptop's heat production with GNU/Linux
compared to windows. My CPU and HDD seem to run hotter than in windows and I have 
searched high and low for a linux distro that keeps them cooler (*ubuntu, debian, gOS, 
PCLOS, and openSUSE). openSUSE was the only one I noticed a real difference in, but it 
was the wrong direction: it was so hot my fan was on full speed 24/7.:(

I refuse to use DSL or another lightweighter as my main distro because I love the 
features of the "full" distros (i.e. ubuntu). I just sit my laptop on a table mostly and
let the cpu fan side hang off the side of the table a bit and that helps ( I hover around
40C with that when it would be ~46C on my lap). 

I feel like this is an area Linux developers could work on, but by no means will
it keep me from using GNU/Linux OS's!

---

### Post by Steelmourne on 2009-05-28
Funnily enough my laptop fan can be heard going off if the processor spikes about 50%, but the trackpad retains heat for long periods of use.

---

### Post by freeman2000 on 2009-05-28
I have an HP laptop with AMD64 x2.  It runs in the 39-42 C range.  It seems that as long as you stay under the 65-70 C range (for an extended period) that you should be ok.  Attached is a link where you can look up your processor to tell what range is ok.  also, if you raise the backend of the laptop about a 1/2 inch, you will get better airflow. Good luck.   

  [http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)

---

### Post by dot2kode on 2009-05-28
I have Ubuntu Jaunty and Vista istalled on my Acer 6930 Aspire and the CPU temp and HDD temp are cooler in ubuntu.  OF course the RAM used is about 60% less in ubuntu also, and I have Compiz running with a lot of the perty' effects ;).  Little break down with mine temp wise you can compare with your's or whatever:

```

shhh@laptop:~# hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: 47°C 
```

```
product: 	WDC WD3200BEVT-2
vendor: 	Western Digital
physical id: 	
0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	11.0
serial: 	WD-WXE708PC7737
size: 	298GiB (320GB)
```
```

shhh@laptop:~# sudo sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +85.0°C, crit = +85.0°C) 
model name	: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz

```
One more thing, if someone has not already said this, but if your laptop allows you to scale the power of the CPU then try adding the CPU Frequency scaling applet to your panel and try putting it on the 'On Demand' setting.

---

### Post by catatonic on 2009-05-28
BIG time problem now, It was overheating under load. I was running updates, and during the kernal install it powered down. Now I cannot login to Ubuntu period. It brings up the login screen, can't use the mouse and freezes after I login. If I have to do a fresh install it would be the 2nd time in 2 weeks...
Something needs to be done with cooling.

---

### Post by theozzlives on 2009-05-28
It has been said that laptops on a males lap can lead to impotence. Just a thought.

---

### Post by gn2 on 2009-05-28
Remember that temperature reporting in Windows is notoriously inaccurate, the only CPU temp monitoring tool that's any use is [CoreTemp]("http://www.alcpu.com/CoreTemp/").

---

### Post by jeraldybelleta on 2009-05-28
[LEFT]AMD state the max operating temp for their XP CPUs is 85C. Some earlier CPUS were 90C, but only a few. Stick with 85C.

85C is the Internal Fry Temp. If the temperature inside the CPU goes above 85C you CPU is increasingly likely to die. Permanently.


Most motherboard CPU temp sensors report the Surface temp. The Surface Temp is typically around 10C lower than the Internal CPU Temp under Full Load conditions. So:

Internal Fry Temp = 85C
Surface Fry Temp = 75C


The Error Free Temp is not the same as the Fry Temp. It will vary from CPU to CPU, but typically it's 20C below the Fry Temp, i.e.

Interenal Error Free Temp = 65C
Surface Error Free Temp = 55C


If you overclock your machine the Error Free Temp falls - i.e. your CPU has to run cooler in order to remain stable. 

I hope this would help..:p[/LEFT]

---

### Post by dot2kode on 2009-05-28
> **jeraldybelleta said:**
> [LEFT]AMD state the max operating temp for their XP CPUs is 85C. Some earlier CPUS were 90C, but only a few. Stick with 85C.

85C is the Internal Fry Temp. If the temperature inside the CPU goes above 85C you CPU is increasingly likely to die. Permanently.


Most motherboard CPU temp sensors report the Surface temp. The Surface Temp is typically around 10C lower than the Internal CPU Temp under Full Load conditions. So:

Internal Fry Temp = 85C
Surface Fry Temp = 75C


The Error Free Temp is not the same as the Fry Temp. It will vary from CPU to CPU, but typically it's 20C below the Fry Temp, i.e.

Interenal Error Free Temp = 65C
Surface Error Free Temp = 55C


If you overclock your machine the Error Free Temp falls - i.e. your CPU has to run cooler in order to remain stable. 

I hope this would help..:p[/LEFT]

I was curious about the surface and internal temp. Nice lil' piece of info, thanks ;)

---

### Post by catatonic on 2009-05-28
Well my reported temps were about 20 degrees lower in ubuntu compared to vista, but at the moment my ubuntu portion is corrupted...

---

### Post by freeman2000 on 2009-05-28
> **catatonic said:**
> BIG time problem now, It was overheating under load. I was running updates, and during the kernal install it powered down. Now I cannot login to Ubuntu period. It brings up the login screen, can't use the mouse and freezes after I login. If I have to do a fresh install it would be the 2nd time in 2 weeks...
Something needs to be done with cooling.


Have you tried to login to recovery mode?  Or try logging in to the previously listed kernel on the Grub screen?  For instance, at the top of my Grub screen I have the latest kernel update + recovery mode.  Below that I have the 2 prior kernels plus their recovery modes.  At the bottom is Windows (haha).  I can work my way down the list (6 options) to get into Ubuntu.  I hope this helps.  Good luck.

---

### Post by catatonic on 2009-05-29
> **freeman2000 said:**
> Have you tried to login to recovery mode?  Or try logging in to the previously listed kernel on the Grub screen?  For instance, at the top of my Grub screen I have the latest kernel update + recovery mode.  Below that I have the 2 prior kernels plus their recovery modes.  At the bottom is Windows (haha).  I can work my way down the list (6 options) to get into Ubuntu.  I hope this helps.  Good luck.

Nope, nothing made it boot right...
I did away with Ubuntu for a short while, I just did a fresh install of openSUSE, I see myself going back already. Oh well it gives me a chance to see some other distros.

---

